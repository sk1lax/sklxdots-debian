# Debian setup  
### Software
- Essentials
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
- Installing packages 
```
sudo apt install nvtop btop intel-microcode alacritty simplescreenrecorder pavucontrol ntp blueman git bc module-assistant build-essential dkms nitrogen libqt5svg5 libqt5svg5-dev libqt5x11extras5 libqt5x11extras5-dev qt5-style-kvantum 
```

- Setting up Flatpak
```
sudo apt install flatpak
```
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

- Groups
```
usermod -a -G video,audio,sudo USERNAME
```
### Steam & Drivers setup 
- Nvidia Drivers
```
sudo apt install nvidia-driver 
```
- 32bit Packages 
```
sudo dpkg --add-architecture i386
```
```
sudo apt update && sudo apt full-upgrade
```
```
sudo apt install mesa-vulkan-drivers libglx-mesa0:i386 mesa-vulkan-drivers:i386 libgl1-mesa-dri:i386 nvidia-driver-libs:i386
```
- Steam
```
sudo apt install steam-installer
```
### BSPWM setup
- Software
```
sudo apt install bspwm polybar sxhkd alacritty brightnessctl dunst rofi lxappearance picom ranger flameshot nemo qt5ct 
```
```
sudo apt install gtk2-engines-murrine gnome-themes-extra
```
- Win + Space layout setup
```
sudo localectl --no-convert set-x11-keymap us,ru "" "" grp:win_space_toggle
```
- Disable mouse acceleration
```
sudo nano /etc/X11/xorg.conf.d/40-libinput.conf
```
```
 Section "InputClass"
  Identifier "libinput pointer catchall"
  MatchIsPointer "on"
  MatchDevicePath "/dev/input/event*"
  Driver "libinput"
  Option "AccelProfile" "flat"
 EndSection
```
### GNOME setup
- Uninstalling trash
```
sudo apt autoremove uim-mozc mozc-utils-gui mozc-server mozc-data xiterm+thai mlterm kasumi anthy-common transmission-gtk yelp gnome-calendar gnome-2048 gnome-clocks simple-scan aisleriot evolution five-or-more gnome-font-viewer yelp gnome-klotski lightsoff gnome-mahjongg gnome-maps gnome-mines gnome-nibbles malcontent seahorse gnome-robots rhythmbox iagno shotwell gnome-sudoku swell-foop software-properties-gtk gnome-todo transmission-gtk gnome-weather firefox-esr gnome-chess gnome-games gnome-tetravex gnome-quadrapassel gnome-tali
```

### Realtek Fix
- Installing driver
```
git clone https://github.com/tomaspinho/rtl8821ce.git
```
```
cd rtl8821ce
```
```
sudo m-a prepare
```
```
sudo ./dkms-install.sh
```
- Blacklisting modules
```
sudo nano /etc/modprobe.d/blacklist.conf
```
```
blacklist rtw88_8821ce
blacklist nouveau
```
- Turning Off ASPM
```
sudo nano /etc/default/grub
```
```
# ---------------------------------GRUB OPTIONS---------------------------------
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"
```
```
sudo update-grub
```
