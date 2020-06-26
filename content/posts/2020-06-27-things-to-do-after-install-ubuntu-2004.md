+++ 
draft = false
date = 2020-06-27T07:00:00+07:00
title = "Những việc cần làm sau khi cài đặt Ubuntu 20.04"
description = ""
slug = "" 
tags = ["Ubuntu", "Linux"]
categories = []
externalLink = ""
series = []
+++

**Đây là bài viết tổng hợp những điều cơ bản mình đã làm sau khi cài lại Ubuntu 20.04**

1. Cập nhật hệ thống

```shell
sudo apt update
sudo apt upgrade
```

2. Cài đặt một số phần mềm cần thiết

```shell
sudo apt install gdebi
```

Các phần mềm mình đã cài với `gdebi` là:
  - [Google Chrome](https://www.google.com/chrome/)
  - [Visual Studio Code](https://code.visualstudio.com/)
  - [Dropbox](https://www.dropbox.com/install)

Một số phần mềm hay ho khác:

  - Spotify:
  ```shell
  curl -sS https://download.spotify.com/debian/pubkey.gpg | sudo apt-key add -
  echo "deb http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list
  sudo apt-get update && sudo apt-get install spotify-client
  ```

3. Cài đặt `zsh`

```shell
sudo apt install zsh
chsh -s /usr/bin/zsh
```

Cài đặt công cụ quản lý zsh plugins: `zplug`

```shell
sudo apt install zplug
```

Chỉnh sửa file `.zshrc` của bạn lại cho phù hợp, ví dụ của mình như sau:

```shell
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

export GTK_IM_MODULE=ibus
export QT_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT4_IM_MODULE=ibus
export CLUTTER_IM_MODULE=ibus

export HISTFILE=~/.zsh_history
export HISTSIZE=10000
export SAVEHIST=10000
setopt append_history
setopt INC_APPEND_HISTORY
setopt hist_expire_dups_first
setopt hist_fcntl_lock
setopt hist_ignore_all_dups
setopt hist_lex_words
setopt hist_reduce_blanks
setopt hist_save_no_dups
setopt share_history
setopt HIST_IGNORE_SPACE

eval $(thefuck --alias)

source /usr/share/zplug/init.zsh

zplug "desyncr/auto-ls"
zplug "djui/alias-tips"
zplug "srijanshetty/node.plugin.zsh"
zplug "voronkovich/mysql.plugin.zsh"
zplug "zlsun/solarized-man"
zplug "zpm-zsh/ls"
zplug "zpm-zsh/ssh"
zplug "zsh-users/zsh-completions"
zplug "zsh-users/zsh-autosuggestions"
zplug "zsh-users/zsh-syntax-highlighting", defer:2
zplug "zsh-users/zsh-history-substring-search"

zplug "plugins/alias-finder", from:oh-my-zsh
zplug "plugins/colored-man-pages", from:oh-my-zsh
zplug "plugins/colorize", from:oh-my-zsh
zplug "plugins/command-not-found", from:oh-my-zsh
zplug "plugins/common-aliases", from:oh-my-zsh
zplug "plugins/extract", from:oh-my-zsh
zplug "plugins/git", from:oh-my-zsh
zplug "plugins/git-auto-fetch", from:oh-my-zsh
zplug "plugins/gitignore", from:oh-my-zsh
zplug "plugins/golang", from:oh-my-zsh
zplug "plugins/gpg-agent", from:oh-my-zsh
zplug "plugins/history", from:oh-my-zsh
zplug "plugins/node", from:oh-my-zsh
zplug "plugins/npm", from:oh-my-zsh
zplug "plugins/python", from:oh-my-zsh
zplug "plugins/sudo", from:oh-my-zsh
zplug "plugins/systemd", from:oh-my-zsh
zplug "plugins/thefuck", from:oh-my-zsh
zplug "plugins/ubuntu", from:oh-my-zsh
zplug "plugins/vscode", from:oh-my-zsh
zplug "plugins/wd", from:oh-my-zsh
zplug "plugins/z", from:oh-my-zsh

zplug 'romkatv/powerlevel10k', as:theme

if ! zplug check --verbose; then
    printf "Install? [y/N]: "
    if read -q; then
        echo; zplug install
    fi
fi

zplug load #--verbose

ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#120299,bg=cyan"

# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
```

4. Cài đặt `tlp`

```shell
sudo apt instlal tlp
sudo tlp start
```
