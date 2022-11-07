# `xterm-termite`: unknown terminal type error fix

When Anaconda is installed and using termite, you might encounter this error

```
'xterm-termite': unknown terminal type.
```

You can fix this with a symlink:

```
ln -s /usr/share/terminfo/x/xterm-termite ~/anaconda3/share/terminfo/x
```
