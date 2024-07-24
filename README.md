# Clems-DWM-Rice
## Install Base 
This is ClemTheAlien's DWM Rice.
First Git Clone the latest DWM, Dmenu and St repos into your Linux OS
```sh 
git clone https://git.suckless.org/dwm
git clone git://git.suckless.org/dmenu
git clone git://git.suckless.org/st
```

NOTE: ST will be removed later and replaced by Alacritty. Just for a base DWM install do this.

Make clean install all of these folders
```sh
mkdir -p .desktopenv    #All of the Desktop Enviroment will exist in this dotfile 
mv dwm dmenu st .desktopenv
cd dmenu & sudo make clean install
cd -
cd dwm & sudo make clean install
cd -
cd st & sudo make clean install
```


### Change Resolution and adding DWM to exec 
```sh
echo "xrandr --output "[OUTPUT]" --mode [RESOLUTION]" > .xinitrc
echo "exec dwm" > .xinitrc
```

## Ricing
### Patches
Save these patches to your Downloads
https://dwm.suckless.org/patches/alwayscenter/
https://dwm.suckless.org/patches/uselessgap/

```sh
mkdir .desktopenv/dwm/patches
mv Downloads/* .desktopenv/dwm/patches
```

Patch

```sh
cd .desktopenv/dwm
patches -i patches/[PATCH]
sudo make clean install
```

NOTE: Check if each patch works seperately 

#### Gitclone this repo
```sh
git clone
cp config.h ~/.desktopenv/dwm/config.h
```

### Wallpaper and Picom 
Install Feh and Picom
```sh
sudo pacman -S feh picom 
#Change the install method based upon your linux distro. Clem uses Arch currently.
```
Set Wallpaper 
```sh
feh --bg-fill [WAllPAPER DIR]/[WALLPAPER]
```

#### Git clone Picom conf
```sh
git clone
sudo cp picom.conf /etc/xdg/picom.conf
```

