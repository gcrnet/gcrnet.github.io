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
4. [Endpoint Commands](#endpoint)

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

<a name="endpoint"></a>
## Endpoint Commands

#### Endpoint IDs and Display Names
Most Globus Command Line Interface (CLI) commands require you to specify one or more endpoints, so it is important to understand how Globus endpoints are identified. Each endpoint has a globally unique 32 character ID as well as a user-friendly and non-unique "display name". It is the ID that must be used in CLI commands.

#### Searching for Endpoints
To acquire the necessary endpoint IDs, users can search using the CLI's `endpoint search` command.
By default, the search will be performed on all endpoints (its scope is "all"). When searching over all endpoints you must add a quoted search term argument to the command. The CLI will search for the term(s) in various endpoint attributes, such as display name, description and organization, but will not attempt to match the owner name.

In this example, we search for all endpoints whose fields contain the text "uncg".

![endpoint search](https://i.imgur.com/q1WIaVS.png)

Such searches can return up to 100 results; in this example, the search returns over two dozen.

By using the --filter-owner-id option we can limit the results to those where the owner matches an ID we provide.

```yml
globus endpointsearch --filter-owner-id mail_id@test.com "uncg"
```

Results can also be filtered by a scope using the `--filter-scope` option. Several scopes are available, such as endpoints that are owned by you (`my-endpoints`) and endpoints that have been shared with you (`shared-with-me`). Only one such filter can be specified. When filtering in this way you do not have to provide a search term.

![scope](https://i.imgur.com/jI1m28Y.png)

The [globus endpoint search](https://docs.globus.org/cli/reference/endpoint_search/) reference page contains more information about this command.