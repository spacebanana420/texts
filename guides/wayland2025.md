# My experience with Wayland (2025)

I have always been a hardcore x11 user, stubbornly refusing to switch to Wayland due to its immaturity when what I use "just works", but recently I got curious to try 3 different Wayland setups to see if I'm ready for the switch yet.

## My setup

I tried 3 different Wayland environments: Hyprland, Wayfire and Labwc. In all of the compositors I used the Xfce suite (xfce4-session or xfdesktop and xfce4-panel). All the tests were done on Alpine Linux (edge repository) on an AMD iGPU (780M) with a laptop screen of 2560x1600@120Hz. For all of these desktops I used fractional scaling ranging between 1.6x and 1.7x.

# Hyprland + Xfce

Hyprland was the first compositor I used. I was very attracted to the idea of using Hyprland because of its wiki as well as Vaxry's effort to making Wayland better.

Hyperland works great and is highly configurable, but it's the desktop that interoperates the least with Xfce components sadly. On start, I launch xfce-session which as consequence launches the whole of Xfce except for Xfwm, including not only the panel and wallpaper but also display settings, Dbus configurations (for leaving session) and detection of other disk devices on Thunar. The alternative would be to independently launch xfce4-panel, xfdesktop and a script I made to run pipewire on non-systemd distros.

Xfdesktop provides wallpaper functionality but sometimes breaks keyboard and mouse functionality on Hyprland for some reason.

Xfce panel's workspaces menu does not detect Hyprland's workspaces.

# Labwc + Xfce

Labwc is a minimal compositor inspired by Openbox. I decided to try out this compositor because it's the default choice for experimental Wayland Xfce and it's focus on correctness is attractive.

Starting Xfce Wayland session with Labwc makes it so the keyboard layout is always reset to default (US), and so it's better to run Labwc directly first and add Xfce components to the autostart file.

The cursor theme I use only partially works on Labwc. For example when adjusting a slider, the cursor disappears.

Just like in Hyprland, you need to run xfce-session so that Xfce is integrated properly, but if that's not a concern you have then you can run the components manually. Launching my pipewire script works unlike on Hyprland, but Xfdesktop does not work at all, leaving the background as a black screen. Other wallpaper tools like wpaperd work, but they will not work in autostart if xfdesktop or xfce4-session are also in autostart.

Unlike Hyprland and Wayfire, Labwc seems to have no way to configure your display's settings, instead you are supposed to run a wlr-randr command from the autostart file. If xfce4-session is executed, Labwc inherits Xfce's display settings however.

Labwc is the least intuitive desktop of the 3 to configure because of the XML syntax of the configuration file, but after a few minutes of reading, experimenting and using a default config as example you figure it out.

Xfce's workspaces menu somehow autodetects and interacts with Labwc's own workspaces and that's great. This doesn't happen on the other compositors.


# Wayfire + Xfce

Wayfire is a very quirky compositor because of all the animations and plugins it has. The default configuration has many things I don't like such as wobbly windows, but it doesn't take long to disable them. After tinkering the compositor to my liking it's great, though it does seem to use more CPU than Labwc slightly.

Wayfire works the best with Xfce components compared to the other compositors I tried and the experience overall is pleasant when it comes to integrating all these components together.

Configuration is very good and decently extensive, I took a liking to merely setting up Wayfire.

Strangely enough, some GTK applications apply the GTK theme on the title bar, while other applications use Wayfire's theme.

Wayfire, unlike Labwc and Hyprland, does not have a setting to enable screen tearing for fullscreen applications or programs in other circumstances. Screen tearing has its usefulness for gaming, primarily low input delay.

# Wayland-specific issues

Fonts, images, MPV output, etc are blurrier than x11. How blurrier they are varies from slight to feeling as if I suddenly had vision loss.

In Wayland fonts are blurrier when you use fractional scaling as well as images that are scaled up or scaled down, and it can be very annoying to use a Wayland desktop for this reason alone. [Thankfully a fix is being worked on and so in the near future this should not be a problem.](https://gitlab.freedesktop.org/wlroots/wlroots/-/issues/3991)

Gaming is really bad on Wayland with fractional scaling because of Xwayland. Whether it's a Linux-native game or a Windows game running on WINE, it will use Xwayland. This x11-Wayland interoperability does not properly support fractional scaling, and so everything is blurry and upscaled to your screen, essentially rendered at a lower resolution. The only way to fix this is to set your compositor's display scale to 1x while you play games so that they are rendered at up to your native resolution.

Some applications have bugs on Wayland, such as GIMP not setting the canvas scale properly (2560x1600 image on 2560x1600 display appearing bigger than the display itself on 100% scaling). This is probably also caused by fractional scaling.

My screen has a slight yellowish tint, and so I use xcalib on x11 to fix it and make white look like pure white. Xcalib is not supported on Wayland and there is no Wayland-native replacement of it.

Despite all the kinds of configurations I did and XDG portals I installed, screen sharing and screen recording did not work on any of the compositors I tried.

# Xfce-specific issues

I mentioned multiple times that in order to intergrate Xfce's functionalities properly you need to launch Xfce-session, but this session also causes its own set of bugs, such as GIMP not rendering any icons or xfdesktop breaking keyboard and mouse or failing to set the wallpaper.

Xfce panel has its fair share of issues. Some of the menus don't close if you click away, transparency isn't rendered correctly, workspaces menu only worked with Labwc, etc.

Application window buttons in the panel show all the applications across all workspaces

# Conclusion

Wayland has made significant progress over these last years, but it's not ready yet for daily driving unless maybe if you use KDE or Gnome. Wayland compositors have advantages over x11 window managers but their negatives significantly outweigh the positives right now.

## Wayland pros
* Better multi monitor support
* Simpler configuration that is more centralized around the compositor
* Ability to set mouse scrolling speed
* Lower CPU usage in idle compared to xorg, giving room for lower battery usage as well (but this might not end up true because of fractional scaling overhead)

## Wayland cons
* Unless if using KDE or Gnome, Wayland requires a lot of troubleshooting, fixing, experimentation and software replacement
* Fractional scaling isn't perfect, fonts and sometimes images and video output are notably blurrier than on x11 desktops. A fix for this is currently being worked on
* Xwayland is horrible when you use fractional scaling, making gaming less convenient (requires setting fractional scaling to 1x)
* Applications like GIMP still have annoying bugs
* Lower availability of window managers and desktop environment software (panels, background software, etc). This is especially true for stacking window managers since all the hype is on tiling
* No xcalib alternative that works on Wayland or at least a software tool that can adjust both brightness and gamma of the RGB channels individually.
* Experience varies between compositors because of the fragmentation of features and implementations
* Screensharing and screen recording are still really bad. It's a miracle if it even works and even then it relies on Pipewire
