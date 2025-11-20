# Playing Slenderman's Shadow (FPSC) games on Linux

The Slenderman's Shadow series has 2 major versions, the games made in the FPS Creator engine and the standalone game made in Unity. I am a fan of the older FPSC version and I noticed how on Linux the game would not work at all and even on Windows they would have weird quirks, but I managed to find a solution and I want to share the procedure here. This guide covers the steps to make the older SMShadow games made in the FPSC engine work on Linux (with a few catches).

## Bypassing launcher error "attempt to call a nil value"

If you downloaded the games from the official source the real game will be package inside a loosely-encrypted zip file called "game.enc", and the exposed executable is just a launcher that extracts the game's contents and runs them. This launcher does not work at all, and a fix for this is unknown, instead why not entirely bypass it?

[In the comments for the Unity v1.3 version](https://marcsteene.itch.io/slendermans-shadow/comments?after=0) there is a person which extracted the game files from the game.enc zip archive and uploaded them [here](https://mega.nz/file/UbAQmTbA#zsFG-YYoFEQ7ukQVYOFqUNk4eRCzFfHZgQLOpm-4hzw). Download the games here as they are extracted and will skip the launcher part entirely, bypassing the nil value error.

## Fixing the screen being green

In-game post-processing is not working at all for me, resulting in a green screen. If you have the same problem, open the game's `setup.ini` file, locate the setting `postprocessing` and set it to `0`. This will disalbe the game's post-processing effects but at least it fixes the green screen issue.

## Mansion: The mementos and keys are invisible!

These objects use a special shader that makes them glow to be easier to spot. For some reason it does not work well with WINE/Proton, making the game unable to properly render the objects and they remain invisible. To fix this, you can disable the glowing effect. Open `setup.ini`, locate the setting `useeffectsonentities` and set it to `0`. Now the mementos and keys do not glow but at least they render properly.

## Misc: other unknown issues

If you have any other issues besides this, try to use Proton instead of WINE, and if Proton is not enough you can always try ProtonGE. I recommend adding the games into Steam as non-steam games to leverage the Steam runtime and Proton easily.
