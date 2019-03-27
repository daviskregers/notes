```bash
davis@davis-arch  ~  sudo pacman -S numlockx
[sudo] password for davis: 
resolving dependencies...
looking for conflicting packages...

Packages (1) numlockx-1.2-4

Total Download Size:   0.01 MiB
Total Installed Size:  0.01 MiB

:: Proceed with installation? [Y/n] 
:: Retrieving packages...
 numlockx-1.2-4-x86_64                           5.9 KiB  0.00B/s 00:00 [########################################] 100%
(1/1) checking keys in keyring                                          [########################################] 100%
(1/1) checking package integrity                                        [########################################] 100%
(1/1) loading package files                                             [########################################] 100%
(1/1) checking for file conflicts                                       [########################################] 100%
(1/1) checking available disk space                                     [########################################] 100%
:: Processing package changes...
(1/1) installing numlockx                                               [########################################] 100%
:: Running post-transaction hooks...
(1/1) Arming ConditionNeedsUpdate...
 davis@davis-arch  ~  vi ~/.xinitrc 
```

```
 davis@davis-arch  ~  cat ~/.xinitrc 
#! /bin/bash
numlockx &
exec i3
betterlockscreen -w dim
source ~/.fehbg
```
