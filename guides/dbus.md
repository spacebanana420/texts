# Setting up User DBus manually

DBus can run as root or as a user, fulfilling different goals. Documentation on running DBus as a user is often with Systemd in mind, leaving questions and confusion about setting it up on other systems.

Even without Systemd, a fully-packed desktop environment like KDE or Xfce initiates a user DBus session, but this is not the case for barebones window managers.

## What happens when you don't have user DBus

Some programs use DBus to communicate with other programs in real-time, but they need specifically a user session DBus. Without it:

* Some programs might fail to start (Waybar)
* File explorers might lack disk mounting and trash bin capabilities
* Panel applets might not work
* Screen recording on Wayland through Pipewire will not work
* And more

## How to run manually

DBus as a user session should be executed before the window manager starts. The command `dbus-run-session` initiates a fully-working user DBus session while also allowing you to pass more commands.

For example, you need user DBus but use Hyprland, you need to launch Hyprland with:

```
dbus-run-session start-hyprland
```

To seamlessly integrate this on your display manager, you have to modify the respective command that a session (such as the Hyprland session starts). These session files are located in `/usr/share/wayland-sessions/` and `/usr/share/wayland-sessions/xsessions`.
