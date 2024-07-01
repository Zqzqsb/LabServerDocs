# 实用工具解析

## 前言

这里会介绍shell环境中预支的一些实用工具以及它们的简单用法。

## tmux

使用Tmux可以通过一系列命令来创建、管理会话、窗口和面板。我们可以在不启动多个终端应用的情况下开启多个shell连接，可以提高终端的使用效率。一个简单tutorials将带你简单了解它的使用方法。

### 启动 / 关闭

+ `tmux`
+ `exit`

启动tmux之后，你会观察到

![tmux_new](https://alicloud-pic.oss-cn-shanghai.aliyuncs.com/NISL_docs/tmux/tmux_new.png)

\[0\]是tmux窗口索引，而 0:zsh 则意味着当前窗口的标号为0的shell会话为zsh。

### 新会话

+ `Ctrl+b c` (先按Ctrl+b,再按c)

![tmux_create](https://alicloud-pic.oss-cn-shanghai.aliyuncs.com/NISL_docs/tmux/tmux_create.png)

得到了一个新会话，并且自动转到了新会话。

### 切换

+ `Ctrl+b session_id` 在会话之间切换

### 分割

+ `Ctrl+b "` 水平分割

![tmux_sh](https://alicloud-pic.oss-cn-shanghai.aliyuncs.com/NISL_docs/tmux/split_horizontal.png)

+ `Ctrl+b %` 垂直分割 

![tmux_sv](https://alicloud-pic.oss-cn-shanghai.aliyuncs.com/NISL_docs/tmux/split_vertical.png)

### 移动

+ `Ctrl+b 方向键`

在组合分割的情况下，可以使用组合方向键 如 `Ctrl+b ↑+→` 向右上方移动。

![move_demo](https://alicloud-pic.oss-cn-shanghai.aliyuncs.com/NISL_docs/tmux/tmux_move_demo.mov)

### 结语

你已经了解了tmux的基本用法，你可以检索资料探索更多功能。

## vim / nvim

实用文本编辑器。

## curl / wget 

这两个命令都可以从网络上下载文件，更推荐使用curl。

### demo

下载文档仓库。

```shell
curl https://github.com/Zqzqsb/lab-server-docs.git
```

## tree

tree可以列出当前的目录结构。

```shell
➜  lab-server-docs git:(main) ✗ tree
.
├── README.md
└── UserDocs
    ├── Disk.md
    ├── Gpu Related.md
    ├── Others To Metion.md
    ├── Quick Start.md
    ├── Support Us.md
    ├── Useful Tools.md
    └── Zsh Profile.md

2 directories, 8 files
```

## fd-find

`fd-find` 是一个用 Rust 编写的简单、快速的文件搜索工具，它允许用户通过指定的模式搜索文件和目录。它的工作原理类似于常见的 find 命令，但相对更加快速和易用。
在不同的系统中使用该工具的不尽相同，你可以尝试以下这些来确定该工具在你的系统中作何称呼。

+ `fd`
+ `fd-find`
+ `fdfind`

**用法**

简单搜索

+ `fdfind <文件/目录名称>` :  搜索当前目录和子目录中包含指定名称的文件或目录。
+ `fdfind <文件/目录名称> <路径>` : 搜索指定路径下的文件和子目录。

匹配模式

+ `fdfind *.txt` : 通配符模式：使用 * 匹配任意字符，? 匹配单个字符。
+ `fdfind -e '^doc.*\.pdf$'` : 正则表达式：使用 -e 参数并指定正则表达式进行匹配。

过滤器

+ `fdfind -t f` : 只搜索普通文件
+ `fdfind -t d` : 只搜索目录

更多选项

+ `fdfind -d 2 <文件/目录名称>` : 控制递归层数
+ `fdfind --color always <文件/目录名称>` : 色彩输出
+ `fdfind -l <文件/目录名称>` : 显示详细信息

## fzf

是一个用于命令行的模糊搜索工具，它可以帮助用户快速选择文件、目录、命令等内容。它的主要功能是提供一个交互式界面，通过模糊匹配搜索的方式让用户快速定位所需内容。这是jj工具的依赖项目，一般来说，你不会直接用到它。

## bat

bat 是一个功能强大的替代 cat 命令的工具，它可以对文件进行语法高亮、行号显示、自动换行等操作。
除了 cat 的功能外，bat 还支持输出带有语法高亮的内容，使得文件内容在终端中更易于阅读。

## exa

exa 是一个现代化的 ls 替代工具，用于在终端中列出文件和目录的内容。与传统的 ls 相比，exa 提供了更美观的输出、更丰富的功能以及更容易理解的选项。
