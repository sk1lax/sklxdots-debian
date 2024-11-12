# Dots setup 
### Processing

# Themes
### Processing 

# Personal Debian setup  
### Software
- Sources
```
sudo nano /etc/apt/sources.list
```
```
deb http://deb.debian.org/debian/ testing main contrib non-free non-free-firmware
deb-src http://deb.debian.org/debian/ testing main contrib non-free non-free-firmware

deb http://security.debian.org/debian-security testing-security main non-free-firmware
deb-src http://security.debian.org/debian-security testing-security main non-free-firmware
```
- Installing packages
```
sudo apt install xorg pipewire pipewire-pulse pipewire-alsa alsa-utils xorg network-manager pipewire-jack
```
```
sudo apt nala install nvtop btop intel-microcode alacritty simplescreenrecorder pavucontrol ntp git bc module-assistant build-essential dkms geany file-roller qbittorrent
# libqt5x11extras5 libqt5x11extras5-dev libqt5svg5 libqt5svg5-dev blueman nitrogen 
```
```
sudo apt install zsh zsh-syntax-highlighting zsh-autosuggestions
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
- Drivers
```
sudo apt install nvidia-driver mesa-utils
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
sudo apt install bspwm polybar sxhkd alacritty dunst rofi nwg-look picom ranger flameshot nemo qt5-style-plugins qt5ct qt5-style-kvantum qt5-style-kvantum-themes xserver-xorg-input-synaptics xdg-desktop-portal-gtk xdg-desktop-portal imagemagick brightnessctl brightnessctl-dev lightdm pamixer feh lightdm-gtk-greeter-settings redshift redshift-gtk
```
```
sudo apt install gtk2-engines-murrine gnome-themes-extra libgtk-3-dev libgtk-3-bin libgtk-3-common libgtk-4-dev libgtk-4-bin libgtk-4-common libgtk-4-1 libgtk-4-dev libgtk2.0-bin libgtk2.0-common libgtk2.0-0t64
```
- Layout setup
```
#sudo localectl --no-convert set-x11-keymap us,ru "" "" grp:caps_toggle
```
```sudo nano /etc/vconsole.conf```
```
# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.
XKBLAYOUT="us,ru"
XKBOPTIONS="grp:caps_toggle,grp_led:scroll"
BACKSPACE="guess"
XKBMODEL="pc105"
XKBVARIANT=","
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
- Touchpad Gestures
```
sudo nano /etc/X11/xorg.conf.d/synaptics.conf
```

```
  GNU nano 7.2                                                     synaptics.conf
Section "InputClass"
        Identifier      "Touchpad"                      # required
        MatchIsTouchpad "yes"                           # required
        Driver          "synaptics"                     # required
        Option          "MinSpeed"              "0"
        Option          "MaxSpeed"              "0"
        Option          "MinSpeed"              "0.9"
        Option          "MaxSpeed"              "0.9"
        Option          "AccelFactor"           "0.0"
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "3"     # multitouch
        Option          "TapButton3"            "2"     # multitouch
        Option "VertEdgeScroll" "on"
        Option "VertTwoFingerScroll" "on"
        Option "HorizEdgeScroll" "on"
        Option "HorizTwoFingerScroll" "on"
        Option "CircularScrolling" "on"
        Option          "CoastingSpeed"         "8"
        Option          "CornerCoasting"        "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollTrigger"     "2"
        Option          "EdgeMotionUseAlways"   "1"
        Option          "LBCornerButton"        "8"     # browser "back" btn
        Option          "RBCornerButton"        "9"     # browser "forward" btn
        Option          "EmulateTwoFingerMinZ"  "35"
        Option          "EmulateTwoFingerMinW"  "8"
        Option "Ignore" "on" # disable touchpad
EndSection

```

```
xprop -spy #to get window name
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

### Setting up theme fix
```
nano ~/.Xresources
```
```
#
Xcursor.theme: Bibata-Modern-Classic
```
```
nano ~/.xprofile
```
```
#
xrdb ~/.Xresources
```

- Flatpak cursor theme
```
nano /home/skilax/.local/share/flatpak/overrides/global
flatpak -u override --env=XCURSOR_PATH=~/.icons
flatpak -u override --env=XCURSOR_THEME=Bibata-Modern-Classic
flatpak -u override --filesystem=/home/$USER/.icons/:ro 
flatpak -u override --filesystem=xdg-config/gtk-3.0:ro
```

### Network Fix
```
sudo nano /etc/network/interfaces
```
```
# This file describes the network interfaces available on>
# and how to activate them. For more information, see int>

source /etc/network/interfaces.d/*

# -------------- Comment these lines:

# The loopback network interface
#auto lo
#iface lo inet loopback
#allow-hotplug wlo1
#iface wlo1 inet dhcp
#       wpa-ssid
#       wpa-psk
```

### System Enviroments 
```
sudo nano /etc/environment
```
```
MUTTER_DEBUG_FORCE_KMS_MODE=simple
QT_STYLE_OVERRIDE=kvantum
XDG_CURRENT_DESKTOP=GNOME
QT_QPA_PLATFORMTHEME=qt5ct
GTK_THEME=Graphite-blue-Dark
XDG_CURRENT_DEKSTOP=gnome
GTK_USE_PORTAL=1
XCURSOR_DISCOVER=1
```
### Reminders 
- Fastest mirrors using nala
```
sudo nala fetch
```




```
sudo systemctl disable avahi-daemon
```

