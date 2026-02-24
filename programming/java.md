# Java is a great and misunderstood language

Throughout the years I saw (and still see) many people on the internet criticise or even shit on Java for different kinds of reasons, so much that at first it even made feel a bit intimidated or concerned to learn Java back in 2022. Ironically, Java is now my favourite language, the absolute #1 favourite of all languages I have ever tried. With my current Java experience and my extreme preference for it, I looked back at the complaints people have and the jokes and memes people make about Java and even talked with a few people that hated using Java and I came to interesting conclusions. 

### My Java experience differs from many people's

With my desire for making self-contained tools that solve usecases I have, I originally went straight into a barebones Java setup without build tools, frameworks or LSP, eventually making my own simple build tool. My focus is on CLI and TUI applications and having as few external dependencies as possible. I simply hate when bloated software nags me. This resulted in some things that significantly made my Java experience closer to a more C/C++ barebones one:

* No Maven/Gradle: I originally wrote scripts to run `javac` and `jar` directly and eventually made my own simple build tool, which in the end is a wrapper for the JDK tooling on steroids. Maven and Gradle can feel very overwhelming and overengineered for simpler projects that do not use frameworks or automatically fetch libraries remotely and recursively.

* No frameworks (Spring, etc): Popular Java frameworks such as Spring significantly increase the complexity of your project and add performance overhead. They also make debugging and developing harder, as now you have to develop *the Spring way* and stack traces that could have been 5 lines long now are 50.

* Verbosity and boilerplate: One of the complaints people who first try Java have are about boilerplate such as having to repeatedly write the keywords "static", "public" and "private". This is not as much of an issue as it seems but I'll elaborate more on that below.

* No IDE and LSP dependency: I wrote Java in all kinds of code editors, from VSCode to Geany to Micro to Emacs to Neovim to heavier programs like Intellij IDEA. An IDE can feel very overwhelming, and can make your developer setup less transparent if you use it for everything, even compiling your program. LSP is nice, but it uses extra CPU which is bad for when my laptop is not plugged, also the best Java LSP out there only works properly for Maven/Gradle setups if I recall correctly, and so it failed to work on my projects.

* Pre-Java 8 experience: Those who worked with Java versions before 8 have a bad opinion of Java because of how it once was, regardless of how much it has evolved since then.

* Performance misconceptions: Many people consider Java to be slow because of Minecraft's performance issues, but these issues come from the game's programming itself and can be fixed with mods such as Sodium. In reality, Java is impressively fast for a virtual machine, some benchmarks show it's faster than C#. Native compilation alternatives exist such as GraalVM.

* Memory usage: This is a very valid claim, but it happens by design and comes with an important performance benefit, I will elaborate on this below.

### Explaining Java's verbosity as a positive trait

Many people, especially people who haven't used Java much or even C# or C++, complain about its verbosity for different reasons. I'll explain these different Java traits and how they reflect in reality, regardless of how people perceived them or talked about them:

#### Classes everywhere, "forced OOP"

Some people complain that in Java all your functions and variables must be inside some kind of class, whether it's a public or protected class. C# also uses the same approach, and while C and C++ do not, I think at least C++ would have been better off doing it this way.

When a class only has static functions and variables inside it, is it really a class or just a module? In reality, classes behave like modules because they are modules. When you import this class, you import its elements as well. If you import `java.nio.file.Files`,  you then can call its functions by calling the Files class, for example `Files.readAllBytes()`. This approach of treating classes like modules is good language design and entirely eliminates the need for C++ namespaces (Java equivalent would have been `java.nio.file.Files.readAllBytes()`) or importing things then not knowing where they come from (for example calling `readAllBytes()` directly).

#### Boilerplate with "public" and "static"

This one is more straightforward. If we treat classes as modules then global functions and variables are static and so they must be specified as static. It would be nice though if Java had an alternate keyword to "class" that would mean "alright, this class can only ever have static functions and variables, and so you do not have to specify that they are static" (similar feature to "Object" in Scala).

As for having to specify "public", Java and C# chose that the default privacy should be protected instead of public. Both ways have ups and downs so there's not much to say here.

#### Other kinds of verbosity

Besides the complaints above, some people say Java is too verbose. If we exclude the use of classes as modules and having to specify "public" and "static", then really Java is almost perfectly comparable to C++ and sometimes even C when it comes to verbosity. People who complain about this kind of verbosity tend to also complain about C and C++ verbosity, but this is a good feature. Verbose and transparent code can still be clean and direct, while having the advantage of being extremely transparent in what it does: what you see is what you get.


#### OOP clusterfuck, class hell, factories everywhere

This comes from a programming culture issue where people rely deeply on OOP design patterns and thick layers of abstraction, when maybe a simple function call and a for loop would have solved the issue. Depending on what Java libraries or frameworks you use, you might come across these painful implementations. Java got the blame for this due to being the most popular language people used for OOP, but Java itself is multi-paradigm and can be written in a style very close to "C with classes", otherwise I wouldn't have liked it nearly as much.


### Explaining Java memory usage

Java programs use a decent amount of memory, but not nearly as much as people expect. This memory behavior comes from optimisation choices implemented into the virtual machine and garbage collector.

#### Initial memory usage

The virtual machine itself needs approx. 40 to 60 MB of RAM to function. Someone new to Java makes a hello world program and sees the program use this much memory and thinks that it will only scale from here, but these 40-60MB are not caused by the hello world, they are for the virtual machine itself. In the end, a full Java program will not use entire gigabytes of memory, it will use significantly less as internal Java variables by themselves don't have that much overhead.


#### Memory usage increases and doesn't lower

This is a performance choice used in the garbage collector by default. When running a Java program, the variables you create and data you allocate go to an internal virtual RAM handled by the virtual machine (this is also why you can set minimum and maximum memory limits on startup, very common in Minecraft). Normally, once a variable in your program is deleted and no longer needed, the garbage collector would free this memory slot so the program can re-use it, but this act of freeing memory costs CPU time. Java handles memory in a "lazy" way to sacrifice memory efficiency for absolute CPU performance: the garbage collector keeps the unused slot occupied and doesn't bother with it, the next variable will use extra space. Only once your program starts to approach the memory limits you defined or the limits of your system's RAM, it will clear all the unused but occupied slots, then your memory will become free again. With this method, the garbage collector only spends time clearing memory when truly needed.

Even when your program frees all those memory slots, you will see that your actual real RAM is still using the same numbers, this is also intended behavior. The virtual machine allocates real RAM, and once it's allocated it keeps it that way, so that if it needs to re-allocate variables in that space as your program runs it won't have to perform extra system calls and CPU instructions that would take extra time. This also improves performance.
