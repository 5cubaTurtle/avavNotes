#linux 
start/stop recording screen: ``Ctrl+Alt+Shift+R
setting recording time to 300 seconds:
```shell
gsettings set org.gnome.settings-daemon.plugins.media-keys max-screencast-length 300
```
- To have unlimited recording time, set this to 0. Stop recording by `Ctrl+Alt+Shift+R` again
- The video will be saved to `$Home/Video` as set in `$HOME/.config/user-dirs.dirs` file:
```shell
cat .config/user-dirs.dirs 
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```
