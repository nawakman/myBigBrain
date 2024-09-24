[[LINUX]]
for pictures display
```bash
sudo snap install ascii-image-converter
ascii-image-converter -bC ~/Downloads/edgrerunnerLucyWallpaper.png
#b for braille, C for color
```
for video display
```bash
sudo apt install mpv
mpv --vo=tct ~/Downloads/stickBugMeme.mp4#better
#tct stands for TrueColorTerminals
#OR
mpv --vo=caca ~/Downloads/stickBugMeme.mp4#pixelated with horrible characters
#caca is from libcaca, stands for ColourAsCiiArt
```