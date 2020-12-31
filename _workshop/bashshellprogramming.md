---
layout: post
title: Intermediate Bash Shell Scripting
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 21 December 2020
---
|**Audience**       | All                                                                           |
|------------------ |-------------------------------------------------------------------------------|                 
|**Prerequisites**  | [Basic Linux Commands](https://gcrnet.github.io/workshop/basiclinuxshell.html)|
|**Duration**       | 2 hour workshop (~2 hours of trainer-led time)                                |

## Description

This workshop is planned to last for 2 hours. It is a live coding
workshop and participants are expected to practise along
with the instructor. Lessons will focus on using the command-line
text editor, Vim, to create and edit files, utilizing for-loops for
automation, using variables to store information, and writing scripts
to perform a series of commands in a sequential order.

## Learning Objectives

* Learning basic operations using the Vim text editor
* Capturing previous commands into a script to re-run with one single command
* Understanding variables and storing information
* Learning how to use variables to operate on multiple files

This workshop is designed on the model developed by the [Software and Data
Carpentry](https://carpentries.org/workshops/). The material on this page is
part from the [Software Carpentry Lessons](https://software-carpentry.org/lessons/)


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
enough foundation for a personal exploration of the Bash shell programing. 
The workshop is structured as follows:

1. [Introducing the Shell](#TheShell)
2. [Navigating Files and Directories](#FilesDirectories)
3. [Pipes and Filters](#PipesFilters)
4. [Finding Things](#FindThings)

<a name="TheShell"></a>
## Introducing the Shell    

<a name="FilesDirectories"></a>
## Navigating Files and Directories

<a name="PipesFilters"></a>
## Pipes and Filters

<a name="FindThings"></a>
## Finding Things
