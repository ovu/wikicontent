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

