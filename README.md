# Licensing
Whenever you think about adding your stuff to github.com/opendreambox, you should 
think about the license you want to apply to your code/resources.
It is a common agreement in the open source world to put a file called 
LICENSE or COPYING into the root directory of your project and/or to add
the license text to the head of all your sources.

Please always take care not to violate the license of code you didn't 
actually write yourself but got somewhere else.

# Adding new plugins or skins
Everyone is welcome to publish their plugins and/or skins on github.com/opendreambox.
Every plugin and skin added to github.com/opendreambox can be added to the
official build system and will usually be available via the official 
experimental mirrors within a day.

## Directory structures and paths
Before you start you should have a rough look at existing directory
structures and structure your things accordingly.
Please do not use any absolute paths, neither in the Makefiles nor in a plugin.
Both autotools and enigma2 provide proper mechanisms to locate a path
properly using environment variables or helper-functions.
In Makefiles you would use variables like $(sysconfdir) or $(prefix)
instead of /etc and /usr. 
In enimga2 and any of its plugins you could use eEnv.resolve() to do the same.
In addition you can use enigma2's Tools.Directories.resolveFilename() 
in conjunction with the according SCOPE_* constants.

## Add your plugin to the build system
Basically everything on github.com/opendreambox will automatically be built on a
daily basis. This is done using "autotools" in an openembedded build environment.
If you want to set up your own openembedded you can take a look at
http://opendreambox.org/ (you will need a Linux system for that).
Whenever you have something new that you would like to be built properly, you 
have to add a proper Makefile.am to every directory that contains files
that have to be compiled and/or installed somewhere on the target system.
In addition, you should always check that you properly extended the 
files "configure.ac" and "Makefile.am" in the root of the git you are
going to commit your files to (no matter if it is a skin or a plugin).
In the Makefile.am in the git-root just add your new plugin's directory
to the "SUBDIRS" variable.
In the configure.ac you have to add all directories containing a
Makefile to the "AC_CONFIG_FILES" call. Just have a look at the existing entries.
Please try to keep the given alphabetical order in those files, it makes
finding and fixing things a lot easier.

If you are not familiar with Makefiles or configure.ac, just try to take a look
at existing content. You'll find lots of examples in enigma2-plugins.

## Become the maintainer of what you created
If you're adding an enigma2-plugin, please also consider adding a proper 
maintainer.info for your plugin.
A maintainer.info just contains two things: the mail address of the author
plus the name of the plugin.
It enables users to send a crashlog to the actual maintainer of a plugin 
that seems to have caused a crash.

Example:
```
stephan@reichholf.net
WebInterface
```
# Changing other people's plugins or skins
Before changing anything in someone else's sources, please try to contact 
him/her and discuss the things you want to change.
Sometimes people have good reasons why they don't want particular things to
be in their plugin or maybe they have certain quality-standards they would
like the code to catch up to.
Sometimes though, the original author doesn't maintain a plugin anymore.
So if you have any fixes or enhancements for some existing plugin that 
doesn't seem to be maintained anymore or you cannot get any feedback from 
the original author, you can always go ahead and commit your changes.
As github.com/opendreambox uses git, you can undo your changes at any time, if you want
or have to.
But again, please check that whatever you're going to change doesn't violate 
any licenses!

# Getting in contact
If you want to get in contact with some of the people that created and
maintain the projects on github.com/opendreambox you are always welcome 
to join us on #enigma2 in the freenode.net IRC network.
