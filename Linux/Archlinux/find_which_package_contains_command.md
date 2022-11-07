# Find which package contains command

```bash
pacman -Fy # sync database
pacman -Fs genfstab
```

```
[root@davis-arch davis]# pacman -Fs genfstab
extra/arch-install-scripts 20-1
    usr/bin/genfstab
```