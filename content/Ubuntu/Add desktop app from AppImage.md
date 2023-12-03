```
[Desktop Entry]
Name=YourApp
**Exec=/path/to/app.AppImage
Icon=/path/to/nextcloud-icon.png**
comment=app
Type=Application
Terminal=false
Encoding=UTF-8
Categories=Utility;
```

Then add the launcher to your applications menu by copying it to the /usr/share/applications directory with a command like:
```
sudo cp /home/yourusername/YourApp.desktop /usr/share/applications/
```

https://www.itprotoday.com/development-techniques-and-management/why-and-how-use-appimage-ubuntu#close-modal