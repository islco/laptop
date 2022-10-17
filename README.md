Laptop
======

_Laptop_ is a script to set up an MacOS computer for web development.

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages
based on what is already installed on the machine.

Requirements
------------

:warning: At this time, this installation script is compatabile with 
MacOS Monterey.

Should you find yourself on a different OS version, tread carefully. Older versions may work but aren't actively tested.

:warning: Before proceeding with the installation steps below, please ensure both Homebrew and
the Xcode Command Line Tools have been installed and are updated to the latest versions.


This can be done by executing the following commands:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

```sh
xcode-select --install
```

NOTE: If you see the following message after executing the above command, double-check the System Preferences' 'Sofware Update' option to manually
confirm whether any XCode Command Line Tool updates are available:

``` sh
xcode-select: error: command line tools are already installed, use "Software Update" to install updates
```


_For troubleshooting either of the above, see upstream vendor docs/resources._

Install
-------

Begin by opening the Terminal application on your Mac. The easiest way to open
an application in MacOS is to search for it via [Spotlight]. The default
keyboard shortcut for invoking Spotlight is `command-Space`. Once Spotlight
is up, just start typing the first few letters of the app you are looking for,
and once it appears, press `return` to launch it.

In your Terminal window, copy and paste each of these two commands one at a
time, then press `return` after each one to download and execute the
script, respectively:

```sh
curl --remote-name https://raw.githubusercontent.com/Mariana-Tek/laptop/master/mac
```

```sh
bash mac 2>&1 | tee ~/laptop.log
```

The [script](https://github.com/Mariana-Tek/laptop/blob/master/mac) itself is
available in this repo for you to review if you want to see what it does
and how it works.

NOTE: :warning: The script may ask you to enter your MacOS password at various
points. This is the same password that you use to log in to your Mac.

Uninstall
---------

To revert the state of your local development environment, removing the applications
and configuration installed by _Laptop_, we have provided a rudimentary
script to uninstall _Laptop_.

It presumes that you may have installed additional packages via Homebrew and will
target the applications installed by _Laptop_ only. Likewise, it presumes
that you may wish to retain Homebrew itself.

In your Terminal window (NOTE: Do not select iTerm for this task, as it will be removed!),
 copy and paste each of these two commands one at a time, then press `return` after
 each one to download and execute the script, respectively:

```sh
curl --remote-name https://raw.githubusercontent.com/Mariana-Tek/laptop/master/mac_uninstall
```

```sh
bash mac_uninstall 2>&1 | tee ~/laptop.log
```

The [script](https://github.com/Mariana-Tek/laptop/blob/master/mac_uninstall) itself is
available in this repo for you to review if you want to see what it does
and how it works.

NOTE: :warning: The script may ask you to enter your MacOS password at various
points. This is the same password that you use to log in to your Mac.

Debugging
---------

Your last _Laptop_ run will be saved to `~/laptop.log`. Read through it to see if
you can debug the issue yourself. If not, copy the lines where the script
failed into a [new GitHub
Issue](https://github.com/Mariana-Tek/laptop/issues/new) for us. Or, attach the
whole log file as an attachment.

What it sets up
---------------

*System Utilities*

* [Homebrew] for managing operating system libraries 🍻
* [wget] for fetching content HTTP resources from the command line 📨

*Terminal*

* [iTerm2] for a great terminal 💻
* [Starship] for an easy to configure, highly informative command prompt 🚀

*Fonts*

* [Nerd Fonts] for all the emojis ✨

*Datastores*

* [PostgreSQL] for your DB utilities 🐘

*Git*

* [Git] for pushing and pulling code to our repositories ↕️
* [GitHub Desktop] for setting up your SSH keys automatically and committing code with a GUI ↕️

*Browsers*

* [Google Chrome] for an alternative to Safari 🕵️

*Editors*

* [Visual Studio Code] for a powerful but lightweight editor ☕ 📜

*Communication*

* [Slack] for communicating with your team 💬

*Security*

* [1 Password] for setting and getting secret credentials 🔐

*DevOps*

* [Docker for Mac] for running containers 🐋

[Homebrew]: http://brew.sh/
[wget]: https://www.gnu.org/software/wget/
[iTerm2]: https://iterm2.com/
[Starship]: https://starship.rs/
[Nerd Fonts]: https://www.nerdfonts.com/
[PostgreSQL]: https://www.postgresql.org/
[Git]: https://git-scm.com/
[Github Desktop]: https://desktop.github.com/
[Google Chrome]: https://www.google.com/chrome/
[Visual Studio Code]: https://code.visualstudio.com/
[Slack]: https://slack.com/
[1 Password]: https://1password.com/
[Docker for Mac]: https://www.docker.com/products/docker-desktop

It should take less than 15-20 minutes to install (depends on your machine and
internet connection).

Customize in `~/.laptop.local`
------------------------------

Your `~/.laptop.local` is run at the end of the `mac` script.
Put your customizations there. This repo already contains a `.laptop.local`
you can use to get started. It lets you install the following tools
(commented out by default):

* [Sublime Text] for a super fast, lightweight editor
* [Postman] for testing APIs in a great GUI interface
* [Sketch] for getting your designs looking right

[Sublime Text]: https://www.sublimetext.com/
[Postman]: https://www.postman.com/
[Sketch]: https://www.sketch.com/

For example:

```sh
#!/bin/sh

# brew cask install 'sublime-text'
# brew cask install 'postman'
brew cask install 'sketch'

```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

_Laptop_ functions such as `fancy_echo`, `brew_install_or_upgrade`,
and `brew_cask_install` can be used in your
`~/.laptop.local`.

```sh
# Go to your MacOS user's root directory
cd ~

# Download the sample file to your computer
curl --remote-name https://raw.githubusercontent.com/Mariana-Tek/laptop/master/.laptop.local
```

Credits
-------

This [Mariana Tek](https://marianatek.com/) project is based on [ISL's](https://isl.co/) iteration of [18F's laptop project](https://github.com/18f/laptop), which was originally based on [thoughtbot's laptop project](https://github.com/thoughtbot/laptop).

### Public domain

thoughtbot's original work remains covered under an [MIT License](https://github.com/thoughtbot/laptop/blob/c997c4fb5a986b22d6c53214d8f219600a4561ee/LICENSE).

18F's work on this project is in the worldwide [public domain](LICENSE.md), as are contributions to our project. As stated in [CONTRIBUTING](CONTRIBUTING.md):

> This project is in the public domain within the United States, and copyright and related rights in the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).
>
> All contributions to this project will be released under the CC0 dedication. By submitting a pull request, you are agreeing to comply with this waiver of copyright interest.

Mariana Tek's original work is covered under a MIT License.
