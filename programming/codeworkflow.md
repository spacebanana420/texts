# My programming workflow (as of early 2026)

As mentioned in my [IDE vs code editor](codeeditors.md) document, I am extremely in-favor of modular setups where each tool does its job. I like efficiency, minimalism and I like being able to do things my own way without being met with friction, but then at the same time I also like a nice plugin and theme repository.

### TLDR
I like to use mostly-vanilla Emacs with a file tree, but I navigate a lot of files directly from my desktop's file explorer (currently Thunar). If the file explorer is keyboard-friendly and fast, many times it's easier to manage files directly from it rather than using a code editor file tree. I like to use multiple terminal windows, and I'm not opposed to the idea of multiple code editor instances each with 1 file open.

### Multiple file editing
Code editor tabs and Emacs buffers are very useful for editing multiple files from within a single editor window. This is extremely common practice nowadays, but it opposes the typical Vim workflow of having one entire window per file. Vim is very good at this because of how fast and lightweight it is, while opening 1 IDE for each file you want to edit would be very slow and bloat up your RAM instantly. Emacs is very flexible in this, it can either go one way or the other, but I usually only have 1 Emacs window open.

### File navigation
File trees built into your code editor or IDE are extremely useful, but sometimes I simply prefer to use my own desktop file explorer. If the file explorer is fast and lightweight and you can navigate easily only using your keyboard, then many times it's easier to get something done from it than if you had to use the code editor file tree. This workflow also detaches file operations from the code editor, one less thing to worry about when you want to select a new editor.

### Scripting, piping and terminals
Sometimes you have to go your own way, and make your scripts (or even whole programs) for building your projects or satisfying specific necessities (automating a bunch of Docker commands for running an Airflow instance locally). Scripting is great, CLI can be automated, and stdin and stdout allow for interprocess communication, assembling functionality with multiple programs.

### Build tooling
Build tools are a huge pain point. They are vastly better than the equivalent built-in IDE feature because they are agnostic to all code editors and can be automated since they are CLI, but so many of them are overcomplicated and their documentation does not go straight to the point. I really do not like Maven or Gradle at all, so I made my own simple build tool. It's mostly a glorified wrapper for the Java compiler and JAR packaging tool but that's exactly why I loved making it and use it on all my projects, it simplifies the process of compiling and building Java programs while still automating and fixing the pains of using the compiler directly. And in the end, I still work closely with the barebones compiler and keep my understanding of it fresh. Makefiles and scripts are also nice alternatives.
