# Debian setup  
### Software
- Sources
```
#deb cdrom:[Debian GNU/Linux 12.7.0 _Bookworm_ - Official amd64 DVD Binary-1 with firmware 20240831-10:40]/ bookworm contrib main non-free-firmware

deb http://deb.debian.org/debian buster-backports main
deb https://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
deb-src https://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware

deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb-src http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware

deb https://deb.debian.org/debian/ bookworm-updates main contrib non-free non-free-firmware
deb-src https://deb.debian.org/debian/ bookworm-updates main contrib non-free non-free-firmware

deb https://deb.debian.org/debian/ bookworm-backports main contrib non-free non-free-firmware
deb-src https://deb.debian.org/debian/ bookworm-backports main contrib non-free non-free-firmware
```
- Essentials 
```
sudo apt install nvtop btop intel-microcode alacritty simplescreenrecorder 
```



### BSPWM setup
- Software
```
sudo apt install bspwm polybar sxhkd alacritty brightnessctl dunst rofi lxappearance picom ranger flameshot nemo
```
```
sudo apt install gtk2-engines-murrine gnome-themes-extra
```
### GNOME setup
- Uninstalling trash
```
sudo apt autoremove uim-mozc mozc-utils-gui mozc-server mozc-data xiterm+thai mlterm kasumi anthy-common transmission-gtk yelp gnome-calendar gnome-2048 gnome-clocks simple-scan aisleriot evolution five-or-more gnome-font-viewer yelp gnome-klotski lightsoff gnome-mahjongg gnome-maps gnome-mines gnome-nibbles malcontent seahorse gnome-robots rhythmbox iagno shotwell gnome-sudoku swell-foop software-properties-gtk gnome-todo transmission-gtk gnome-weather firefox-esr gnome-chess gnome-games gnome-tetravex gnome-quadrapassel gnome-tali
```


