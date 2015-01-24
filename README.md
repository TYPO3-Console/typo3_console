TYPO3 CMS Console [![Build Status](https://travis-ci.org/helhum/typo3_console.svg?branch=master)](https://travis-ci.org/helhum/typo3_console)
=================

Many frameworks come with command helper tools that enables interactions on the command line easily.
TYPO3 CMS currently has CLI support, but no dedicated command tool but only a CLI dispatcher script
which not straight forward to use and not nice to extend for developers.

A great step forward for developers is the possibility to register command controllers, but running them
also requires calling the cli_dispatcher. Another downside is, that until finally the command controller is reached,
the framework jumps through several hoops to finally bootstrap Extbase and run the requested command.

The goal of this project is to provide a clean API to register commands (using Extbase Command Controllers) and
providing a sane way to call the commands through a single command line tool called "typo3cms"

e.g.

Instead of typing

```
./typo3/cli_dispatch.phpsh extbase extension:install realurl
```

just type:

```
./typo3cms extension:install realurl
```

## Features
* Command line tool
* Flexible bootstrap for commands (not every command needs a fully bootstrapped framework)
* Cache flush and core cache warmup commands
* Scheduler command
* Backend lock/unlock commands
* Reference Index commands
* Support for all other Extbase command controllers


## Installation

For the extension to work, it *must* be installed in the typo3conf/ext/ directory *not* in any other possible extension location.
To get the typo3cms command, just _copy_ typo3_console/Scripts/typo3cms to your TYPO3 root directory. Windows users must copy
typo3_console/Scripts/typo3cms.bat to the TYPO3 root directory and set the location to the php.exe in that file (untested but should work).

Don't forget to activate the extension in the extension manager before you start using the command line tool.

#### linux shell installation
make sure **"_cli_lowlevel"** user is a valid backenduser with any password**

```
cd typo3conf/ext/
git clone https://github.com/helhum/typo3_console.git
cp typo3_console/Scripts/typo3cms ../../
cd ../../
php ./typo3/cli_dispatch.phpsh extbase extension:install typo3_console
php typo3cms help
```

## TODO & Ideas

Currently only a few commands are delivered with the extension, but those delivered are quite useful already. And if any other extension
adds Extbase command controllers, they will also be useable with the typo3cms command.

* … Add ideas to the issues section of this repository where title is prepended with "idea:"
