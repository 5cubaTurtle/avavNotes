[online book](https://debian-handbook.info/browse/stable/index.html)

## UI
### Desktop shortcut
 Create `.desktop` file at `~/.local/share/applications` or `/usr/share/applications/` depending whether you want the shortcut to be accessible only by the local account or by everyone.
Example `.desktop` file:
```
[Desktop Entry]  
Version=1.0  
Name=Name of the application  
Comment=text you want to show when hovering above the icon  
Exec=Path of the executable file %U  
Icon=Path of the image  
Terminal=false  
StartupWMClass=name of application  
Type=Application  
Categories=category of the application  
MimeType=Type of application it should open
```
For the full list of categories of desktop environments, check the official [specification](https://standards.freedesktop.org/menu-spec/latest/apa.html).