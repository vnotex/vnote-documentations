# HTTP 接口

VNote 4.14 引入了可选的 **HTTP API**，供本机自动化客户端与智能体使用。它运行在正常的主 VNote 应用中，并非无界面服务或 MCP 服务器。本指南适用于 VNote 4.14.4；完整协议参见[上游 API 指南](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md)及 [OpenAPI 契约](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.openapi.yaml)。

## 启用客户端 { #enable-a-client }

1. 保持需要授权的笔记本打开，然后进入**设置 → HTTP API**。
2. 在**客户端令牌（Client Tokens）**下点击**新建（New）**。在**签发客户端令牌（Issue Client Token）**中填写标签，选择笔记本、权限和有效期。新授权默认为**只读**、有效期 **90 天**；可选 1、7、30、60、90 或 180 天，或**永不过期（Never）**。之后打开或创建的笔记本不会自动加入授权。
3. 点击**签发令牌（Issue Token）**，在令牌显示时点击**复制（Copy）**。密钥**仅显示一次**，无法从 VNote 恢复。请将其存入客户端的密钥存储，不要放入笔记、URL、命令历史、源代码仓库或智能体的工具参数。关闭对话框不会清空剪贴板；安全保存令牌后，请自行清空剪贴板。
4. 启用 **`127.0.0.1:18765`** 上的监听器，或明确选择其他端口。也支持显式指定 IPv6 回环地址 `::1`。不支持通配/公共地址绑定，也不会自动回退到其他端口。
5. 每次请求都必须携带 **`Authorization: Bearer …`** 请求头，包括 `/api/v1/info`。客户端不再需要访问时，在设置中撤销令牌；没有远程令牌管理端点。

监听器关闭时也可以签发令牌。**永不过期**不会取消笔记本或权限限制，令牌仍可撤销。建议使用有限有效期，并只授予客户端实际需要的权限。

