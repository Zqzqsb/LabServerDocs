# Shell

## 1. 关于 `shell`

### 1.1 什么是 `shell`

- 以下内容通过 `AI` 生成，_其准确性经过人工验证_。

> Linux shell 是 Linux 操作系统中的一个命令行解释器，也称为命令行界面（Command Line Interface, CLI）。它是与操作系统内核进行交互的主要工具之一，允许用户通过输入命令来执行各种操作。

---

- 对于绝大多数的 `Linux` 操作系统而言，其默认 `shell` 为 `bash`。
- 但是对于本实验室大部分非 `root` 用户，管理员已经将其替换为 `zsh` 。该部分内容将在下文介绍。

### 1.2 如何查看当前 `shell`

- 请输入如下命令

```shell
echo $SHELL
```

- 其结果如下所示：

```shell
# albertwang @ AlbertMBP in ~ [21:24:22]
$ echo $SHELL
/bin/zsh
```

### 1.3 不建议切换 `shell`

- **强烈不建议**切换 `shell`。
- `zsh` 对 `bash` 具有很好的兼容性，因此，如果需要编辑 `{HOME}/.bashrc` 文件，你可以将其平滑迁移至 `{HOME}/.zshrc` 文件当中，**而不是试图修改 `shell`**。
- 如果不得不改变 `shell` ，请联系服务器管理员(mail: 572023697@qq.com)，管理员会协助完成你的需求。

## 2. 关于 `zsh`

### 2.1 为什么选择 `zsh`

- 首先，`zsh` 具备良好的兼容性。它和 `fish` 等较为激进的终端解释器不同，`zsh` 能够兼容 `bash` 编程当中的大多数语法。
- 其次，`zsh` 具备良好的扩展性。`zsh` 具备良好的插件扩展能力，能够支持 `oh-my-zsh` 等插件框架，极大提升了易用性。
- 同时，`zsh` 具备良好的稳定性。`MacOS/Arch Linux` 等操作系统，将 `zsh` 设置为默认 `shell` 。其流行性一定程度上佐证了其稳定性。

### 2.2 关于 `.zshrc`

- `${HOME}/.zshrc` 是 `zsh` 启动的入口文件。对于每个独立启动的 `zsh` 进程而言，它会预先加载 `.zshrc` 文件。
- `${HOME}/.zshrc` 文件规定了 `PATH` 环境变量等重要信息，**强烈不建议删除该文件**。
- 如果某文档说明需要修改 `.bashrc` 文件，那么，对于本服务器而言，可以将其写入 `.zshrc` 文件。如果确实存在兼容性问题，请联系管理员(mail: 572023697@qq.com)。
- 如果修改了 `.zshrc` 文件，请执行以下命令

```shell
source .zshrc
```

### 2.3 关于 `oh-my-zsh`

- 这是一个 `zsh` 的插件框架，能够实现丰富的功能。链接：[GitHub - ohmyzsh/ohmyzsh: 🙃 A delightful community-driven (with 2,100+ contributors) framework for managing your zsh configuration. Includes 300+ optional plugins (rails, git, macOS, hub, docker, homebrew, node, php, python, etc), 140+ themes to spice up your morning, and an auto-update tool so that makes it easy to keep up with the latest updates from the community.](https://github.com/ohmyzsh/ohmyzsh)

- 对于本服务器而言， `oh-my-zsh` 程序的存放位置为 `${HOME}/.oh-my-zsh` 目录。
- 对于本服务器而言，在 `${HOME}/.zshrc` 文件当中，插件配置定义如下：

```shell
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```

- `git` 插件提供了关于 `git` 的补全和缩写功能。
- `zsh-syntax-highlighting` 插件提供了语法高亮功能。
- `zsh-autosuggestions` 插件提供了丰富的补全功能。大部分情况下，按 `Tab` 键即可提示需要的内容。

---

- 如果在登陆时，系统频繁提示 `omz update` 相关内容，可以选择忽略，或者在进入终端后，手动执行如下命令

```shell
omz update
```

## 3. 建议

1. 尽可能多地使用 `tab` 键，该按键能够对命令和路径进行补全。同时，也一定程度上提升了操作的安全性。
2. 如果你熟悉 `vim` ，可以尝试安装名为 `zsh-vi-mode` 的 `oh-my-zsh` 插件。链接：[GitHub - jeffreytse/zsh-vi-mode: 💻 A better and friendly vi(vim) mode plugin for ZSH.](https://github.com/jeffreytse/zsh-vi-mode)
3. 对于大部分 `Linux` 命令，可以在该网站上速查。链接：[Linux 命令搜索引擎 命令，Linux Linux 命令搜索引擎 命令详解：最专业的 Linux 命令大全，内容包含 Linux 命令手册、详解、学习，值得收藏的 Linux 命令速查手册。 - Linux 命令搜索引擎](https://wangchujiang.com/linux-command/)
