# The Advantages of CLI over GUI
There are plenty of programs that have all kinds of interfaces, from command-line to terminal text interfaces to graphical interfaces.
Many people on Windows/Mac-like environments end up using mostly graphical interfaces, but a deep power and efficiency surges when we primarily work inside a terminal.

Many people on UNIX-like systems end up adopting a majority of CLI software, and it is not by chance or based on outdated principles, but a timeless efficiency and productivity.

## Acronyms
* **CLI**: command-line interface (example: cp, mv, cat, grep, ffmpeg, apt, magick)
* **TUI**: terminal user interface (example: cfdisk, ranger, ncdu)
* **GUI**: graphical user interface (example: GIMP, Blender, Firefox, Chrome, VLC)

## Performance and resource usage
CLI programs have lower overhead in their interface.
This means that a command-line or terminal-based interface uses fewer CPU and RAM to function, compared to a modern graphical interface.

This is natural, as a CLI or TUI interface has fewer things going on for the final program to render.
A command-line interface has 0 rendering whatsoever, relying solely on executing a program and passing arguments, while a TUI application has an interface entirely made of text.
A graphical interface has to worry about graphical rendering as well as deeper and more complex interface elements.

## Portability
CLI and TUI interfaces are extremely portable, this means that they are much easier to port to other platforms.

Graphical interfaces have to worry about extremely platform-specific implementations.
You need an implementation for Windows, another one for MacOS, another one for X11, another one for Wayland, and the list goes on.
If you have to write a graphical library from scratch, the effort to implement for all kinds of platforms and have a unified look and behaviour is enormous.

Most people who make GUI applications rely on large libraries/frameworks such as GTK and QT, but then you are bound to their overhead/bloat or design choices.

## Efficiency
Many tasks require less time, effort and key presses (or mouse presses for GUI) if they are done on a properly-made CLI program.
Of course that there are many workflows where GUI is better, especially image manipulation and drawing, 3D, video and audio editing, web browsing, media players, etc, but the rest tends to be better off in a TUI or CLI.

## Automation and composition
CLI programs can be composed alongside others.
You can write a single command that executes multiple programs where one complements each other, and you can do the same with shell scripts or your very program.
Suddenly a task that would require opening graphical applications, wait for them to load and click on many buttons now can be automated to a single command, a script or a program.

Standard input and output appear as an interface for the terminal to read user prompts and print text to the screen, but in their raw nature they are simply reserved places in memory for programs to read and write byte streams.
Software can be programmed to expect certain raw bytes or text to be written into its standard input, or produce relevant data to standard output.
An example of this is `cat | grep` where cat prints the text contents of a file (writes bytes to standard output) and then grep will have those bytes be written into its standard input.
This way, cat and grep transfer data to each other, they talk with each other.

## Text as universal format
Standard input/output/error and CLI arguments are very low-level in operating system userspace.
In their raw form, they are byte streams or chunks, but most often they are used for text data.

Text is the universal communication format: any person, text-aware application (such as cat, grep or a text editor), scripting or programming language can read and write text.
You no longer are bound to specific ABIs, API specifications, programming languages or policies.
You dictate your tools, languages and environment.
This idea is part of the UNIX operating system philosophy.

## Debugging and troubleshooting
All programs can print to standard output/error, but CLI programs tend to do it more.
Many programs use standard output/error as a place for sending logs, messages, warnings and errors.
This makes program behaviour and issues much more transparent and easier to solve or at least understand and pinpoint the cause.

## Freedom to do it yourself
Due to the positive traits I mentioned above (text communication, composition and automation, portability, etc), a software workflow made of CLI tools makes it much easier to do things yourself.
You are not bound to a single unreplaceable gigantic graphical application that does everything, you can compose and automate CLI tools together.
Because of this, you can choose your components, your tools, and replace them. You can make your own and have them integrate with the others or make use of them.

Freedom to do things your way becomes easier.

## You can mix both
There are some cases where a graphical application could be more efficient or practical to use if you define what it's meant to do or configure it straight from the command-line.
Some examples like this exist, one of the best examples is MPV.

MPV is a media player, and yet extremely CLI-friendly.
Despite being a graphical application (or not, optionally), all of its options are exposed as CLI arguments or config file options.
This CLI implementation makes it extremely straightforward to configure MPV and have it behave uniquely for each context.

You might have the general options you use for playing video and audio, but you might also prefer to use MPV for viewing images.
You can associate image file formats with a custom MPV command that has the right arguments for properly viewing images (for example: have MPV not close instantly after opening the image) without \
