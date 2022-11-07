# Backup iOS devices from iTunes on Windows

By default, when making a backup on windows for an apple device, it will save it to a directory like this:

```
C:\Users\Davis\Apple\MobileSync\Backup
```

Since I have another hard drive that stores backups and synces it elsewhere, I want to move it.
That can be done by using something similar to symlink (linux):

```
mklink /J "C:\Users\Davis\Apple\MobileSync" "X:\Backups\Dāvis Backup\MobileSync"
```
