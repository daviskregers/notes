---
Created: 2022-11-28 15:52:58
Modified: Sunday 27th November 2022 15:52:30
Type: wiki
Source: https://wiki.archlinux.org/title/Dolphin#Mismatched_folder_view_background_colors
Tags: [development/linux/dolphin, review]
---

When running Dolphin under something other than Plasma, it is possible the background color in the folder view pane will not match the system Qt theme. This is because Dolphin reads the folder view's background color from the `[Colors:View]` section in `~/.config/kdeglobals`. Change the following line to the RGB value you prefer (it may be given in the form \#RRGGBB or R,G,B):

~/.config/kdeglobals
```
[Colors:View]
BackgroundNormal=#2E2E2E
```

If you get a blue border around the folder view pane (if you are in split view it will only be around the focused pane), you may get rid of it by applying the `fusion-fixes.qss` style sheet via the qt5ct app. This [answer](https://unix.stackexchange.com/a/683366) describes what to do to get the adwaita dark theme working for dolphin under Gnome.

Alternatively, use [kvantum](https://archlinux.org/packages/?name=kvantum) to manage your Qt5 theming. For instructions on usage see the [Kvantum](https://github.com/tsujan/Kvantum/blob/master/Kvantum/README.md) project homepage.