# Arch linux installation

Download .iso from [https://www.archlinux.org/download](Arch linux downloads)
Then write the iso to a bootable flash, where X is the flash device identifier. (can be found using `lsblk` command).

```bash
dd if=/path/to/image.iso of=/dev/sdX
```

Reboot computer and boot into the arch stick.


Check for efivars and internet connection.

```bash
ls /sys/firmware/efi/efivars
ping archlinux.org
```

If the efivars returns a list of files instead of an error, you will need to make an EFI partition in later steps.


## Format drives

```bash

fdisk -l
fdisk /dev/sdX

```

Where X is the drive you want to install the arch to. This will open an interface where you can manage drive partitions, to delete them all - enter 
the command `d` a few times.

### Create EFI partition (skip if no efivars found)

1. Press n
2. Select p (primary)
3. Press enter (1)
4. Press enter (start at the very start)
5. Write `+550M` - this will create a 550M partition

### Create boot partition (skip if efivars found)

1. Press n
2. Select p (primary)
3. Press enter (2)
4. Press enter (start at the very start)
5. Write `+200M` - this will create a 200M partition

### Create SWAP partition

1. Press n
2. Select p
3. Enter
4. Enter
5. +24G -- 150% of RAM

### Create / root partition

1. Press n
2. Select p
3. Enter
4. Enter
5. +50G

### Create /home partition 

1. Press n
2. Select p
3. Enter
4. Enter
5. Enter (takes up the rest of the drive)

### Apply changes

There are no changes made to the drive yet. To apply them press `w`. Note that it will wipe your hd clean and all the data on it will be lost.


### Make file systems

```bash

mkfs.ext4 /dev/sda1 or mkfs.fat -F32 /dev/sda1 # (no efivars vs efivars)
mkfs.ext4 /dev/sda3
mkfs.ext4 /dev/sda4
mkswap /dev/sda2

```

## Mount drives

```bash
mount /dev/sda3 /mnt
mkdir -p /mnt/boot /mnt/home /mnt/efi
mount /dev/sda1 /mnt/boot
mount /dev/sda1 /mnt/efi
mount /dev/sda4 /mnt/home
```

## Install Arch

```bash
pacstrap /mnt base base-devel
```

## Write the mounts to `fstab`

```bash
genfstab /mnt -U >> /mnt/etc/fstab
```

## Change root to freshly installed arch

```bash
arch-chroot /mnt
```

## Apply time settings & locales

```bash

ln -sf /usr/share/zoneinfo/Europe/Riga /etc/localtime
hwclock --systohc

nano /etc/locale.gen # uncomment wanted locales
locale-gen

nano /etc/locale.conf # put LANG=en_US.UTF-8
nano /etc/hostname # put your machine hostname like `davis-arch`
```

## Set up hosts

```bash
nano /etc/hosts
```

```
127.0.0.1	localhost
::1		localhost
127.0.1.1	davis-arch.localdomain davis-arch
```

## Change root password

```bash
passwd
```

## Install grub

```bash
pacman -S grub os-prober
grub-install --target=i386-pc /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
```

## Install network manager

```bash
pacman -S networkmanager
systemctl enable NetworkManager
```

## Exit setup

Press `CTRL+d` or `exit` and type `reboot`.


