# zsh 配置解析

## 前言

zsh 配置在你主目录的.zshrc中，其内容配置决定了你的shell样式，shell中的插件工具和用户层级的环境变量。本文将对该配置逐一分段做出解释以便使用者更好的理解其中的工作原理。

## zsh 

```shell
# --------------------- zsh ---------------
export ZSH=$HOME/.oh-my-zsh

ZSH_THEME="robbyrussell"

plugins=(git zsh-syntax-highlighting zsh-autosuggestions)

HISTFILE="${ZSH}/cache/.zsh_history"
ZSH_COMPDUMP="${ZSH}/cache/.zcompdump-${SHORT_HOST}-${ZSH_VERSION}"
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=blue'
source $ZSH/oh-my-zsh.sh
```

+ zsh_theme 指定了当前shell的主题，你可以在[oh-my-zsh-themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)挑选中意的主题。
+ plugins 指定来自oh-my-zsh的插件，当前插件的主要作用是高亮和提示。
+ HISTFILE 指定shell history的存放位置。
+ ZSH_COMPDUMP 指定zsh缓存补全文件的位置。
+ ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE 指定自动补全的高亮样式。

## general

```shell
# --------------------- general --------------------
export TERM="xterm-256color"
user_name=$(whoami)
echo "\e[35m nice to meet you, ${user_name} 🚀\e[0m"
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
export LS_COLORS=${LS_COLORS}:'di=01;35'
```

这些是shell的提示信息和基础配置，不需要改动。

## alias

```shell
#  --------------------- alias --------------------
alias "pc"="proxychains4"
alias "nv"="nvim"
alias "tm"="tmux"
alias "lg"="lazygit"
alias "ll"="ls -l"
alias "la"="ls -al"
```

为命令起一些别名，比如打出`ll` 代表你需要执行 `ls -a`。

## proxy

```shell
# --------------------- proxy --------------------
function proxy_on() {
    local proxy_ip_address="127.0.0.1"
    local port="7890"

    if [[ -n "$1" ]]; then
        proxy_ip_address="$1"
    fi

    if [[ -n "$2" ]]; then
        port="$2"
    fi

    export http_proxy="http://${proxy_ip_address}:${port}"
    export https_proxy="http://${proxy_ip_address}:${port}"
    export all_proxy="socks5://${proxy_ip_address}:${port}"
    echo -e "proxy on, ip is ${proxy_ip_address}, port is ${port}"
    curl cip.cc
}

function proxy_off() {
    unset http_proxy
    unset https_proxy
    unset all_proxy
    echo -e "proxy turn off"
    curl cip.cc
}
```

服务器利用clash构建了统一的代理出口，你可以执行两个命令来启动和关闭代理。当前的clash部署在10.176.22.35,你需要手动指定代理服务器地址。

**`proxy_on server_ip`**

```shell
➜  ~ proxy_on 10.176.22.35
proxy on, ip is 10.176.22.35, port is 7890
IP	: 103.238.130.134
地址	: 日本  东京都  东京
运营商	: interscale.com

数据二	: 亚太地区

数据三	: 日本东京都东京

URL	: http://www.cip.cc/103.238.130.134
```

**`proxy_off`**

``` shell
➜  ~ proxy_off
proxy turn off
IP	: 202.120.234.234
地址	: 中国  上海
运营商	: 复旦大学

数据二	: 上海市 | 复旦大学教育网

数据三	: 中国上海上海市 | 教育网

URL	: http://www.cip.cc/202.120.234.234
```

**注意**

+ 在不需要使用代理的场合，请及时关闭。
+ 请不要使用代理做任何与学习工作无关的事情。


## prompt

prompt部分是首次登录的一些提示信息。

## other

脚本中还包含审计工具的相关内容。


## 写在最后

该配置由[Albert Wang](https://github.com/Albert26193)的[lab-server-ops](https://github.com/Albert26193/lab-server-ops)工具生成。