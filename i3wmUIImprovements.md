i3 UI improvements
==================

Install the font Yosemite San Francisco
https://github.com/supermarin/YosemiteSanFranciscoFont

unzip the downloaded file

Copy all .ttf files into another directory:
mv * .ttf ~/.fonts/

Set the fonts in the i3 config
Change from monospace to:

font pango:System San Francisco Display 13

Install lxappearance

lxappearance creates a configuration file that can changed later

cd ~/
ls 

After applying some configuration with lxappearance it will create a config file

~/.gtkrc-2.0

That is the configuration file.

Change the font in the gtkrc config file:

gtk-font-name="System San Francisco Display 13"

For GKT3 there is another configuration file located in (some linux systems may have it):

~/.config/gtk-3.0/settings.ini

Change the font there as well

gtk-font-name=System San Francisco Display 13

Now lxappearance should show the configured font

Note: Check as well infinality to have a better font rendering

# Better UI in all windows

Use nautilus or install thunar as a file manager

Install gnome-icon-theme-full

Maybe the last command is just needed for Ubuntu

Use the Arc-theme to impreve the UI

It can be found here:
https://github.com/horst3180/Arc-theme

Change the theme in lxappearance

# Improve the icons

Install the Moka icons

http://samuelhewitt.com/moka/download

Download the Moka Icon Theme

Change the theme in lxappearance

# Changing dmenu
Replace dmenu with rofi (window switcher, run dialog and dmenu replacement)

Intallation for Fedora can be found here:
https://copr.fedorainfracloud.org/coprs/yaroslav/i3desktop/

Install Rofi using the following commands. Add a new repo for dnf.
#dnf copr enable yaroslav/i3desktop
#dnf install rofi
