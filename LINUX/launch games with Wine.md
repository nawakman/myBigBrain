[[LINUX]]
https://www.reddit.com/r/linux_gaming/comments/s7s08a/how_do_i_run_games_through_wine_guide/

First install wine and winetricks (winetricks allows you to install required windows dll)

```bash
sudo apt install wine64
sudo apt install winetricks
```

launch winetricks, *Select the default Wineprefix/Install a Windows dll or component* , then tick the latest *vcrun*

A **Prefix** is a folder containing the windows settings and configurations needed for a game to launch, you can make multiple prefixes and switch to the good one following the game (some work on 32bits machine, some on 64), preferably, each game has its own prefix, game files will be stored on a fake C: disk in the prefix

In your Game Folder, create a Prefix with wintricks *create new wineprefix*, then with winetricks *Select the default Wineprefix/Run an arbitrary executable*, run the game installer and install

Then create the following shell script to launch the game, here for exemple I want to run Noita

```bash
#switch to the corresponding Prefix
export WINEPREFIX=~/Games/Noita.v75522/Prefix

#you need to cd to the executable directory before running it with wine
#https://askubuntu.com/questions/934622/running-wine-applications-from-different-terminal-paths-yield-different-results
cd ~/Games/Noita.v75522/Prefix/drive_c/GOG\ Games/Noita/ && wine-stable noita.exe

```