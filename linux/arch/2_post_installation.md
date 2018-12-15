# Arch post installation

## Add your account

```bash
useradd -m -g users -s /bin/bash davis
```

## Instasll sudo & add to sudoers

... 

## Install i3

```bash
pacman -S i3-wm dmenu xorg xorg-xinit
nano ~/.xinitrc 
```

```
#! /bin/bash
exec i3
```

```
nano /etc/profile
```

```
# autostart systemd default session on tty1
if [[ "$(tty)" == '/dev/tty1' ]]; then
	exec startx
fi
```

# Install `yaourt`

```
sudo pacman -S base-devel wget git
cd /tmp
git clone https://aur.archlinux.org/package-query.git
cd package-query
makepkg -si
cd ..
git clone https://aur.archlinux.org/yaourt.git
cd yaourt
mkpkg -si
cd ..
yaourt -Syu
rm -rf package-query/ yaourt/
```

## Add sound

```
pacman -S alsa-utils
alsamixer
yaourt -S asoundconf
asoundconf list
asoundconf set-default-card AIMO
speaker-test -c2
```

## Multiple monitors

```
sudo pacman -S arandr
arandr
```


