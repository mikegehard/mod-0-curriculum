---
layout:     page
title:      Turing Environment Setup Instructions
subheading: Getting Your Computer Ready For Programming
permalink:  setup-instructions
---


# Tech Setup

Complete the following steps before Mod 0 in order to get the tools you'll need on your machine.

Here's what we'll cover in this guide. Click a link to jump to that portion of the guide:

- [New to Mac?](#1-new-to-mac)
- [Install Atom as your Text Editor](#2-install-atom-as-your-text-editor)
- [Install Xcode-select](#3-install-xcode-select)
- [Install Homebrew](#4-install-homebrew)
- [Setup Github]($5-setup-github)
- [Install Git](#6-install-git)
- [Configure Git](#7-configure-git)
- [Install Chrome](#8-install-chrome)
- [Set Up Terminal Access for Atom](#9-set-up-terminal-access-for-atom)
- [Add GitHub SSH Keys](#10-add-github-ssh-keys)
- [Install Rectangle](#11-install-rectangle)

Lets get started:

## 1) New to Mac?

If this is your first time using a Mac instead of a PC or Linux, then watch [this video](https://www.youtube.com/watch?v=MN0FD8KW2V4) about the basics of using a Mac.

## 2) Install Atom as your Text Editor

Install [Atom](https://atom.io/). Atom is a program where we edit code - it is a text editor with many great features that makes editing code more enjoyable compared to a simple text editor. Atom is commonly used in the software development industry, and we will use it throughout your time at Turing.

## 3) Install Xcode-select

[Xcode](https://developer.apple.com/xcode/) is a suite of development tools published by Apple. If we wanted to develop software for the Apple Ecosystem (iPhone apps, macOS apps, etc), we would use Xcode as our editor. But even though we're not building iPhone apps, Xcode provides some system dependencies that we need.

Rather than download Xcode via the Apple Store, we can get a much smaller selection of necessary tools, called `xcode-select`, via our terminal.

Follow these steps to get Xcode-select installed on your machine:

1. Open the Terminal by pressing the `Command + Space` keys at the same time, which opens Spotlight, and then type `Terminal` into the search.
1. Press the enter key to open `Terminal`
1. Once terminal is open, type the following **without the `$` symbol**: 
 ```
  $ xcode-select --install
 ```
1. When prompted, enter the password you use to login to your computer.
1. Check that installation was succesful by typing `xcode-select` in your terminal. You should see something like this:

```
$ xcode-select
xcode-select: error: no command option given
Usage: xcode-select [options]

Print or change the path to the active developer directory. This directory
controls which tools are used for the Xcode command line tools (for example,
xcodebuild) as well as the BSD development commands (such as cc and make).

Options:
  -h, --help                  print this help message and exit
.
.
.
```

### A note on convention

When you see a `$` before a line, it means "enter what follows the dollar sign as a terminal command".

Lines that don't have a `$` are usually what is printed out as a _result_ of the command.

A `.` on adjacent lines means "omitted text here". For example:

```
$ xcode-select
Usage: xcode-select [options]

Print or change the path to the active developer directory. This directory
controls which tools are used for the Xcode command line tools (for example,
xcodebuild) as well as the BSD development commands (such as cc and make).

Options:
  -h, --help                  print this help message and exit
.
.
.
```

## 4) Install Homebrew

[Homebrew](https://brew.sh/) is a package management system that makes it easy to install hundreds of open source projects and compile them from source for maximum performance on your machine.

Follow these steps to get Homebrew installed on your machine:

1. Open `Terminal`. Again, you can get to Terminal by pressing the `Command + Space` keys at the same time, then typing `Terminal` into the search.

1. Once you have Terminal open, paste this line and hit enter. (remember, skip the `$`)

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

1. When prompted, enter the password you use to login to your computer. It needs this because it installs its packages in a place that all users of this computer can access.

1. When the process has completed, you will be given instructions for updating your `PATH` - follow the output from your terminal. It should look similar to this:
```
==> Next steps:
- Add Homebrew to your PATH in /Users/yourname/.zprofile:
    echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> /Users/yourname/.zprofile
    eval $(/opt/homebrew/bin/brew shellenv)
```

1. When it has completed the installation, type `brew doctor` in your terminal + press enter. It should tell you that everything is fine:

```
$ brew doctor
Your system is ready to brew.
```

<!-- If you got a warning from Homebrew about your path, do the following:

```
$ touch ~/.zshrc
$ echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.zshrc
$ source ~/.zshrc
// Now run "brew doctor" again and the warning should be gone.
``` -->

### I followed the above instructions and Homebrew won't install!
No worries! This likely means you have one of Apple's newest M1 laptops - fancy you 😉 ! Essentially, some programs are not currently supported with this setup, Homebrew being one of them. 

However, there is another way to get Homebrew installed using a program that's built into your Mac known as `Rosetta`

[This video](https://www.youtube.com/watch?v=nv2ylxro7rM) does a solid job of walking you through the steps to install Homebrew using Rosetta - don't worry about the native setup.

I've also outlined the steps here:

1. Open a Finder window by pressing `CMD + N` on your Desktop. You can also use Spotlight by pressing `CMD + Space` and searching for `Finder`
1. Click on the `Applications` folder on the left sidebar
1. Click into the folder called `Utilities`
1. Right click on the `Terminal` app and choose `Get Info`
1. Check the box that says `Open using Rosetta`
1. Open the `Terminal` app by either double clicking the icon or using a Spotlight search for `Terminal`
1. Proceed with Step 2 from the instructions above this section!

## 5) Setup Github
If you haven't had a chance to sign up for [Github](https://github.com/), now is a good time to do that.

Update your [GitHub Profile](https://github.com/settings/profile) and be sure that you choose a username, status, profile info and picture that is PROFESSIONAL and APPROPRIATE! Future employers will be looking at your Github to see your projects, code, etc.

## 6) Install Git

[Git](https://git-scm.com/) is a Version Control System (VCS). It allows you to save work on your project, and reference previous states of a project if needed. Normally when we save something on our computer, the newer version overwrites the older version. This is problematic if we need to look back at an earlier version. Git solves this problem by providing you multiple save points. You can get the current version, and ANY previous version. Git’s philosophy: never lose anything.

One other thing to clear up - `git` is not the same thing as `Github`. You'll learn more about how they interact in Mod 0!

To install Git, we will use Homebrew. Follow these steps to install `git` on your machine:

1. Open your Terminal, and type this:

```
$ brew install git
```
1. Check that it was successful by typing `git` in the terminal. It should output: 

```
$ git
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one
.
.
.
```

## 7) Configure Git

We'll want to configure git with some basic information about us.

We can tell git to configure itself using the git config command from our terminal. Additionally, we're setting "global" configurations for git, so we'll use the --global flag when we provide it with a new piece of configuration.

1. Open Terminal with Spotlight search (press the `Command + Space` keys like we did previously). 
1. Type the following, one at a time, **SUBSTITUTING YOUR OWN NAME AND EMAIL** for the first two commands:

```
git config --global user.name "Eric Weissman"
git config --global user.email eric@example.com
git config --global init.defaultBranch main
git config --global core.editor "atom --wait"
git config --global pull.rebase false
```

1. You can verify that this is working by typing `git config --list` in your terminal and checking the output: 

```
$ git config --list
credential.helper=osxkeychain
user.name=Eric Weissman
user.email=eric@example.com
init.defaultbranch=main
core.editor=atom --wait
pull.rebase=false

```
If you get "stuck" in the screen showing the output of `git config --list`, **don't panic!** Just type `q`, and you should get back to your regular terminal.


## 8) Install Chrome

If you're not already using Chrome, install it from [here](https://www.google.com/chrome/). Chrome includes a set of developer tools that will come in handy down the road. Additionally, it is always on the cutting edge of being able to support new web technologies.

--------------------

You've done a lot of environment setup! How about you take a break, go for a walk, drink some water.

We'll be here when you get back. :)

--------------------

## 9) Set Up Terminal Access for Atom

Install the shell commands for Atom. Open Atom, drop down the `Atom` menu in the top left corner of your screen, and click on `Install Shell Commands`. Atom should now be enabled from your command line.

![Install Shell Commands](/images/install_shell_commands.jpg)

To confirm that Atom is working from your command line, complete the following steps:
1. Open Terminal with Spotlight search (`Command + Space`), type `terminal` and hit enter. 
1. Type `atom .` in your terminal. **Be sure to include a space between `atom` and the `.`** If it is setup correctly, the atom editor will automatically open.
1. If you get an error, make sure you've selected `Install Shell Commands` from the Atom menu.
1. If is _still_ not working, try entering this in the command line:

```
ln -s /Applications/Atom.app/Contents/Resources/app/atom.sh /usr/local/bin/atom

```
1. Try opening Atom from the command line/terminal by typing `atom .` If it's still not working, message one of the Turing staff, or mention this in your cohort channel. We'll get this squared away!

Atom also offers a number of different options and packages that you can customize to your liking. [This](https://www.youtube.com/watch?v=WWwBQQOGllo&list=PLYzJdSdNWNqwNWlxz7bvu-lOYR0CFWQ4I) series of videos will walk you through many of them if you'd like to dive deeper.

## 10) Add GitHub SSH Keys

SSH keys are a more secure and convenient way of authenticating than typing in our password every time we want to interact with Github.

This is getting fairly advanced, so if you want to stop the setup instructions here, and come back later once you're annoyed at entering your Github password regularly, that's totally fine.

This can be a bit tricky to do, so here's another quick walk-through, of _just_ adding Github SSH keys:

<iframe width="560" height="315" src="https://www.youtube.com/embed/YVBwSh-vlFY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Generate a new key by running:

Follow these steps to generate a new key:
1. Open terminal and enter the following command - **You should use the email associated with your GitHub account**

```
$ ssh-keygen -t rsa -C "johndoe@example.com"
```

1. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location, which is `~/ssh/id_rsa`

1. When asked to enter a password, hit `enter`, which means "no password".

You'll see a confirmation message that looks like:

```
Your identification has been saved in id_rsa.
Your public key has been saved in id_rsa.pub.
The key fingerprint is:
SHA256:C3AB8FF13720E8AD9047DD39466B3C8974E592C your@email_address.com
The key's randomart image is:
+---[RSA 2048]----+
| .       =   ..  |
|o . . o + = ..   |
| =.o o o o o  .  |
|+ +o. .  ..  . . |
|.+E  .  S   o o..|
|..     .  .o . .+|
|        o  oo .o+|
|       . o  ==o.=|
|        . .+=B=o |
+----[SHA256]-----+
```

### 2. Add this new key to your system by running:

- In your terminal, run:
```
$ ssh-add ~/.ssh/id_rsa
```

### 3. Copy the new _public_ key to your clipboard:

- In your terminal, run:
```
$ pbcopy < ~/.ssh/id_rsa.pub
```

### 4. Tell GitHub about this key.

1.  Go to [https://github.com/settings/keys](https://github.com/settings/keys)
1.  Click the green `New SSH key` button.
1.  Leave the `title` section empty
1.  Paste the key into the `key` section with `Command + v`.
1.  Hit the green `Add SSH key` button.


**To test that our key is configured, type the following into the command line:**

- In your terminal, run:
```
$ ssh -T git@github.com
```

**If you get a prompt similar to this:**

```
The authenticity of host 'github.com (192.30.252.153)'... can't be established.
RSA key fingerprint is 00:11:22:33:44:55:66:77:88:99:aa:bb:cc:dd:ee:ff.
Are you sure you want to continue connecting (yes/no)?
```

-   Type `yes`

**If everything's working, you'll see the the following:**

```
Hi <your_username>! You've successfully authenticated, but GitHub does not provide shell access.
```

Great work! You've connected your terminal to your Github profile. You can now interact with Github from your terminal _without_ entering your password all the time.

## 11) Install Rectangle
**Install [Rectangle](https://rectangleapp.com/)** - Rectangle allows you to move and resize windows so you can watch the Zoom call and work in the terminal for your technical sessions.

Once you've installed Rectangle, open the app and it will run in the background. You should see a smaller version of the Rectangle icon in the top right corner of your screen.

Take some time to play around with the commands to adjust the positioning and size of different windows on your screen using the Rectangle shortcuts!

### You're Done!

Give yourself a pat on the back.

![congrats](https://media.giphy.com/media/xWZcTvh1cuAaSi7HeI/giphy.gif)
