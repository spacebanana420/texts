# Touhou on Linux: The Manual

This guide serves to help you play and set up the Touhou Project games on Linux-based systems, having a focus on fixing quirks and issues as well as troubleshooting and improvements.

You don't need to read everything here. Most likely you don't have most of these issues, and some issues (the fullscreen ones) are just "what if" scenarios that don't really or usually happen.
The Touhou games run very well out-of-the-box, but they might need one or two adjustments to be perfect.

The information seen here is specific to WINE, Proton and Linux, with a strong focus on Steam but also some mentions of Lutris and WINE forks.
The guide focuses more on troubleshooting issues and improving your experience but not so much on how to install or patch the games.

## Table of Contents

* [Fixing muffled SFX audio](#fixing-muffled-sfx-audio)
* [Fixing thick, unreadable text](#fixing-thick-unreadable-text)
* [Fixing fullscreen issues and stretched game image (fshack)](#fixing-fullscreen-issues-and-stretched-game-image-fshack)
* [Fixing fullscreen issues (Proton and ProtonGE)](#fixing-fullscreen-issues-proton-and-protonge)
* [Fixing fullscreen issues (Gamescope)](#fixing-fullscreen-issues-gamescope)
* [Fixing fullscreen issues (DXVK)](#fixing-fullscreen-issues-gamescope)
* [Sharp upscaling (Gamescope)](#sharp-upscaling-gamescope)
* [Using thcrap on Steam (thcrap-proton)](#using-thcrap-on-steam-thcrap-proton)
* [Using Proton and ProtonGE without owning the games](#using-proton-and-protonge-without-owning-the-games)
* [Fixing frameskip, microstutters or bad frametimes](#fixing-frameskip-microstutters-or-bad-frametimes)
* [Fixing input lag (Touhou 6, 7 and 8)](#fixing-input-lag-touhou-6-7-and-8)
* [Input lag on x11](#input-lag-on-x11)
* [Input lag on Wayland](#input-lag-on-wayland)


## Fixing muffled SFX audio

It's likely that on your setup, the audio for sound effects in most Touhou games is muffled and sometimes distorted.
This is caused by bad resampling from WINE and Proton, but the fix is very easy.

The `wine-staging` variant of WINE comes with a much better resampling that entirely fixes this problem, and some WINE/Proton forks come with it.
The WINE variants that have the good resampler are `wine-staging`, `wine-ge`, `ProtonGE` and `lutris-wine`. Using any of these will fix your issue.

### TLDR

Use one of the following WINE/Proton variants:

* wine-staging
* lutris-wine (available on Lutris, old WINE versions)
* WineGE (available on Lutris and binary available on GitHub)
* ProtonGE (use it with Steam)


## Fixing thick, unreadable text

Touhou games after Touhou 14 can have a very thick text font that makes dialogues hard to read.
This is caused by the antialiasing and subpixel rendering of your desktop.
The method to fix this is very specific to each desktop environment or window manager, but the idea is to adjust font antialias settings and use grayscale subpixel rendering instead of RGB or similar.

The most desktop-agnostic way to fix this would be to edit the file in `~/.config/fontconfig/fonts.conf`.
If editing this file, this parameter could help:

```
 <match target="font">
  <edit name="rgba" mode="assign">
   <const>none</const>
  </edit>
 </match>

 <match target="font">
  <edit name="hintstyle" mode="assign">
   <const>hintslight</const>
  </edit>
 </match>
```


## Fixing fullscreen issues and stretched game image (fshack)

Upstream WINE distributions such as vanilla WINE or wine-staging do not come with the `fshack` patch.
This patch makes it so your fullscreen application run as borderless instead of exclusive fullscreen (while still allowing for low input lag by disabling desktop vsync).

You need to switch to a WINE variant that supports or out-of-the-box contains fshack, such as lutris-wine, wine-ge, ProtonGE or just plain Proton.

### TLDR

Switch to WineGE, Proton or ProtonGE or enable fshack on Lutris/Bottles.


## Fixing fullscreen issues (Proton and ProtonGE)

If you have fullscreen issues on Steam, try disabling DXVK entirely by adding `PROTON_USE_WINED3D=1 %command%` to your game's startup parameters.


## Fixing fullscreen issues (Gamescope)

If you no matter what have fullscreen issues on Touhou, especially if it's specific games, you can try using Gamescope.
Install `gamescope` on your system and add to your game's startup parameters:
```sh
gamescope -W <WIDTH> -H <HEIGHT> -w <GWIDTH> -h <GHEIGHT> -f -- %command%

# Make sure to replace <WIDTH> and <HEIGHT> with your screen's native resolution, for example -W 1920 -H 1080
# Make sure to replace <GWIDTH> and <GHEIGHT> with the Touhou game's resolution, for example -w 640 -h 480 (for old games) or -w 1280 -h 960 (for modern games)
```


## Fixing fullscreen issues (DXVK)

If your fullscreen issues are not fixed with the methods above, you can try to use WINED3D's OpenGL backend instead of DXVK's Vulkan one.
This is not guaranteed to fix your issue, but it's worth trying. On Steam and Proton, you can use the startup parameter `PROTON_USE_WINED3D=1 %command%`.


## Sharp upscaling (Gamescope)

You can achieve sharp scaling with nearest neighbor by using gamescope:
```sh
gamescope -W <WIDTH> -H <HEIGHT> -w <GWIDTH> -h <GHEIGHT> -f -F nearest -- %command%

# Make sure to replace <WIDTH> and <HEIGHT> with your screen's native resolution, for example -W 1920 -H 1080
# Make sure to replace <GWIDTH> and <GHEIGHT> with the Touhou game's resolution, for example -w 640 -h 480 (for old games) or -w 1280 -h 960 (for modern games)
```


## Using thcrap on Steam (thcrap-proton)

When launching a Touhou game bought on Steam with thcrap outside Steam, the playime is not registered since Steam doesn't detect you are playing.
Trying to manually launch thcrap from Steam has it "close" the game on the launcher because it launches the Touhou game as a subprocess instead.

The easy solution: use [thcrap-proton](https://github.com/nerusuki/thcrap-steam-proton-wrapper). Once installed, add this to your game's startup parameters:

`thcrap_proton -c en.js -- %command%`


## Using Proton and ProtonGE without owning the games

If you pirated a Touhou game and do not own the Steam version, but you want to use ProtonGE or Proton, you can add your game to your Steam library as a non-Steam game.

* Go to your steam library
* At the very bottom of the launcher, click "Add a Game" and "Add a non-Steam Game"
* Choose the executable to run
* Configure the game's properties, if you change the executable make sure the path is encapsulated inside quotation marks again


## Fixing frameskip, microstutters or bad frametimes

I noticed that Touhou games can have microstutters sometimes. This is severely improved by disabling FSYNC and ESYNC.
These options are available on most game launchers and WINE helpers like Lutris. On Steam, you need to set the startup parameter `PROTON_NO_ESYNC=1`.

Using WINED3D instead of DXVK might also help, though at cost in performance that is negligible unless you use 2000s or early 2010s integrated graphics.
On Steam, you can do that by setting the startup parameter `PROTON_USE_WINED3D=1 %command%`. You can combine both with `PROTON_NO_ESYNC=1 PROTON_USE_WINED3D=1 %command%`.

Using a refresh rate that is not divisible by 60 (such as 75Hz) also introduces microstutters. 60Hz, 120Hz or above is recommended.


## Fixing input lag (Touhou 6, 7 and 8)

Touhou 6, 7 and 8 have very notable input lag out of the box.
You need to download vpatch with the appropriate DLL file for the game you want to play, then you launch Touhou from its executable.


## Input lag on x11

Make sure to disable your desktop compositor on X11. The desktop compositor is the software component that handles desktop vsync and effects (such as shadows and blur).
Depending on which desktop environment you use, desktop vsync might stay enabled even on fullscreen games. In this case, you need to manually disable it.


## Input lag on Wayland

Some Wayland compositors do not disable vsync even when you are playing a fullscreen game.
Some compositors such as Hyprland and KDE Plasma let you enable the ability to disable vsync while a fullscreen application is open, but some (such as GNOME) do not.
