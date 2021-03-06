# Getting #

```
git clone https://github.com/egrath/idle37-flatpak.git
```

# Building and Installing #

```
# build 
flatpak-builder --force-clean --install-deps-from=flathub build org.python.idle37.json
# export
flatpak-builder --repo="repo" --force-clean build org.python.idle37.json
# add repo
flatpak remote-add --user --no-gpg-verify idle37 repo
# install from repo
flatpak install --user --no-gpg-verify idle37 org.python.idle37
```

# Build the .flatpak file #
```
flatpak build-bundle repo idle37.flatpak org.python.idle37 3.7.3
```

# Desktop integration #

TCL/TK based applications don't integrate very well with the rest of the desktop. To have at least a similar look for the fonts, i highly recommend to add the following line to your ~/.Xresources file and match up with your desktop font. Example for EOS:

```
Idle*font: -*-lato-regular-r-normal-*-15-*-*-*-*-*-*-*
```

On some distributions, this file is automatically merged during login, on some others (like EOS), you have to create a appropriate desktop autostart file:

~/.config/autostart/xrdb.desktop:
```
[Desktop Entry]
Name=Merge X resource database entries
Type=Application
Exec=xrdb -merge /sysroot/home/egon/.Xresources
```
and make it executable:
```
gio set ~/.config/autostart/xrdb.desktop metadata::trusted yes
chmod 755 ~/.config/autostart/xrdb.desktop
```

# Use Python 3.7 outside of IDLE #
```
flatpak run --command=sh org.python.idle37
```

