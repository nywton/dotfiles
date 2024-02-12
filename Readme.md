# Environment
![image](https://github.com/nywton/dotfiles/assets/6857918/22039bb5-5291-46fc-9ff5-16a0f71aea0f)


## Create synlinks to dotfiles

```
$ ln -s -f ~/dotfiles/zshrc  ~/.zshrc
$ ln -s -f ~/dotfiles/nvim  ~/.config/nvim
$ ln -s -f ~/dotfiles/tmux  ~/.tmux
$ ln -s -f ~/dotfiles/kitty  ~/.config/kitty
$ ln -s -f ~/dotfiles/fzf  ~/.config/fzf
$ ln -s -f ~/dotfiles/i3  ~/.config/i3
$ ln -s -f ~/dotfiles/nitrogen  ~/.config/nitrogen
$ ln -s -f ~/dotfiles/picom  ~/.config/picom
```

## Disable grub menu
```
sudo sh -c 'echo GRUB_RECORDFAIL_TIMEOUT=0 >> /etc/default/grub';
sudo update-grub;
```
## Ryzen 5 5600g
* On ubuntu 22.02 the default instalation don´t launch screen after boot.
* You need to access `/etc/default/grub` and set `nomodeset` at:
```
...
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nouveau.modeset=0" # <~
...
```
# Kitty
## Installation
Offical guide: https://sw.kovidgoyal.net/kitty/binary/
## Set as default terminal
```
% sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /home/nywton/.local/kitty.app/bin/kitty 50
```
