---
layout: post
title: Basic Linux Commands
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 31 August 2020
---
## Introduction
Linux commands are issued to a computer program called
`shell`. The shell enables us to send commands to the
computer and receive output. It is also referred to as
the terminal or command line interface~(CLI). Some
computers include a default Unix Shell program. If not
natively present, a program called Linux/Unix emulator
can be installed to access a Unix Shell on a server.

In addition, the command line is often the easiest way to interact
with remote machines and supercomputers. **Familiarity with the shell
is near essential to run a variety of specialized tools and resources
including high-performance computing systems**. As clusters and cloud
computing systems become more popular for scientific data crunching,
being able to interact with the shell is becoming a necessary skill.
We can build on the command-line skills covered here to tackle a wide
range of scientific questions and computational challenges.


## Setup
Download [data-shell.zip](http://swcarpentry.github.io/
shell-novice/data/data-shell.zip) and move the file to
your Desktop. Unzip/extract the file. You should have a
new folder called `data-shell` on your Desktop.
Open a terminal. If you’re not sure how to open a
terminal in your operating system, see the instructions
below. In the terminal type `cd` then press the 'Return'
key. This step will make sure you start with your home
folder as your working directory. Later on, you will
find out how to access the data files in this folder.

### [Windows](#tab/windows)
Computers with Windows operating systems~(OS) older than
Windows 10 do not have the Bash shell installed by default.
If you have a Windows OS older than Windows 10, we encourage
you to use an emulator included in Git for Windows, which
gives you access to both Bash shell commands and Git. Once
installed, you can open a terminal by running the program Git
Bash from the Windows start menu.

Additionally, you can run Bash commands from a remote
computer or server that already has a Unix Shell. This
can usually be done through a Secure Shell (SSH) client.
One such client available for free for Windows computers
is PuTTY. See the **reference** below for information on
installing and using PuTTY, using the Windows 10 command-line
tool, or installing and using a Unix/Linux emulator.

**Reference**
  * [Git for Windows](https://gitforwindows.org/) - Recommended           

**For advanced users, you may choose one of the following alternatives**:                 
  * [Install the Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
  * [Using a Unix/Linux emulator (Cygwin) or Secure Shell (SSH) client (Putty)](http://faculty.smu.edu/reynolds/unixtut/windows.html)      
Please note that commands in the Windows Subsystem for Linux or Cygwin may differ slightly from those shown in the lesson or presented in the workshop.

### [macOS](#tab/macOS)
For a Mac computer running macOS Mojave or earlier
releases, the default Unix Shell is Bash. For a Mac
computer running macOS Catalina or later releases,
the default Unix Shell is `Zsh`. Your default shell is
available via the Terminal program within your Utilities
folder. To open Terminal, try one or both of the following:
  * In Finder, select the Go menu, then select Utilities. Locate Terminal in the Utilities folder and open it.
  * Use the Mac `Spotlight` computer search function. Search for: `Terminal` and press `Return`.

To check if your machine is set up to use something other than Bash, type `echo $SHELL` in your terminal
window.
           
If your machine uses something other than Bash, you can run it by opening a terminal and typing
`bash`.

  * [How to Use Terminal on a Mac](http://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/)

### [Linux](#tab/Linux)
The default Unix Shell for Linux operating systems is
usually Bash. On most versions of Linux, it is accessible
by running the [Gnome Terminal](https://help.gnome.org/users/gnome-terminal/stable/)
or [KDE Konsole](https://konsole.kde.org/) or [xterm](https://en.wikipedia.org/wiki/Xterm),
which can be found via the applications menu or the
search bar. If your machine is set up to use something
other than Bash, you can run it by opening a terminal
and typing bash.        

This workshop will not make you an expert but will provide you with a good
enough foundation for a personal exploration the Unix shell. The shell has
a very rich echo system of commands but we will only touch on those deemed
essential for scientific computing. The lesson is structured as follows:

1. [Introducing the Shell](#TheShell)
2. [Navigating Files and Directories](#FilesDirectories)
3. [Pipes and Filters](#PipesFilters)
4. [Finding Things](#FindThings)

<a name="TheShell"></a>
## Introducing the Shell    
Using the shell will take some effort and some time to learn.
While a GUI presents you with choices to select, CLI choices
are not automatically presented to you. Unlike a spoken language,
a small number of “words” (i.e. commands) gets you a long way,
and we’ll cover those essential few today.

The grammar of a shell allows you to combine existing tools into
powerful pipelines and handle large volumes of data automatically.
Sequences of commands can be written into a script, improving the
reproducibility of workflows.

When the shell is first opened, you are presented with a prompt,
indicating that the shell is waiting for input.
```
Bash
$  
```
The shell typically uses `$` as the prompt, but may use a different symbol.
So let’s try our first command, `ls` which is short for listing. This command
will list the contents of the current directory:

```
Bash
$ ls  
```
```
Output

$ Desktop   Downloads  Movies  Pictures
  Document  Library    Music   Public   
```

*If the shell can't find a program whose name is the command typed, it will print an error message such as:
```
Bash
$ ks  
```
```
Output

$ ks: command not found
```
This might happen if the command was mis-typed or if the program corresponding to that command is not installed.

**ATypical Problem**
A marine biologist, has just returned from a six-month survey of the [North Pacific Gyre](https://en.wikipedia.org/wiki/North_Pacific_Gyre), where she has been sampling gelatinous marine life in the [Great Pacific Garbage Patch](https://en.wikipedia.org/wiki/Great_Pacific_garbage_patch). She has *1520* samples that she’s run through an assay machine to
measure the relative abundance of 300 proteins. She needs to run these 1520 files through an imaginary program called
`goostats` she inherited. On top of this huge task, she has to write up results by the end of the month so her paper
can appear in a special issue of `Aquatic Goo Letters`.

The bad news is that if she has to run `goostats` by hand using a GUI, she’ll have to select and open a file 1520
times. If `goostats` takes 30 seconds to run each file, the whole process will take more than 12 hours of the
scientist’s attention. With the shell, she can instead assign her computer this mundane task while she focuses her
attention on writing her paper.

The next few lessons will explore the ways the task can be achieved. More specifically, they explain how command
shell can be used to run the `goostats` program, using loops to automate the repetitive steps of entering file names,
so that her computer can work while she writes her paper.

As a bonus, once the processing pipeline has been put together, it can be used again whenever more data is collected.


<a name="FilesDirectories"></a>
## Navigating Files and Directories
<a name="PipesFilters"></a>
## Pipes and Filters

<a name="FindThings"></a>
## Finding Things