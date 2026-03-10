# Rain World on Linux - mod fix and extras

Rain world works near-flawlessly on WINE/Proton and so this guide will be very short. The only required fix is very short and easy to add. The section related to gamescope is optional and just a nice extra.

## Fixing mods not working
On Steam, open the game's properties and add to your launch options: `WINEDLLOVERRIDES="winhttp=n,b" %command%`.
This fixes third party mods not working on Rain World entirely.

## Sharp upscale without mods and low-latency cursor
Rain World plays at a low resolution and it makes perfect sense, but the upscale to high resolution screens is blurry due to bilinear filtering. Some mods circumvent this, but their ways to do it might be hacky and some users reported issues with those particular mods on Linux. A great alternative is to use gamescope.
Once you have gamescope installed, you can run it from the game's launch options. This will run the game inside the gamescope compositor, and from there you can control upscaling and mouse capture.

Here's a final example of gamescope use:

`WINEDLLOVERRIDES="winhttp=n,b" gamescope -f -F nearest -S fit -w 1229 -h 768 -s 0.4 --force-grab-cursor -- %command%`

* `WINEDLLOVERRIDES="winhttp=n,b"`: The mod fix mentioned earlier, unrelated to gamescope

* `gamescope`: Execute gamescope and have it run your game instead (see below)

* `-f`: Run compositor in fullscreen

* `-F nearest`: Upscale game with nearest neighbor, resulting in sharp but pixelated image (fits Rain World very well)

* `-w 1229 -h 768`: Force the game to detect a screen size of this resolution. This specific resolution is the 16:10 option Rain World provides. **You should change it to the actual resolution you use in-game**

* `-s 0.4 --force-grab-cursor`: Have gamescope capture your cursor directly and set sensibility to 0.4. This is important, otherwise your real desktop cursor will show up on top of the in-game one. This also improves input lag because Rain World's built-in cursor does not read raw mouse input

* `-- %command%`: The argument `--` is how gamescope knows when to stop parsing its settings and any CLI argument that comes after it (which is the game, `%command%`) is the program it has to execute.
