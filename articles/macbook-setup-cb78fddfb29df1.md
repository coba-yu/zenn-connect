---
title: "MacBook Setup手順"
emoji: "💻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["mac", "github"]
published: true
---

個人用の備忘録です。

## Homebrew

https://brew.sh/

## Git Completion

https://github.com/git/git/tree/master/contrib/completion

```shell
mkdir -p ~/.zsh
curl -s https://raw.githubusercontent.com/git/git/refs/heads/master/contrib/completion/git-completion.zsh \
  -o ~/.zsh/_git
```
