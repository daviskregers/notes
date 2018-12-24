# Arch post installation

## Add your account

```bash
useradd -m -G wheel,users -s /bin/bash davis
```

## Change password

```bash
passwd davis
```

## Install sudo & add to sudoers

```bash
pacman -S sudo
visudo
```

Add `davis ALL=(ALL) ALL` after the `root ALL=(ALL) ALL`.


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

## Install i3 (from dotfiles)

```bash
pacman -S i3-wm i3status i3blocks dmenu xorg xorg-xinit git
git clone https://github.com/daviskregers/dotfiles.git
cd dotfiles
chmod +x sync.sh
./sync.sh
chmod +x apps.sh
./apps.sh
```

if something fails due to keys / signatures, add them

```bash
gpg --recv-keys A2C794A986419D8A
```

# Install i3 (from scratch - skip if dotfiles used)

```bash
pacman -S i3-wm dmenu xorg xorg-xinit
nano .xinitrc
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


