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

## Karabiner

https://karabiner-elements.pqrs.org/

windowsのキー配置になっているキーボードをmacのJISキーボードlikeに使うための設定.

```shell
cat <<EOF > ~/.config/karabiner/karabiner.json
{
    "global": {
        "check_for_updates_on_startup": true,
        "show_in_menu_bar": true,
        "show_profile_name_in_menu_bar": false
    },
    "profiles": [
        {
            "complex_modifications": {
                "parameters": {
                    "basic.simultaneous_threshold_milliseconds": 50,
                    "basic.to_delayed_action_delay_milliseconds": 500,
                    "basic.to_if_alone_timeout_milliseconds": 1000,
                    "basic.to_if_held_down_threshold_milliseconds": 500,
                    "mouse_motion_to_scroll.speed": 100
                },
                "rules": []
            },
            "devices": [
                {
                    "disable_built_in_keyboard_if_exists": false,
                    "fn_function_keys": [],
                    "identifiers": {
                        "is_keyboard": true,
                        "is_pointing_device": false,
                        "product_id": 49977,
                        "vendor_id": 1133
                    },
                    "ignore": false,
                    "manipulate_caps_lock_led": true,
                    "simple_modifications": [
                        {
                            "from": {
                                "key_code": "japanese_pc_nfer"
                            },
                            "to": [
                                {
                                    "key_code": "japanese_eisuu"
                                }
                            ]
                        },
                        {
                            "from": {
                                "key_code": "japanese_pc_xfer"
                            },
                            "to": [
                                {
                                    "key_code": "japanese_kana"
                                }
                            ]
                        },
                        {
                            "from": {
                                "key_code": "caps_lock"
                            },
                            "to": [
                                {
                                    "key_code": "left_control"
                                }
                            ]
                        },
                        {
                            "from": {
                                "key_code": "left_command"
                            },
                            "to": [
                                {
                                    "key_code": "right_option"
                                }
                            ]
                        },
                        {
                            "from": {
                                "key_code": "left_option"
                            },
                            "to": [
                                {
                                    "key_code": "left_command"
                                }
                            ]
                        },
                        {
                            "from": {
                                "key_code": "japanese_pc_katakana"
                            },
                            "to": [
                                {
                                    "key_code": "delete_or_backspace"
                                }
                            ]
                        }
                    ]
                }
            ],
            "fn_function_keys": [
                {
                    "from": {
                        "key_code": "f1"
                    },
                    "to": [
                        {
                            "consumer_key_code": "display_brightness_decrement"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f2"
                    },
                    "to": [
                        {
                            "consumer_key_code": "display_brightness_increment"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f3"
                    },
                    "to": [
                        {
                            "apple_vendor_keyboard_key_code": "mission_control"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f4"
                    },
                    "to": [
                        {
                            "apple_vendor_keyboard_key_code": "spotlight"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f5"
                    },
                    "to": [
                        {
                            "consumer_key_code": "dictation"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f6"
                    },
                    "to": [
                        {
                            "key_code": "f6"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f7"
                    },
                    "to": [
                        {
                            "consumer_key_code": "rewind"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f8"
                    },
                    "to": [
                        {
                            "consumer_key_code": "play_or_pause"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f9"
                    },
                    "to": [
                        {
                            "consumer_key_code": "fast_forward"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f10"
                    },
                    "to": [
                        {
                            "consumer_key_code": "mute"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f11"
                    },
                    "to": [
                        {
                            "consumer_key_code": "volume_decrement"
                        }
                    ]
                },
                {
                    "from": {
                        "key_code": "f12"
                    },
                    "to": [
                        {
                            "consumer_key_code": "volume_increment"
                        }
                    ]
                }
            ],
            "name": "Default profile",
            "parameters": {
                "delay_milliseconds_before_open_device": 1000
            },
            "selected": true,
            "simple_modifications": [],
            "virtual_hid_keyboard": {
                "country_code": 0,
                "indicate_sticky_modifier_keys_state": true,
                "mouse_key_xy_scale": 100
            }
        }
    ]
}
EOF
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
