# 常见问题

这里解答常见问题并给出人们最常遇到问题的修复方法。如果这里没有你的问题，请查阅文档的其余部分或项目的 [GitHub issues](https://github.com/vnotex/vnote/issues)。

## 如何指定自定义的 MathJax 脚本？ { #custom-mathjax }

VNote 使用 **MathJax 3** 渲染数学公式。要选择它加载哪个 MathJax 构建：

1. 把**默认**配置文件夹中的 `web/js/mathjax.js` 复制到**用户**配置文件夹下的相同路径（`web/js/mathjax.js`）。VNote 将使用你的副本而非默认版本。
2. 编辑复制的文件并设置脚本 URL。默认值为：

    ```js
    this.mathJaxScript = 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js';
    ```

若要使用**本地**副本以便离线使用，[下载 MathJax](https://docs.mathjax.org/en/latest/web/hosting.html) 并指向它：

```js
this.mathJaxScript = 'file://c:/Users/foo/mathjax/tex-svg.js';
```

背景信息参见[数学与图表](../editing/math-and-diagrams.md)和[设置](../customization/settings.md)。

## VNote 在版本更新后崩溃

当更新跨越多个版本、旧配置不再兼容时，常会发生这种情况。打开你的**用户**配置文件夹，删除 `vnotex.json`，然后重启 VNote。该文件夹的位置参见[设置](../customization/settings.md)。

## 界面卡死、编辑模式下光标不可见，或打开笔记时 VNote 崩溃

在 **Windows** 上，这三种症状通常由显卡驱动引起。依次尝试以下步骤，每一步后重启 VNote 检查是否有效：

1. 更新显卡驱动。
2. 设置 VNote 使用集成显卡运行。
3. 若无效，在**设置**对话框中逐一尝试各个 `OpenGL` 值。
4. 确保 VNote 的可执行文件夹位于 `C:` 盘。

## 我的笔记存放在哪里？

存放在你放置它们的地方。每个笔记本都是一个普通目录（其*笔记本根文件夹*），其中包含纯 Markdown 文件，图片则存放在附件文件夹中（默认为 `vx_assets`）。你的笔记绝不会被锁在数据库里——VNote 自身的索引和缓存与你的内容分开保存。参见[笔记本、文件夹与笔记](../managing-notes/notebooks-folders-notes.md)。

## 如何在多台设备间同步笔记？

VNote 为捆绑笔记本提供了内置的 Git 同步；而且由于笔记本本身就是一个文件夹，你也可以用任何你信任的工具来同步它，例如 Dropbox、OneDrive 或 Nextcloud。参见[笔记本同步](../managing-notes/notebook-sync.md)。

## 我能便携地使用 VNote（从 U 盘）吗？

可以。按[让 VNote 便携化](../customization/settings.md#make-vnote-portable)所述，把配置与可执行文件放在一起。

## 如何导入我已有的 Markdown 文件？

创建一个**捆绑笔记本**并把你的文件夹导入其中——参见[导入与迁移](../managing-notes/importing-migrating.md)。如果你更希望完全按原样接纳现有文件夹，可以用**新建笔记本 → 类型：原始笔记本**打开它，它会就地浏览该文件夹，但没有标签、附件和回收站。从其他应用迁移参见[数据迁移](data-migration.md)。

## 捆绑笔记本和原始笔记本有什么区别？

捆绑笔记本会在其根文件夹下维护一份索引，正是这份索引让标签、附件、回收站以及内置的 Git 同步成为可能。原始笔记本没有索引——它像文件浏览器一样就地浏览一个文件夹——因此这些功能都不可用。请优先选择捆绑笔记本；只有当现有文件夹必须按原样被接纳，或者由 VNote 之外的东西管理时，才选择原始笔记本。参见[笔记本、文件夹与笔记](../managing-notes/notebooks-folders-notes.md#which-type-should-i-use)。
