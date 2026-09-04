# How Complexity is Related to Vendor Lock-in

Software complexity has raised and will continue to raise in our daily lives.
Some software is more lightweight, efficient and minimalist and we can definitely choose which to use even at the operating system level, but even in open source grounds complexity is rising.

Complexity in software can mean many things: resource usage, inefficient in its resource usage, inefficient in time and effort it takes to use, code complexity, etc.
Many people are minimalists and avoid excessive complexity or bloatware, but something that has been on my mind that usually isn't talked about is how software complexity imprisons us, more specifically it promotes vendor lock-in.

Vendor lock-in means to be stuck with certain software and ecosystems, unable to replace them or escape them.
Vendor lock-in is very common in proprietary software, because closed-source software dictates how you use your computer and what platforms the software will run on.
It can also manifest in open source software if the software itself is not flexible.

Some examples of vendor lock-in are:
* Proprietary software that is specific to an operating system (and proprietary software in general)
* Tools that only work under specific environments
* Paid remote services (for example: GitHub Copilot and Claude)
* Proprietary operating systems themselves and their software
* Corporate services like Azure, Databricks, SQLServer, BigQuery, etc
* Software projects with built steps that are tied to specific IDEs
* Complex software such as Xorg and Wayland and its compositors, web browsers and GTK and QT
* Complex, bloated and invasive software such as systemd

Notice the last examples I gave and how they mention complexity.
In programming and engineering, complexity is often a negative trait that people perceive as virtue, when true virtue is in simplicity and efficiency.

Software complexity worsens performance, portability, difficulty in scaling or adding features and difficulty in maintaining and troubleshooting code.
As software becomes more complex, portability is often affected, and less portability results in less freedom of choice in platform and tools.
Once you can't choose your tooling and system at all, you are now stuck in an equivalent situation to vendor lock-in, even if it's not intentional by the developers.

Software complexity also causes vendor lock-in for programmers.
UNIX operating system philosophy allows for direct access to mechanisms, universal text communication and process composition.
All of these traits allow for simple and practical creation of tools and automation that make up your system, which for me significantly increased my pleasure and experience in programming.

Complex software is hard to work with: using its mechanisms for practical outcome requires much more investment in effort and time:
* Web browsers need to cover so many edge cases and functionality that no one ever wants to make one from scratch, so nearly every browser in the world is just a fork of Firefox or Chromium.
* X11 is old and complex, so no one makes an X11 server from scratch (some tried with AI).
* Xorg is extremely complex and huge, with so much spaghetti code. Nearly no one can touch that thing.
* Wayland as a protocol is very complex and extremely vast. It takes tremendous effort to make a compositor, even with libraries like wl-roots.
* Other programs like DBus and PipeWire are huge, complex and poorly documented or laid out. It takes huge effort to use them.

With software complexity, suddenly what would be highly efficient and practical and would take a few lines of code to implement now takes years of effort into studying deep obscure arcane spells just to make something.
This murder of practicality and efficiency results in fewer people working in certain tools like the ones I mentioned above, which results in vendor lock-in indirectly: all of us, even programmers, now depend on extremely specific people or organisations to make these huge monsters of bloat.
Now we depend on them to make our browsers, our desktop environments and window managers, etc. We are now stuck to them and the ever-decreasing number of complex software.

Our freedom of choice or freedom to do things ourselves dies, and we now have vendor lock-in.