!!! warning "不要暴露内置 HTTP 端口"
    保持 VNote 监听器仅使用回环地址。不要将其 HTTP 端口公开或通过端口转发暴露给其他机器。远程使用需要管理员在**同一台主机**上部署 HTTPS 反向代理，并遵循上游的 [HTTPS 与 Host/Origin 规则](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md#https-for-other-machines)。VNote 不提供 TLS、浏览器界面或 CORS：带有 `Origin` 或 `Cookie` 请求头的请求会被拒绝。不要使用基于浏览器的 OpenAPI“试用”客户端。

## 权限与笔记边界 { #permissions-and-note-boundaries }

| 权限范围 | 允许的操作 |
| --- | --- |
| `notes:read` | 列出已授权且打开的笔记本及节点，读取元数据与已保存内容，搜索已保存的笔记。 |
| `notes:read-live` | 额外允许通过 `view=live` 读取活动编辑器的实时内容；同时需要 `notes:read`。 |
| `notes:write` | 创建空白 Markdown/文本笔记、替换或追加内容，以及重命名受支持的笔记。 |
| `notes:trash` | 将受支持的普通笔记移入可恢复的回收站；独立于写入权限。 |

授权指向特定笔记本，而非任意文件系统路径。**原始笔记本**和**捆绑笔记本**都支持授权读取及受支持的 Markdown/文本修改，但笔记本必须处于打开状态。请使用 API 返回的稳定笔记本/节点 ID，而非根据显示名称拼接路径。移除原始笔记本后重新添加，不会保留原来的身份标识。

- **受保护/加密笔记**不会出现在 API 列表与搜索中，包括名称与摘要，即使该笔记已在编辑器中解锁。API 无法将其解锁。
- **专用格式或二进制笔记**可能只提供元数据，而不允许读取内容。应检查能力标志，不要假定每种文件都能读取或修改。
- **已保存内容读取和搜索**使用已持久化的内容，而非编辑器中的未保存文本。实时读取需要额外权限，会返回 `dirty`，但不会保存编辑器。如果没有活动写入视图，响应会明确回退到 `view=saved`。
- **有未保存修改的编辑器**不会被 API 修改操作静默保存或覆盖。遇到 `unsaved_changes` 时，请先由笔记所有者处理，再考虑新的修改。
- **移入回收站必须可恢复**。原始笔记本报告 `capabilities.trash=false`；其他条件合法的 DELETE 可能先收到 `202`，随后以 `unsupported_trash`（`422`）、`committed=false` 和 `saved=false` 失败。不会回退到永久删除。

## 只读 PowerShell 示例 { #read-only-powershell-example }

启用监听器并签发只读令牌后，在 PowerShell 中运行以下代码。将令牌粘贴到隐藏输入的提示中，而不是写入命令本身。两次请求均为 **GET**：返回 API 信息并列出当前已打开的授权笔记本，不会修改笔记。

```powershell
$secret = Read-Host 'VNote client token' -AsSecureString
$headers = @{
    Authorization = 'Bearer ' + [System.Net.NetworkCredential]::new('', $secret).Password
}
try {
    Invoke-RestMethod -Method Get -Uri 'http://127.0.0.1:18765/api/v1/info' -Headers $headers
    Invoke-RestMethod -Method Get -Uri 'http://127.0.0.1:18765/api/v1/notebooks' -Headers $headers
}
finally {
    $secret.Dispose()
    Remove-Variable secret, headers
}
```

如果在设置中更改了端口，请相应调整。授权请求头必然会在进程内存中包含明文令牌；移除变量不保证内存被擦除。该示例不会持久化令牌，也不会将其写入命令历史。不要记录请求头；如果通过剪贴板粘贴令牌，使用后请清空剪贴板。

## 写入、冲突与操作结果 { #writes-conflicts-and-operation-results }

需要写入权限的客户端，应先阅读完整的[端点与冲突契约](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md#validators-and-conflict-recovery)，再实现修改操作。修改已有笔记时，必须在 `If-Match` 中使用带引号的强校验值，值来自响应正文：

| 操作 | 所需校验值 |
| --- | --- |
| 替换或追加内容 | 从**已保存**内容读取中取得的 `contentVersion`。 |
| 重命名 | 从元数据中取得的 `metadataVersion`。 |
| 移入回收站 | 从已保存内容中取得的 `noteStateVersion`。 |

HTTP `ETag` 描述的是某一响应页，并非修改整篇笔记所需的校验值。不要使用它、实时内容校验值或文件名来替代。新建操作只创建**空白**笔记；初始化内容是另一个有条件的操作，不是带内容的原子新建请求。

**`202 Accepted` 不代表成功。**使用同一令牌轮询返回的 `Location`，直到操作达到终止状态，再检查 `committed`、`saved` 和错误信息。失败的操作也可能已经更改内存中的内容或保存到磁盘；失败并不意味着回滚。版本冲突（`412`）需要重新读取并协调修改；未保存编辑冲突（`409`）需要由所有者处理编辑器。遇到超时、响应丢失、应用重启或操作记录过期时，不要盲目重试修改：原操作可能已经生效。

## 存储与撤销 { #storage-and-revocation }

只有监听器的 `enabled`、`address` 和 `port` 设置存储在本机 **`session.json`** 的 `httpApi` 下。**`vnotex.json` 中的 HTTP API 键会被忽略，不会迁移**。这两个文件都不保存 bearer 密钥，也不用于管理令牌。

仅所有者可访问的凭据注册表文件保存的是 **SHA-256 校验值**，而非可恢复的 bearer 密钥。Windows 上的位置为 `%LOCALAPPDATA%/VNote/http-api/tokens.json`；Windows 便携配置使用可执行文件旁的 `config/local/http-api/tokens.json`。其他平台使用应用数据配置目录，而非缓存。该文件独立于普通设置，也不构成密码学上的机器绑定：主动复制有效的注册表文件，仍可能让令牌在其他机器上可用。不要随笔记本共享它，也不要通过编辑该文件撤销客户端。

请通过**设置 → HTTP API**撤销令牌。撤销会立即在内存中生效；如果持久化失败，VNote 会停止监听器并报告错误。重新启用监听器之前，请先修复存储或权限保护问题——不要假定失败的撤销已被持久保存。关闭监听器不等于撤销令牌。

## 相关工作流 { #related-workflows }

- 使用[任务](tasks.md)运行受信任的本地程序；HTTP API 不提供 shell 命令或笔记本任务接口。
- 使用[笔记本同步](../managing-notes/notebook-sync.md)进行同步；API 不提供同步控制。
- 访问审计、限制、支持的端点与错误码参见[固定版本的上游指南](https://github.com/vnotex/vnote/blob/v4.14.4/docs/http-api.md)。
