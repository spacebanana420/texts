# Fixing GIMP crashes on Wayfire

GIMP's Wayland support is still a bit unreliable, and it might crash occasionally compared to when you run it on KDE or GNOME.
It seems that on Wayfire GIMP crashes often/easily.

## Common error

If you launch GIMP from a terminal (and maybe you need `--verbose` argument), once it crashes you might see this error:

```
(gimp:22837): Gdk-WARNING **: 21:38:27.583: Couldn't map window 0x5587561be610 as subsurface because its parent is not mapped.

(gimp:22837): Gdk-WARNING **: 21:38:27.583: Couldn't map window 0x5587561be610 as subsurface because its parent is not mapped.
Gdk-Message: 21:38:27.600: Lost connection to Wayland compositor.
/usr/lib/gimp/3.0/plug-ins/script-fu/script-fu: fatal error: GIMP crashed
```

## Mitigation

The easiest way to fix or at least significantly lower probability of GIMP crashing on Wayfire is to increase the `transaction_timeout` setting on your Wayfire INI config:

```ini
# Originally 100, causes frequent GIMP crashes
# Increase it as much as you need
[core]
transaction_timeout = 800
```

The documentation for this setting can be found [here](https://github.com/WayfireWM/wayfire/blob/master/metadata/core.xml).
