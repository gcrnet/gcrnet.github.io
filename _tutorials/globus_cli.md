---
layout: post
title: Globus CLI
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 08 June 2020
---

The Globus CLI is a Python-based application that must be installed on the computer systems at both ends of your file transfer. It requires a Python version of at least 2.7 or 3.3, as well as the Python "pip" command.

1. [Installation](#install)
2. [Logging in into Globus](#login)
3. [Using the interface](#interface)

<a name="install"></a>
## Installation
The Globus website provides [CLI installation](https://docs.globus.org/cli/installation/) instructions that cover all types of operating systems. It also includes instructions for updating and removing the CLI. This page follows the recommendations from the Globus site, while only giving instructions for installing on XSEDE resources and assuming that you are running the Bash shell. When installed, the CLI will be added to your shell path and will automatically be available when you log in again. <br>

<a name="login"></a>
## Logging in into Globus
Before you can use the Globus CLI on a given computer, you must log in to Globus using the `globus login` command on the computer.

![login](https://i.imgur.com/Q4WVRH8.png)

It will redirect you to the browser and you need to login with your Globus credentials.

![browser_login](https://i.imgur.com/r3BdBfJ.png)

After successful login you will see a success message in the terminal.

![login success](https://i.imgur.com/3PzyoP4.png)

You will now be able to issue Globus CLI commands on this computer. You can check your Globus login status at any time with the command `globus whoami`.

<a name="interface"></a>
## Globus CLI Commands
Once you have logged in to Globus in a shell, you will be able to issue Globus CLI commands. Each CLI command begins with `globus` and the command name, possibly followed by a sub-command name and/or flags and arguments. To see more information about a specific CLI command, pass the `--help` flag to the command.

You can see a list of all Globus CLI commands by issuing the command:

```yml
globus list-commands
```
There are over four dozen commands, many of which are in groups containing a parent command and multiple sub-commands.
If you need more information on any CLI command, Globus provides in-depth [here](https://docs.globus.org/cli/reference/).
