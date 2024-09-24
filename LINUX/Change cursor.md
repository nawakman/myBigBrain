[[LINUX]]
```bash
sudo apt intall gnome-tweaks
pipx install win2xcur
```

-GNOME Tweak is an app that allows further customization of Ubuntu (including cursor)
-win2cur is a python script that convert windows .cur and .ani (animated cursor) files to the Ubuntu format

Create a folder with an arbitrary name for your cursors set , inside which create a "cursors" folder

With win2xcur generate cursors from your .cur and .ani with
`win2xcur cursorName.cur -o ./` or `win2xcur cursorName.ani -o ./` 
copy the created file in the "cursors" folder and rename it.

The name of the cursor defines which pointer it will replace:
	-`default` or `left_ptr` for default cursor
	-`wait` for the throbber
	-and much more you can find on internet

then move the arbitrarily named folder to  `/usr/share/icons`

Reload GNOME Tweaks and a cursor option with the name of your arbitrarily named folder should appear, choose it and enjoy!