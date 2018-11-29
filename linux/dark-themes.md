# Dark themes

## Slack 

> [One Dark Theme for Slack | slack-one-dark-theme](https://mallowigi.github.io/slack-one-dark-theme/)

## Boostnote

> Preferences -> Interface

## Chrome

> [Dark Reader - Chrome Web Store](https://chrome.google.com/webstore/detail/dark-reader/eimadpbcbfnmbkopoojfekhnkhdbieeh?hl=en)
> [Material Simple Dark Grey - Chrome Web Store](https://chrome.google.com/webstore/detail/material-simple-dark-grey/ookepigabmicjpgfnmncjiplegcacdbm)

## Visual Studio Code

> Dark+ Material

## HeidiSQL

[gtk - What can be done to make Wine look more integrated into Unity? - Ask Ubuntu](https://askubuntu.com/questions/175868/what-can-be-done-to-make-wine-look-more-integrated-into-unity)

> [Gnome to Wine color scraper · GitHub](https://gist.github.com/endolith/74192#file-wine_colors_from_gtk-py)

> [HOWTO: Change colors of wine applications - Page 3](https://ubuntuforums.org/showthread.php?t=55286&page=3)

```
#!/usr/bin/env python
import pygtk
import gtk


def format_color_string( Color ):
	return "%s %s %s" % (Color.red /256, Color.green/256,  Color.blue/256)
	
def format_color_key( key, Color):
	return "\"%s\"=\"%s\"\n" % (key, format_color_string( Color ))
	

invisible1 = gtk.Invisible()
style1 = invisible1.style

button1 = gtk.Button()
buttonstyle = button1.style

scroll1 =  gtk.VScrollbar()
scrollbarstyle = scroll1.style

menu1 = gtk.Menu()
menuitem1 = gtk.MenuItem()
menu1.add(menuitem1)
menustyle = menuitem1.style

user_reg = """WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\\\Colors]
"""

# http://www.moeraki.com/pygtkreference/pygtk2reference/class-gtkstyle.html
# http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html

user_reg += format_color_key('Scrollbar', scrollbarstyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Background', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ActiveTitle', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('InactiveTitle', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('Menu', menustyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Window', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('WindowFrame', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('MenuText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('WindowText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('TitleText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ActiveBorder', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('InactiveBorder', menustyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('AppWorkSpace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Hilight', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('HilightText', style1.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('ButtonFace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonShadow', style1.bg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('GrayText', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('ButtonText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InactiveTitleText', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('ButtonHilight', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonShadow', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonLight', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InfoText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InfoWindow', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonAlternateFace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonHilight', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('GradientActiveTitle', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('GradientInactiveTitle', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('MenuHilight', menustyle.bg[gtk.STATE_NORMAL])

print user_reg
```
gedit ~/.wine/user.reg
