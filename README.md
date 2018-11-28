# Quick tmux setup

## ~/.bashrc

```
case $- in
    *i*)
        if command -v tmux>/dev/null; then
            if [[ ! $TERM =~ screen ]] && [[ -z $TMUX ]]; then
                if tmux ls 2> /dev/null | grep -q -v attached; then
                    exec tmux attach -t $(tmux ls 2> /dev/null | grep -v attached | head -1 | cut -d : -f 1)
                else
                    exec tmux
                fi
            fi
        fi
        ;;
esac
```

## ~/.tmux.conf

```
unbind C-b
set-option -g prefix C-t
bind-key C-t send-prefix
```
