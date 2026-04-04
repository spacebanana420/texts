# Running Pipewire without Systemd

Pipewire does not depend on any particular init system to function, however, it has to be executed as a user. Systemd (and OpenRC) supports user mode for services, and so Linux systems that use Systemd take care of this step for you, but this is not the case for other distros that use any other kind of init system, and so on these you must set it up yourself.

## How it is launched

You can run Pipewire and its components by running the commands `pipewire`, `wireplumber` and optionally `pipewire-pulse` for pulseaudio support.

The most convenient way to launch these programs is by executing them on desktop startup. Most if not all desktop environments and window managers let you execute programs on startup, so you can assemble your own desktop software of your choice. Xfce has this, KDE has this, Hyprland has this, Wayfire and Labwc have this, etc.

## The script

A convenient way to run all the 3 Pipewire components regardless of how you run it is to put it all inside a shell script:

```
touch run-pipewire
chmod +x run-pipewire
```

Now open it with your of choice and paste:

```
#!/bin/sh

pipewire & pipewire-pulse & wireplumber &
```

The `&` symbol allows the programs to run in parallel, while also ending the script instead of waiting for completion. You can now execute this script on launch on your graphical environment, though details are specific to the desktop you use.
