# pretty-wiman
Bash script to move and resize windows, making it prettier when using basic WMs like OpenBox

This script is intended to use with one or two monitors, one alongside the other.
If you use more than 2 screens or one is above the other, you will need to edit the script to make it work properly to your needs.

To use the script you will need these dependencies, all of them available in the most popular GNU/Linux distributions:
- xrandr
- awk
- xdotool
- bc

If you have them installed, is easy as running for example:

```pretty-wiman W```

For resizing the active window half the width of your screen and place it to the West (left).

The available arguments are:
- W (West):
    - Moving the window to the left and with the width halved
- N (North):
    - Moving the window to the top and with the height halved
- E (East):
    - Moving the window to the right and with the width halved
- S (South):
    - Moving the window to the bottom and with the height halved
- SW (South West):
    - Moving the window to the upper left corner with width and height both halved
- NW (North West):
    - Moving the window to the upper right corner with width and height both halved
- NE (North East):
    - Moving the window to the lower left corner with width and height both halved
- SE (South East):
    - Moving the window to the lower right corner with width and height both halved
- C (Center):
    - Respect window size, but moving it to the center of the screen
- F (Fullscreen):
    - Make the window fullscreen, but with a slight margin
- U (Unscreen):
    - Rollback the window size before going fullscreen
- TF (Toggle Fullscreen):
    - Switches between F and U
- TD (Toggle Display):
    - Moves the window from one display to the other, can be problematic if using monitors with different resolutions
- CC (Clear Cache):
    - When going back and forth from fullscreen, pretty-winman creates temporary files to store the window geometry, this removes all the files.
    - Useful for example clearing the cache before start X Server

Here you have a snippet using it inside Openbox configuration file `rc.xml`:
```
    <keybind key="W-Left">
      <action name="Execute">
        <command>pretty-wiman W</command>
      </action>
    </keybind>
    <keybind key="W-Up">
      <action name="Execute">
        <command>pretty-wiman N</command>
      </action>
    </keybind>
    <keybind key="W-Right">
      <action name="Execute">
        <command>pretty-wiman E</command>
      </action>
    </keybind>
    <keybind key="W-Down">
      <action name="Execute">
        <command>pretty-wiman S</command>
      </action>
    </keybind>
    <keybind key="W-S-Left">
      <action name="Execute">
        <command>pretty-wiman SW</command>
      </action>
    </keybind>
    <keybind key="W-S-Up">
      <action name="Execute">
        <command>pretty-wiman NW</command>
      </action>
    </keybind>
    <keybind key="W-S-Right">
      <action name="Execute">
        <command>pretty-wiman NE</command>
      </action>
    </keybind>
    <keybind key="W-S-Down">
      <action name="Execute">
        <command>pretty-wiman SE</command>
      </action>
    </keybind>
    <keybind key="W-C-Left">
      <action name="Execute">
        <command>pretty-wiman TD</command>
      </action>
    </keybind>
    <keybind key="W-C-Right">
      <action name="Execute">
        <command>pretty-wiman TD</command>
      </action>
    </keybind>
    <keybind key="W-c">
      <action name="Execute">
        <command>pretty-wiman C</command>
      </action>
    </keybind>
    <keybind key="W-F11">
      <action name="Execute">
        <command>pretty-wiman TF</command>
      </action>
    </keybind>
```

I hope you enjoy it!
Feel free to modify it to your liking or making it better.
Also feel free to email me with your changes!
