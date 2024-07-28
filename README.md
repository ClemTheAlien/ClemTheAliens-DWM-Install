# Clems-DWM-Install
Here are some videos I used to make my install 
In order to maintain your DWM install i recommend learning some basic C and also how to manually patch alongside how DWM works in general.
- https://www.youtube.com/watch?v=6MaTMuFVGck&t=2713s&pp=ygUDZHdt
- https://www.youtube.com/watch?v=unqsQJaECv0&pp=ygUDZHdt
- https://www.youtube.com/watch?v=DlViR5Ymg4A&t=558s&pp=ygUIZHdtIHJpY2U%3D

## Install Base 
This is ClemTheAlien's DWM Rice.
First Git Clone the latest DWM, Dmenu and St repos into your Linux OS or use the binaries uploaded here. The Stock folder holds all of the patches and tar.gz I used to make this install. If you download from Stock, make sure to extract the tar.gzs. 

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

### Xinitrc

Install xorg and xorg-xinit

```sh
sudo pacman -S xorg xorg-xinnit
#Change the install method based upon your linux distro. Clem uses Arch currently.
```

Make and edit .xinitrc and add (you can do this with an echo command also)
```
!#/bin/bash
[add any additional commands you want to run before dwm such as the program that adds ur background before the "exec dwm"]
exec dwm
```

NOTE: If you have any resolution errors use Xrandr to fix them. What you need to do resolution wise might change if you have one or more monitors.


## Ricing
### Patches
Save these patches to your Downloads
https://dwm.suckless.org/patches/alwayscenter/
https://dwm.suckless.org/patches/uselessgap/


or download the patches from this repo 


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

NOTE: Check if each patch works seperately. You might have to do some copy and pasting of C code if the patches dont work. Also delete config.h before you recompile after a patch (after the first patch).


### Wallpaper and Picom 
Install Feh and Picom
```sh
sudo pacman -S feh picom 
```
Set Wallpaper 
```sh
feh --bg-fill [WAllPAPER DIR]/[WALLPAPER]
```

#### Git clone Picom conf
```sh
git clone https://github.com/ClemTheAlien/ClemTheAliensPicomConf
sudo cp picom.conf /etc/xdg/picom.conf

#Recompile DWM afterwards for it to take effect 
```
NOW YOUR DONE :) 

##Extra 

### Runing something concurrently with another keybinding action (Ex: running J4-Dmenu-Desktop with DMENU on Mod+P)
If you want to use j4-dmenu-desktop for a more readable dmenu, insert

```
static const char *j4[] = {"j4-dmenu-desktop", NULL};
```
 under the "/* commands */ section of config.h then insert

 ```
 static const char *j4[] = {"j4-dmenu-desktop", NULL};
 ```

 so that everytime MOD+P is pressed both dmenu and j4-dmenu-desktop

 I HIGHLY recommend learning some C so you fully understand your config.h and DWM in general

### Changing terminal 
 Now if you want to change your terminal change the 
 ```
 static const char *termcmd[]  = { "st", NULL };
 ```

 under the "/* commands */"  section to whatever terminal you want

 Thats all my tips for now :)
 