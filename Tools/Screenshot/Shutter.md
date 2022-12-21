---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: tool
Source: https://www.postman.com/
Tags: [development/tools/screenshot, development/tools/linux, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

```
sudo apt install shutter
```

## Replace default screenshot software with shutter

In mint you can go to "Keyboard settings -> Custom shortcuts" and add a new shortcut for the "Print Screen" button. It will execute `shutter -s` command which stands for selected area.

![](2018-12-11-11-35-48.png)

## Annotating screenshots & disabled features

```
sudo add-apt-repository ppa:linuxuprising/shutter
sudo apt update
sudo apt install gnome-web-photo
sudo apt install libgoo-canvas-perl
```

And restart shutter and there will be an editing tool available, where you can anotate.

![](2018-12-11-13-22-30.png)