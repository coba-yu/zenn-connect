---
title: "MacBook Setup手順"
emoji: "💻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["mac", "github"]
published: true
---

個人用の備忘録です.

## Homebrew

https://brew.sh/

```shell
cat <<EOF > ~/.zprofile
# homebrew
eval "$(/opt/homebrew/bin/brew shellenv)"

EOF
```

## GitHub

### .gitconfig

```
cat <<EOF > ~/.gitconfig 
[user]
    name = coba-yu
    email = yukob.formal@gmail.com

[alias]
    b = branch
    c = commit
    ch = checkout
    cm = commit -m
    l = log --oneline
    s = status -s --untracked-files=no
    u = add -u

EOF
```

### GitHub CLI

```shell
brew install gh
```

### Git Completion

https://github.com/git/git/tree/master/contrib/completion

```shell
mkdir -p ~/.zsh
curl -s https://raw.githubusercontent.com/git/git/refs/heads/master/contrib/completion/git-completion.zsh \
  -o ~/.zsh/_git
```

## Google Cloud Platform

### gcloud

https://cloud.google.com/sdk/docs/install?hl=ja

`google-cloud-cli-darwin-arm.tar.gz` をダウンロードして解凍する.

```shell
curl -Os https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-darwin-arm.tar.gz
tar -xzvf google-cloud-cli-darwin-arm.tar.gz
./google-cloud-sdk/install.sh --command-completion=true --install-python=false
./google-cloud-sdk/bin/gcloud init
```

beta componentをinstallする.

```shell
gcloud components update
gcloud components install beta
```

## Terraform

https://developer.hashicorp.com/terraform/install

## zsh

### .zshenv

環境変数を記述する.

### .zprofile

Homebrewの設定時に作成済みであるはず.

### .zshrc

```shell
cat <<EOF > ~/.zshrc
source $HOME/.local/bin/env
fpath=(~/.zsh $fpath)

# terminal
eval "$(starship init zsh)"

# k8s
alias k=kubectl

# execute `nodebrew use stable`
export PATH=$HOME/.nodebrew/current/bin:$PATH

# pyenv
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# The next line updates PATH for the Google Cloud SDK.
if [ -f '/Users/yukob/google-cloud-sdk/path.zsh.inc' ]; then . '/Users/yukob/google-cloud-sdk/path.zsh.inc'; fi

# The next line enables shell command completion for gcloud.
if [ -f '/Users/yukob/google-cloud-sdk/completion.zsh.inc' ]; then . '/Users/yukob/google-cloud-sdk/completion.zsh.inc'; fi

EOF
```
