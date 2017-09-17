# i3-lastpass
This project aims to be a read-only interface for LastPass exclusively for the Linux + i3 Window Manager environment.

It aims to be an improvement over my [previous cross-platform attempt](https://github.com/alexzorin/lpass-ui) in both safety and usability.

![screenshot](https://i.imgur.com/kzPdrfu.png)

## Features
- No binaries, no building: it is just a really short shell script that composes [lpass-cli](https://github.com/lastpass/lastpass-cli), [dmenu](https://wiki.archlinux.org/index.php/Dmenu) (which is already used as the i3 application launcher) and [xsel](https://linux.die.net/man/1/xsel) for clipboard management.
- UI: mimics the i3 application launcher, doesn't look out of place
- Security: uses the ['SECONDARY' clipboard](https://specifications.freedesktop.org/clipboards-spec/clipboards-latest.txt). Does not use your regular (Ctrl-C,Ctrl-V) clipboard and clears the password after the first use. 
- Probably doesn't work on Wayland ¯\\_(ツ)_/¯

## Usage

1. Install the `i3-lastpass` script from this repository to somewhere in your path (such as `/usr/local/bin/`).
2. Set your `~/.i3/config` up and reload it with key binds for both the 'copy' and 'paste' actions. I use $mod+, and $mod+. , respectively:
```
bindsym --release $mod+less exec "i3-lastpass"
bindsym --release $mod+greater exec --no-startup-id "xdotool type --delay 0 --clearmodifiers $(xsel --secondary -o -c)"
```
3. Enjoy!

## LICENCE
MIT