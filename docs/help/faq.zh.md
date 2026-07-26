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

存放在你放置它们的地方。每个笔记本都是一个普通目录（其*笔记本根文件夹*），其中包含纯 Markdown 文件和一个用于图片的 `vx_images` 文件夹。没有任何内容隐藏在数据库里。参见[笔记本、文件夹与笔记](../managing-notes/notebooks-folders-notes.md)。

## 如何在多台设备间同步笔记？

VNote 没有内置云；你可以用任何你信任的工具同步笔记本文件夹——Dropbox、OneDrive、Nextcloud 或 git。参见[笔记本同步](../managing-notes/notebook-sync.md)。

## 我能便携地使用 VNote（从 U 盘）吗？

可以。按[让 VNote 便携化](../customization/settings.md#make-vnote-portable)所述，把配置与可执行文件放在一起。

## 如何导入我已有的 Markdown 文件？

使用**从文件夹新建笔记本**围绕现有目录构建笔记本，或把文件和文件夹导入笔记本。参见[导入与迁移](../managing-notes/importing-migrating.md)。从其他应用迁移参见[数据迁移](data-migration.md)。
