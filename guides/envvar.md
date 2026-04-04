# Environment Variables on Linux

Environment variables are a widespread concept in operating systems that allows for a more convenient alternative to change software behaviour without adding more command-line arguments during execution. These variables can be passed during process execution or defined during the lifetime of a program or the entire operating system. Environment variables are more common in people's workflows and troubleshooting on UNIX-like systems.

## How an environment variable works

Environment variables are a userspace concept, meaning that they do not exist at the kernel level. A variable has a name, which is used to identify it, a then a value which can represent anything but is always stored as text, as a string. When a program is launched with a set of environment variables, any other program it launches will also have those variables assigned.

Instead of having to always pass command-line arguments to programs when you want a specific behavior or configuration to persist, you can instead use environment variables and have the programs check for them.

## How environment variables are implemented in Linux

On Linux, many of your system's environment variables are assigned when you log-in, usually in `/etc/environment` and `/etc/profile`. PAM authentication (used in log-in methods) reads from the environment file, while log-in shells (TTY login) read from the profile file. When logging into a graphical session (session files from `/usr/share/wayland-sessions/` and `/usr/share/xsessions/`), variables might also be defined depending on what the session file runs. Each desktop environment or window manager might also have its own set of variables it defines which you can configure. A script might also assign variables.

Environment variables propagate throughout the system, since a program with a set of variables passes them on to the programs it executes. Shells and graphical environments are used to launch other programs, and so by having your log-in shell or graphical environment contain certain variables, you essentially configured the entire operating system to use them.

Shells also check for even more variables every time you open them, by reading their rc files (for example: `~/.bashrc` for Bash).


## How to set an environment variable temporarily

* You can set a temporary variable for running a single command that then disappears
  * e.g. `WINEPREFIX=/path/to/customprefix wine game.exe`
* Use `export` command provided by your shell to define a variable throughout the lifespan of that shell, for all commands you run on it
  * `export WINEPREFIX=/path/to/customprefix`
  
These methods work both for running commands as well as for writing your scripts, since environment variables work as normal variables in shell scripts.
  
## How to set an environment variable permanently

* Add your variable in `/etc/environment`, it will be assigned during log-in
* Add your variable in `/etc/profile`, it will be assigned when running a log-in shell (TTY)
* Add your variable to an *rc file, such as `~/.bashrc` for Bash, it will be set every time you open that shell
* Configure your window manager/desktop environment's variables, they are then passed on to all programs they run
* Change your session file (`/usr/share/wayland-sessions/` and `/usr/share/xsessions/`) so that it also sets variables by running a custom script

There are other ways you can set environment variables or even run shell code on startup, but these are a few examples.

## Checking for environment variables

* Run `env` command to see all variables
  * You can filter by name by piping into grep: `env | grep SHELL`
* You can also use "printenv": `printenv SHELL`
* If you already know the name of the variable, you can echo it: `echo $SHELL`
