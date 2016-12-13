i3wm
====

Mod + Enter : Open console (Default)

Mod + V : Open console vertical

Mod + Shift + q : Quit. Kills the current window

Mod + D : Show the applications bar (dmenu)

Change between windows

Mod + Arrow

optionally use the jkl; keys instead of the arrows  

Mod + E: Show tailing mode

Mod + W: Show in tab mode

Mod + r : Resize mode
  User the arrow keys to make the window bigger/shorter

Move window

User the Mod + shift + Arrow key


Workspaces:

Mod + Shift + 2 : Create a new Workspace named 2

To go in a workspace: Mod + 2

Logout:
Mod + Shift + E (Exit)

Lock the screen:
On command line write the command:

i3lock


### Customizing

Custom lock shortcut 

lock using Mod + Shift + x
bindsym $mod+shift+x exec i3lock


After changing the configuration reload it using:
Mod + Shift + r (Reload)

##Start application when i3 is starting (after login)
exec skype

##Customize background
Install the application feh
Run the command feh --bg-scale wallpaper.jpg
After running the command the wallpaper is set as background (however when logging again the config is gone)
Add the following line to the configuration to keep it when logging out:
exec_always feh --bg-scale /home/xxx/Pictures/wallpaper.jpg 
--bg-scale scales the picture without repeating it

##Multiple monitors
Install arandr
Executes it to configure the monitors
Saves the generated configurations as .sh file

Copy the generated command in the i3 configuration and set it to be executed always:
exec_always xrandr ...... 

##Configuring workspaces

Name a workspace:
bind $mod+1 workspace Terminals

It would require to change the command to mode a container into a workspace
bindsym $mod+Shift+1 move container to workspace Terminals

##Using variables in the configuration file
set $workspace1 "Terminals"
Now we can use the variable in the following way:

bind $mod+1 workspace $workspace1
bindsym $mod+Shift+1 move container to workspace $workspace1

##Best practices
The name of the workspaces should contain at the beginning the number of the workspace.
E.g set $workspace1 "1. Terminals"

## Force open some windows in some workspaces
First find the information about the window:
$ xprop
After pressing enter click on the window to be analyzed.

It will show the class of the window.

Copy the second value of WM_CLASS(STRING)

Then add in the configuration file the following entry:
assign [class="Rhythmbox"] $workspace10

Here we are using the variables again.

## Showing icons for workspaces

First it is required to install fonts.
E.g get the font from https://github.com/FortAwesome/Font-Awesome
Download the last release.
In the zip file search a .ttf file. That is the font we want to install.
$ mkdir ~/.fonts
$ mv fontawesome-webfont.ttf ~/.fonts/
Now search in the web for Font awesome cheat sheet and get the icon you want.
Then past the icon inside the name of the workspace.

set $workspace1 "1. Editor <Your icon>"
