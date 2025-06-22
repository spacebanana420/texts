# My experience with Wayland (2025)

I have always been a hardcore x11 user, stubbornly refusing to switch to Wayland due to its immaturity when what I use "just works", but recently I got curious to try 3 different Wayland setups to see if I'm ready for the switch yet.

## My setup

I tried 3 different Wayland environments: Hyprland, Wayfire and Labwc. In all of the compositors I used the Xfce suite (xfce4-session or xfdesktop and xfce4-panel). All the tests were done on Alpine Linux (edge repository) on an AMD iGPU (780M) with a laptop screen of 2560x1600@120Hz. For all of these desktops I used fractional scaling ranging between 1.6x and 1.7x.

# Hyprland + Xfce

Hyprland was the first compositor I used. I was very attracted to the idea of using Hyprland because of its wiki as well as Vaxry's effort to making Wayland better.

Hyperland works great and is highly configurable, but it's the desktop that interoperates the least with Xfce components sadly. On start, I launch xfce-session which as consequence launches the whole of Xfce except for Xfwm, including not only the panel and wallpaper but also display settings, Dbus configurations (for leaving session) and detection of other disk devices on Thunar. The alternative would be to independently launch xfce4-panel, xfdesktop and a script I made to run pipewire on non-systemd distros.

Xfdesktop provides wallpaper functionality but sometimes breaks keyboard and mouse functionality on Hyprland for some reason.

Xfce panel's workspaces menu does not detect Hyprland's workspaces.

Fonts in Hyprland are a bit blurrier than compared to x11 but they seem to be the sharpest of the 3 compositors I used.

# Labwc + Xfce

Labwc is a minimal compositor inspired by Openbox. I decided to try out this compositor because it's the default choice for experimental Wayland Xfce and it's focus on correctness is attractive.

Starting Xfce Wayland session with Labwc makes it so the keyboard layout is always reset to default (US), and so it's better to run Labwc directly first and add Xfce components to the autostart file.

Just like in Hyprland, you need to run xfce-session so that Xfce is integrated properly, but if that's not a concern you have then you can run the components manually. Launching my pipewire script works unlike on Hyprland, but Xfdesktop does not work at all, leaving the background as a black screen. Other wallpaper tools like wpaperd work, but they will not work in autostart if xfdesktop or xfce4-session are also in autostart.

Fonts are slightly blurrier than in Hyprland as well as a few images and MPV's output when in windowed mode. The text on window title bars can become notably blurrier than the rest.

Unlike Hyprland and Wayfire, Labwc seems to have no way to configure your display's settings, instead you are supposed to run a wlr-randr command from the autostart file. If xfce4-session is executed, Labwc inherits Xfce's display settings however.

Labwc is the least intuitive desktop of the 3 to configure because of the XML syntax of the configuration file, but after a few minutes of reading, experimenting and using a default config as example you figure it out.

Xfce's workspaces menu somehow autodetects and interacts with Labwc's own workspaces and that's great. This doesn't happen on the other compositors.


# Wayfire + Xfce

Wayfire is a very quirky compositor because of all the animations and plugins it has. The default configuration has many things I don't like such as wobbly windows, but it doesn't take long to disable them.

Wayfire works the best with Xfce components compared to the other compositors I tried and the experience overall is pleasant when it comes to integrating all these components together.

Fonts, images, MPV output, etc are slightly blurrier than Labwc and Hyprland and it does feel as if I suddenly had vision loss. It's unpleasant and makes me require that I use a higher display scale (1.7x) rather than the 1.6x I used in Hyprland. The moment I go back to x11 everything is suddenly notably sharper and that's a shame really.

Configuration is very good and decently extensive, I took a liking to merely setting up Wayfire.

Strangely enough, some GTK applications apply the GTK theme on the title bar, while other applications use Wayfire's theme.

# Wayland-specific issues

Like mentioned multiple times above, in Wayland fonts are blurrier at least when you use fractional scaling, and it can be very annoying to use a Wayland desktop for this reason alone. At first it also seemed that taking screenshots in Wayland also results in blurrier images (tested with Grim) but when viewing the same images on x11 they seem to be just fine, so it's probably a problem with GIMP and ristretto on Wayland.

Gaming is abysmally bad on Wayland with fractional scaling. Whether it's a Linux-native game or a Windows game running on WINE, it will use Xwayland. This x11-Wayland interoperability does not properly support fractional scaling, and so everything is blurry and upscaled to your screen, essentially rendered at a lower resolution. Some games don't even start with Xwayland.

Some applications have bugs on Wayland, such as GIMP not setting the canvas scale properly (2560x1600 image on 2560x1600 display appearing bigger than the display itself on 100% scaling).

My screen has a slight yellowish tint, and so I use xcalib on x11 to fix it and make white look like pure white. Xcalib is not supported on Wayland and there is no Wayland-native replacement of it.

Despite all the kinds of configurations I did and xdg portals I installed, screen sharing and screen recording did not work on any of the compositors I tried.

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
* Lower CPU usage in idle compared to xorg (theoretically)

## Wayland cons
* Unless if using KDE or Gnome, Wayland requires a lot of troubleshooting, fixing, experimentation and software replacement
* Fractional scaling isn't perfect, fonts and sometimes images and video output are notably blurrier than on x11 desktops, ranging from slightly uncomfortable to emulating the sensation of having bad eyesight
* Xwayland is horrible when you use fractional scaling, making gaming absolutely not feasible
* Applications like GIMP still have annoying bugs
* Lower availability of window managers and desktop environment software (panels, background software, etc). This is especially true for stacking window managers since all the hype is on tiling
* No xcalib alternative that works on Wayland or at least a software tool that can adjust brightness and gamma of the RGB channels individually.
* Experience varies significantly between compositors because of the fragmentation of features and implementations
* Screensharing and screen recording are still really bad. It's a miracle if it even works and even then it relies on Pipewire
