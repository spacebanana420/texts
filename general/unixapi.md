# UNIX Design Beauty: piping and pseudo-files

Two of the features/ideas of UNIX OS design I love the most are piping and and pseudo-files. They work as universal APIs to communicate with the kernel and subprocesses in a language-agnostic way, without requiring any language bindings to C. This ease of modularity is extremely powerful and I love leveraging it. 

### Standard I/O 
From an end-user perspective, standard input and output on a CLI program tend to be used for seeing log and error messages and prompting text, but these interfaces are extremely reliable means of one program communicating with another. They function somewhat like a TCP socket, you can write and read byte streams, allowing a program to communicate with a subprocess. On UNIX-like systems this is common sense, as many programs leverage stdio piping for extreme modularity. There are many examples of piping in the real world:

* All kinds of scripts
* FFmpeg and ImageMagick (reading images from stdin and writing images to stdout)
* Grep
* LSP programs
* Emacs
* Xclip and wl-clipboard (saving and reading clipboard data on X11/Wayland)
* And many many more

Simple, language-agnostic and modular means of communicating with a subprocess.

### Pseudo-files
Pseudo-files are incredible. These "files" are an extremely convenient way to interact with the operating system kernel and hardware on UNIX-like systems. From a user and program perspective, they look like real files you read from and write to, but in reality you are communicating with the kernel for all various kinds of instructions. These files are called pseudo-files exactly because they are not real and interacting with them does not result in disk usage or the latency and performance cost it would have caused. Their goal is to interact with the kernel and hardware to retrieve information or configure the hardware.
There are all kinds of pseudo-files in these OSes. Some let you retrieve operating system, process and hardware information, others let you control your CPU and suspend your system, others let you control your laptop battery and brightness, and there are many others with different behavior. Manipulating these pseudo-files is not something you think on a daily basis even if you use Linux or a BSD, but for programming and scripting it's extremely convenient and useful to use them if you have the usecase for them. They are also language-agnostic, since from the program's perspective it seems as it's performing file operations rather than system calls. You can then use a language such as Java or Go without requiring C bindings, since you do not need to run system calls directly.
