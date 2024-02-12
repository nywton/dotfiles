## Arch Linux Personal Settings

## Installation
* Use rufus or balenaetcher to create a usb stick.
* boot on UEFI mode
* change linux kernel params on boot by typing `e` or `tab` in the bootloader screen and add `nomodeset` as kernel params (for ryzen 5 5600g CPU)

### Verify the boot mode
Ensure be using UEFI mode otherwise `archinstall` script fails on patitioning.<br>
To verify the boot mode, check the UEFI bitness:
```
$ cat /sys/firmware/efi/fw_platform_size
```
### Set the console keyboard layout and font
The default console keymap is US. Available layouts can be listed with:
```
$ localectl list-keymaps
```
To set the keyboard layout, pass its name to loadkeys(1). For example, to set a German keyboard layout:
```
$ loadkeys br-abnt2 (for pt-br microsoft keyboard)
```
Init the gpg keys:
```
$ pacman-key --init
$ pacman-key --populate archlinux
```

### Archinstall script

To install by a helper type:
```
# archinstall
```

#### Personal setup for Install Script:
* Select best mmirrors (Brazil, US)
* Select `ext4` for partition and `best-effort default partition layout`
* set locales (keyboard layout is: br-abnt2 for Microsoft Keyboards)
* add an user account
* Select `Pipewire` as audio server
* Add `git` and `neovim`
* Use `NetworkManager` as Network configuration
* Use `Brazil/East` as `Timezone`
* Use `multlib` as Optional Repositories (Just in case you need compile [32bit libraries as well)[https://wiki.archlinux.org/title/official_repositories])

## First boot
### Install Yay
To be able to acces AUR you must install yay https://github.com/Jguer/yay
```
# Install Yay

$ pacman -S --needed git base-devel
$ cd /opt
$ sudo git clone https://aur.archlinux.org/yay.git 

# change owner to be able to execute yay
sudo chown -R $USER:$USER yay

$ cd yay
$ makepkg -si

# update by run
$ yay -Suy
```

## Graphics Drivers
* https://wiki.archlinux.org/title/AMDGPU#Installation
* on the Ryzen 5 5600g it's not booting thought the HDMI1 port. Try a different port if you get no display after booting menu.

### Force resolution (removes nomodeset)
https://raw.githubusercontent.com/torvalds/linux/master/Documentation/fb/modedb.rst
update: For the current version, arch on ryzen5 5600g is not adressing default tty to HDM1. If you getttig no screen after boot, try use another input fot the monitor. 

## Audio
On this current version, archlinux adds conflicting libs for audio `wireplumper` + `pipewire-media-session`. Reinstalling `wireplumber` may fix the audio. https://bbs.archlinux.org/viewtopic.php?id=282119

```
$ sudo pacman -S alsa-firmware alsa-utils
$ sudo pacman -S pipewire pipewire-pulse pipewire-alsa pipewire-jack pipewire-media-session
$ sudo pacman -S wireplumber
```

## SSH Keys
```
$ ssh-keygen -t rsa
```
## Zsh
https://wiki.archlinux.org/title/zsh
