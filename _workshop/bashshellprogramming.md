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

[Follow the instructions here to set up your operating system](https://gcrnet.github.io/workshop/basiclinuxshell.html#Windows)
## Contents
1. [Basic Shell Commands](#TheBasics)
2. [Introduction to Vim](#IntroVim)
3. [Shell scripts and for loops](#Shellscripts)


<a name="TheBasic"></a>
## Basic Shell Commands    

Below is a key of the basic commands you should be familiar with in order to be able to follow this module.
```
## Commands

cd            # change directory to "~" or to specified directory
ls            # list contents of current or specified directory
man <command> # display manual for specified command
pwd           # specify present working directory
echo "..."    # display content in quotes on the standard output
history       # display previous "historical" commands
cat <file>    # display all contents of a file on the standard output
less <file>   # open a buffer with the contents of a file
head <file>   # display the first 10 lines of a file
tail <file>   # display the last 10 lines of a file
cp <..> <..>  # copy files or directories
mdkir         # make a new directory/folder
mv <..> <..>  # move or rename files or directories
rm <file>     # remove a file or a folder (-r)

## Other
~             # home directory
.             # current directory
..            # parent directory
*             # wildcard
ctrl + c      # cancel current command
ctrl + a      # start of line
ctrl + e      # end of line

```
**Visit the sites below to see how bash commands are used**
* [http://explainshell.com](http://explainshell.com)
* [http://www.commandlinefu.com](http://www.commandlinefu.com)

**Shell Cheat Sheets**
* [Unix/Linux Command Cheat Sheet]( http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)
* [Software Carpentry Shell Cheatsheet](https://github.com/swcarpentry/boot-camps/blob/master/shell/shell_cheatsheet.md)

**General Help**
* man bash - run this at your command line to learn more about bash
* Google - Googling things you don't know. Other people have probably had the same question.
* Learn by doing. There is no better way to learn other than  by trying.

<a name="IntroVim"></a>
## Introduction To Vim

### Creating Text Files
There are two ways to create text files: using GUI text editors or command-line text editors.
> **NOTE:** by "text editor," we really do mean "text". The editors can only work with plain characters,
  not tables, images, nor any other media.


#### GUI text editors
[TextWrangler](http://www.barebones.com/products/textwrangler/), [Sublime](http://www.sublimetext.com/),
and [Notepad++](http://notepad-plus-plus.org/) are examples of GUI text editors. They have a **G**raphical
**U**ser **I**nterface that has buttons and menus that you can click on to issue commands to the
computer and you can move about the interface just by pointing and clicking.

#### Command-line text editors
If we are working on remote computer (i.e. high-performance compute environments) we don't have
access to a GUI and so we need to use **Command-line editors** to create, modify and save files.
When using these types of editors, you cannot 'point-and-click', you must navigate the interface
using only the keyboard.

Popular command-line editors include [nano](https://www.nano-editor.org/), [Emacs](http://www.gnu.org/software/emacs/)
or [Vim](https://www.vim.org/). These editors are available by default
on any shell environment, including on high-performance compute environments (local or cloud).

### Vim Text Editor
It is a powerful text editor with extensive text editing options; however, in this introduction
we are going to focus on exploring some of the more basic functions. To help you remember some of
the keyboard shortcuts introduced and to allow you to explore additional functionality on your own,
the research team at the [Harvard Chan Bioinformatics Core](https://bioinformatics.sph.harvard.edu/)
has compiled a [cheatsheet](https://hbctraining.github.io/In-depth-NGS-Data-Analysis-Course/resources/VI_CommandReference.pdf)

#### Vim Interface
Get into your work environment with `cd` and make a copy of the file `notes.txt` into a new document entitled
`vim_notes.txt`. Use vim to open the new document

~~~
$ cd ~/Desktop/data-shell
$ cp notes.txt vim_notes.txt
$ vim vim_notes.txt
~~~
#### Vim Modes
Vim has two basic modes that will allow you to create documents and edit your text:
> * **command mode (default mode):** allows you to save and quit the program (and execute other more advanced commands).
 * **insert (or edit) mode:** allows you to write and edit text

Files open with `vim` are automatically in command mode. To change to the INSERT mode, push the `i-key` and
notice the `--INSERT--` at the bottom left hand of the screen.

Type a few lines of text:
>While vim offers great functionality, it takes time to use, get familiar and learn the shortcuts.

After you have finished typing, press `esc` to enter command mode. Notice the `--INSERT--` disappeared
from the bottom of the screen.

#### Vim Saving and Quitting

To write to file (save), type `:w`. You can see the commands you type in the bottom left-hand corner of the screen.

After you have saved the file, the total number of lines and characters in the file will print out at the bottom
left-hand section of the screen.

Alternatively, we can write to file (save) and quit all at once. Let’s do that by typing `:wq`. Now, you should
have exited vim and returned to the command prompt. To edit your `vim_notes.txt` document, open up the file again
using the same command you used to create the file:``vim vim_notes.txt`.

Change into the insert mode and type a few more lines (you can move around the lines of text using
the arrows on the keyboard). This time we decide to quit without saving by typing `:q!`

#### Vim Editing
Create a new document `new_vim_test.txt` in vim. Enter the text as follows:
```add image```

Add line number to the document by switching to the command mode and typing `:set number`.
```add image```

**Save the document**. If you choose to remove the line numbers later you can type `:set nonumber`

*Vim* has shortcuts (which are completely unituitive, but very useful as you get used to them over time).
Check to see what mode you are currently in. While in command mode, try moving around the screen and
familarizing yourself with some of these shortcuts:

---
| **Navigation Shortcuts**         |    **Editing Shortcuts**           |
|----------------------------------|------------------------------------|
|**key**| **action**               | **key**  | **action**              |  
|-------|--------------------------|----------|-------------------------|    
|`gg`   | move to top of file      |`dd`      | delete line             |    
|`G`    | move to bottom of file   |`u`       | undo                    |    
|`$`    | move to end of line      |`Ctrl + r`| redo                    |   
|`O`    | move to beginning of line|`i`, `esc`| insert and command modes|

<a name="Shellscriptss"></a>
## Shell scripts and for loops

