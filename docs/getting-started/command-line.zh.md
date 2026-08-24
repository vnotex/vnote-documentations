# 命令行

你可以从终端、脚本或桌面的“打开方式”菜单启动 VNote。传入文件路径即可直接打开它们，另有若干选项可以改变 VNote 的启动方式。

```bash
vnote [选项] [路径...]
```

## 打开文件

任何位置参数都会被当作要打开的文件或文件夹。路径可以是相对路径或绝对路径，文件也不必属于某个笔记本——VNote 会将其作为独立的缓冲区打开。

如果 VNote 已在运行，再次调用不会启动新进程：路径会被转发给正在运行的实例，由它打开文件并激活窗口。

## 选项

| 选项 | 作用 |
|------|------|
| `-h`、`--help` | 打印选项列表并退出。 |
| `-v`、`--version` | 打印版本号并退出。 |
| `--verbose` | 打印更多日志。 |
| `--log-stderr` | 将日志输出到 stderr，而不仅仅写入日志文件。 |
| `--quiet` | 抑制非关键的控制台日志。 |
| `--watch-themes` | 监视主题文件夹的变化，在你编辑主题时自动重新加载。制作[主题](../customization/themes-and-styles.md)时很有用。 |
| `--detached-view` | 在分离的视图分屏中打开指定文件。 |

## 分离视图

使用 `--detached-view` 时，文件会在一个独立的顶层窗口中打开，而不是主窗口的标签页，并且主窗口不会被置前。这让 VNote 很适合用来查看需要与其他应用并排显示的文件：

```bash
vnote --detached-view notes/todo.md
```

分离窗口详见[编辑器基础](../editing/editor-basics.md)，在那里你也可以把已经打开的标签页分离出去。

!!! note "很少需要"
    VNote 还接受少量 QtWebEngine 参数——`--remote-debugging-port <port_number>`、`--no-sandbox` 和 `--disable-gpu`。它们不会出现在 `--help` 中，仅用于调试以及规避显卡驱动问题。
