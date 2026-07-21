# Supersampling: Perfect Anti-aliasing for Screenshots

When making 2D image works I often use screenshots of games like Minecraft, Vintage Story, Space Engine, Garry's Mod, etc.
These games offer a lot of technical freedom for taking high quality screenshots, one way they do it is by allowing you to take higher resolution screenshots.

Videogames often have [anti-aliasing](https://en.wikipedia.org/wiki/Anti-aliasing), but depending on the technique used (FXAA, MSAA, etc), it might not produce great results.
If you want your screenshot to look sharp, the anti-aliasing implementation built into the game might hinder you a bit.
When this happens, the best approach is supersampling.

[Supersampling](https://en.wikipedia.org/wiki/Supersampling) is effectively taking multiple samples, then reducing them to a single sample which is the average of the ones you took.
In practice, you achieve supersampling by rendering an image at a high resolution then downscaling it with a filter such as bilinear.
The result is a sharp image but with smooth anti-aliased edges.

Some older games used to have this technique as a built-in anti-aliasing implementation called SSAA (supersampling anti-aliasing), but this method is very slow and heavy on memory and so it was replaced by lighter alternatives for gaming.
For taking screenshots and rendering images it's the best you can do for a smooth screenshot, since gaming performance doesn't matter for taking screenshots.
All you have to do is to take a screenshot at a higher resolution than your screen (if the game allows), then scale it down to 1/2, 1/3, 1/4, etc of the original size.

It's important that you scale down in integers so the scaling is even and doesn't fail to remove all aliasing.

Here's a visual example of how an image can change, where at the left the image has aliased edges, and at the right (after scaling) it doesn't:


<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/1/14/Naa-vs-aa.png" width="35%">
</div>
