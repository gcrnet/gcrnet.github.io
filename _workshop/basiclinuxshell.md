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

**A Typical Problem**        
A marine biologist, has just returned from a six-month survey of the [North Pacific Gyre](https://en.wikipedia.org/wiki/North_Pacific_Gyre), where she has been sampling gelatinous marine life in the [Great Pacific Garbage Patch](https://en.wikipedia.org/wiki/Great_Pacific_garbage_patch). She has *1520* samples that she’s run through an assay machine to
measure the relative abundance of *300* proteins. She needs to run these 1520 files through an imaginary program called
`goostats` she inherited. On top of this huge task, she has to write up results by the end of the month so her paper
can appear in a special issue of `Aquatic Goo Letters`.

The bad news is that if she has to run `goostats` by hand using a GUI, she’ll have to select and open a file *1520*
times. If `goostats` takes *30* seconds to run each file, the whole process will take more than *12* hours of the
scientist’s attention. With the shell, she can instead assign her computer this mundane task while she focuses her
attention on writing her paper.

The next few lessons will explore the ways the task can be achieved. More specifically, they explain how command
shell can be used to run the `goostats` program, using loops to automate the repetitive steps of entering file names,
so that her computer can work while she writes her paper.

As a bonus, once the processing pipeline has been put together, it can be used again whenever more data is collected.


<a name="FilesDirectories"></a>
## Navigating Files and Directories

The part of the operating system responsible for managing files and directories is called the **file system**.
It is organized in multiple layers. The top most layer is the root directory. When you remotely login to a
computer for the first time, you get on the home directory. Every user account on a server (High Performance Computer)
has a home directory.
![Examples of a file system](https://i.imgur.com/rumMGhTl.jpg)

The forward slash character `/` does two things:
  * When it appears at the front of a file or directory name, it refers to the root directory.
  * When it appears inside a path, it’s just a separator.

The root directory `/` has `/bin`, `/data`, `/Users`, and `/tmp` directories. The `/Users` directory in turn
has the `/Users/Sarah`, `/Users/Jacob` and `/Users/Nelle` directories. The path from the root directory
to any targeted file or directory is called the **absolute path**. `/Users/Sarah`, `/Users/Jacob` and `/Users/Nelle`
are the abasolute paths to Sarah's, Jacob's, and Nelle's home directories.

Download the `data-shell.zip` from the setup section on to your destop. Start the terminal on your computer.

Use the command below to determine your home directory
```
Bash
$ echo $HOME  
```
```
Output
$ /Users/Jacob
```
Determine your current working directory (data-shell)
```
Bash
$ pwd  
```
```
Output
$ /Users/Jacob/Desktop/data-shell
```
List the content of your current working directory with `ls`
```
Bash
$ ls
```
```
Output
$ creatures          molecules          notes.txt           solar.pdf
  data               north-pacific-gyre pizza.cfg           writing
```
`ls` prints the names of the files and directories in the current directory. We can make its output more
comprehensible by using the *-F* option (also known as a switch or a flag) , which tells `ls` to classify
the output by adding a marker to file and directory names to indicate what they are:    
  * a trailing / indicates that this is a directory
  * @ indicates a link
  * \* indicates an executable        

Depending on your default options, the shell might also use colors to indicate whether each entry is a file
or directory.     
```
Bash
$ ls -F 
```
```
Output
$ creatures/          molecules/          notes.txt           solar.pdf
  data/               north-pacific-gyre/ pizza.cfg           writing/
```
### Syntax of a shell command
Consider a general example of a command, which we will dissect into its component parts: 
```
Bash
$ ls -F /
```
```
Output
Applications/ System/       bin/          etc@          private/      usr/
Library/      Users/        cores/        home@         sbin/         var@
Network@      Volumes/      dev/          opt/          tmp@
```

`ls` is the command, with an option `-F` and an argument `/`.  We’ve already encountered options
(also called switches or flags) which either start with a single dash (-) or two dashes (--), and
they change the behaviour of a command. Arguments tell the command what to operate on (e.g. files and directories).
Sometimes options and arguments are referred to as parameters. A command can be called with more than one option
and more than one argument, but doesn’t always require an argument or an option.

Each part is separated by spaces: if you omit the space between `ls` and `-F` the shell will look for a command
called `ls-F`, which doesn’t exist. Also, capitalization can be important. For example, `ls -s` will display the
size of files and directories alongside the names, while `ls -S` will sort the files and directories by size, as
shown below:

```
Bash
$ ls -s /Users/Jacob/Desktop/data-shell/data/
total 208
  8 amino-acids.txt    0 elements/         24 planets.txt
  0 animal-counts/     8 morse.txt          8 salmon.txt
  8 animals.txt        0 pdb/             152 sunspot.txt
```
and
```
Bash
$ ls -S /Users/Jacob/Desktop/data-shell/data/
sunspot.txt      elements/        morse.txt        animals.txt      salmon.txt
planets.txt      pdb/             amino-acids.txt  animal-counts/

```
### Getting Help
There are two common ways to find out how to use a command and what options it accepts:
  1. We can pass a` --help` option to the command, such as
  ```
  Bash
  $ ls --help
  ```
  ```
  Output
  ls: illegal option -- -
  usage: ls [-@ABCFGHLOPRSTUWabcdefghiklmnopqrstuwx1%] [file ...]
  ```
 2. We can read its manual with `man`, such as
  ```
  Bash
  $ man ls
  ```   
  ```  
  Output     
   LS(1)                     BSD General Commands Manual                    LS(1)
   NAME
      ls -- list directory contents
   SYNOPSIS
      ls [-ABCFGHLOPRSTUW@abcdefghiklmnopqrstuwx1%] [file ...]
   DESCRIPTION
      For each operand that names a file of a type other than directory, ls displays
      its name as well as any requested, associated information.  For each operand that
      names a file of type directory, ls displays the names of files contained within
      that directory, as well as any requested, associated information.
    
      If no operands are given, the contents of the current directory are displayed.
      If more than one operand is given, non-directory operands are displayed first;
      directory and non-directory operands are sorted separately and in lexicographical
      order.

      The following options are available:

      -@      Display extended attribute keys and sizes in long (-l) output.
   :
  ```
  
Continue to push on the space bar of your computer to scroll down the `ls` manual.
Sometimes at the bottom of the manual, you see some examples of how to use the command.
Push the `q` key to exit the `man` page.

If you try to use an option (flag) that is not supported, `ls` and other commands will usually print
an error message similar to:

```
Bash
$ ls -j
```
```
Output
ls: illegal option -- j
usage: ls [-@ABCFGHLOPRSTUWabcdefghiklmnopqrstuwx1%] [file ...]
```

### Exploring Directories

We can look at the content of `data-shell` by passing the directory name to ls
```
Bash
$ ls -F /Users/Jacob/data-shell
```
```
Output
creatures/          molecules/          notes.txt           solar.pdf
data/               north-pacific-gyre/ pizza.cfg           writing/
```
We can use the *change directory* `cd` command to move from one directory to another.
This is akin to double clicking on a directory in a GUI environment. The command below
moves from `data-shell` directory to its subdirectory `data`.
```
Bash
$ cd data
```
Use `pwd` command to confirm your location
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell/data

```
So far, 'cd' only sees sub-directories inside your current directory. There are different
ways to see directories above your current location. This is done using a shortcut in the
shell to move up one directory level that looks like this:

```
Bash
$ cd ..
```
`pwd` can then be used to verify our location

```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell

```
We can see that `cd ..` takes us back to `data-shell` directory.
`..` is a special directory that is always present in all directories. To see
this special directory and other hidden files in a directory, we add `-a` option to the
`ls` command.
```
Bash
$ ls -a -F
```
```
Output
./                  creatures/          north-pacific-gyre/ solar.pdf
../                 data/               notes.txt           writing/
.bash_profile       molecules/          pizza.cfg
```
`-a` stands for ‘show all’. It forces `ls` to show us file and directory names that begin with `.`,
such as `..` (which, if we’re in /Users/Jacob, refers to the /Users directory) As you can see,
it also displays another special directory that’s just called `.`, which means 'the current working directory'. 

**Note that** in most command line tools, multiple options can be combined with a single `-` and no
spaces between the options, `ls -F -a` is equivalent to `ls -Fa`.

**Important Shortcuts**   
`~` (tilde) at the start of a path means “the current user’s home directory”. For example, if Jacob’s
home directory is /Users/Jacob, then `~/Deskstop/data-shell/data` is equivalent to
`/Users/Jacob/Desktop/data-shell/data`. *This only works if `~` is the first character in the path*

`-` (dash) character istranslated by `cd` to mean *previous directory* I was in, which is faster than
having to remember, then type, the full path. This is a very efficient way of moving back and forth
between directories.

**Note that** `cd ..` takes you up, one level while `cd -` takes you back where you were previousely.
You can think of it as the Last channel button on a TV remote.

### Absolute and Relative Paths
An *absolute path* is defined as specifying the location of a file or directory from the root directory(/).
`/Users/Jacob/Desktop/data-shell/data` is the absolute path to the `data` directory. Use `cd` only or `cd ~`
to go back to your home directory. From your home directory, go back to the `data` directory using its absolute
path
```
Bash
$ cd
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/
```
```
Bash
$ cd /Users/Jacob/Desktop/data-shell/data
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell/data
```
*Relative path* is defined as the path related to the present working directly(pwd).
Use the *relative path* to get to the `Desktop` directory and back to the data directory
```
Bash
$ cd ../..
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop
```
Now go back to the `data` directory
```
Bash
$ cd data-shell/data
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell/data
```
The relative path from `data` to `Desktop` directory is `../..` and the relative path
back to `data` from `Desktop` directory is `data-shell/data`.

<a name="PipesFilters"></a>
## Pipes and Filters

<a name="FindThings"></a>
## Finding Things