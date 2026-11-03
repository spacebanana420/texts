# IDE vs code editor: monolith vs modular

IDE popularity raised significantly decades ago when it introduced and centralised features that smaller code editors did not have. People started adopting all kinds of IDEs from IntelliJ to Eclipse and others. Does this mean that code editors are irrelevant? Absolutely not, otherwise there wouldn't have been an increasing desire for younger people to use tools like Vim, Emacs, VScode and other less-known editors such as Micro and Helix.

IDEs became popular exactly because of how many features they centralised in a closed environment, but these features (or most of them) already existed in the form of separate programs. It comes to the difference between 2 types of environments: monolithic or modular.

### Monolithic (IDE environment)
All or most development happens inside the editor. This results in a very enclosed workflow and suits specific environments extremely well, for example, IntelliJ for Java projects using Maven or Gradle. IDEs have extensive built-in autocompletion and static analysis, build tool integration and debuggers, but this tooling might not work well if used in a project that does things different than usual. Once you shift away from the norm, things might not work exactly the way they should.

### Modular (Code editor + CLI tools)
The original and still prevailing environment for UNIX fans. This setup follows the "each program does one job and well" idea. The code editor is only used for code editing, and external functionality belongs to external tools. Modularity allows you to define your environment your way, modify it easier and replace the components you need or want to replace. It comes at higher friction and longer planning on designing your workflow than an IDE but it provides efficiency and freedom once set up.

### My stance
I am extremely in favor of the modular approach, where I use a smaller code editor for programming, while using external tools (git, compiler, file management, scripts, piping, etc) for the rest. This allows me to dictate my environment my own way and it will always work regardless of the computer or POSIX-compatible OS I use. I also have lower memory and CPU usage and I do not have to bother disabling features I don't care about to make an IDE more tolerable. LSP programs are also a great example of a software that standardized the idea of "IDE autocompletion but can be used from any code editor" exactly because they follow the modularity principle.

### People's stances on the professional field
Milage may vary, but the majority of people seem to use VScode nowadays, regardless of who they work for or what they do. I consider VScode one of the universal code editors because of its extensive language support and plugin repository.

People working at bigger companies tend to use more enclosed environments, either because they want to (IDE) or because it's forced by the company (Windows+WSL rather than bare metal Linux). The opposite tends to be true for smaller companies. Overall, your team appreciates if you know how to use the tools they use, just in case there's a necessity for everyone to be on the same page. If they all use IntelliJ that's fine, you can choose to use it or to use maybe VScode or even Vim, but if you do not use their tools you should be prepared to be able to set it up yourself without any help from them. People are flexible overall.

### Comfortable middle-term?
Despite my stance, I used to use IntelliJ however in an abnormal way. I would disable most features, disable static analysis almost entirely and still perform many actions outside the IDE, such as using the git CLI. This worked well and I could still leverage the nice extras of an IDE that actually matter to me, but the bloat was still a bit high and my future-proofing was worse since IntelliJ is not as OS-agnostic as something like Emacs or VScode.
