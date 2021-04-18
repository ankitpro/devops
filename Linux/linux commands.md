# Ankit Agarwal
## _Linux Commands, Most Used_

[![N|Solid](https://icons.iconarchive.com/icons/tatice/operating-systems/256/Linux-icon.png)](https://www.linux.com/what-is-linux/)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


- [About Linux](#about-linux)
- [What is Linux?](#what-is-linux)
- [Basic Commands](#basic-commands)
- [Introduction To Linux](#introduction-to-linux) </br>
      - [Command-Line Structure](#command-line-structure)
- [Man Page Categories](Man-Page-Categories)
- [Info Documentation](Info-Documentation)




- [Everyday use](#everyday-use)
- [More resources](#more-resources)
- [Disclaimer](#disclaimer)

# About Linux
A Linux-based system is a modular Unix-like operating system, deriving much of its basic design from principles established in Unix during the 1970s and 1980s. Such a system uses a monolithic kernel, the Linux kernel, which handles process control, networking, access to the peripherals, and file systems.

- **OS family:** Unix-like
- **Default user interface:** Unix shell

# What is Linux
Just like Windows, iOS, and Mac OS, Linux is an operating system. In fact, one of the most popular platforms on the planet, Android, is powered by the Linux operating system. An operating system is software that manages all of the hardware resources associated with your desktop or laptop. To put it simply, the operating system manages the communication between your software and your hardware. Without the operating system (OS), the software wouldn?t function.

The Linux operating system comprises several different pieces:

- **Bootloader** –  The software that manages the boot process of your computer. For most users, this will simply be a splash screen that pops up and eventually goes away to boot into the operating system.
- **Kernel** – This is the one piece of the whole that is actually called ?Linux?. The kernel is the core of the system and manages the CPU, memory, and peripheral devices. The kernel is the lowest level of the OS.
- **Init system** – This is a sub-system that bootstraps the user space and is charged with controlling daemons. One of the most widely used init systems is systemd? which also happens to be one of the most controversial. It is the init system that manages the boot process, once the initial booting is handed over from the bootloader (i.e., GRUB or GRand Unified Bootloader).
- **Daemons** – These are background services (printing, sound, scheduling, etc.) that either start up during boot or after you log into the desktop.
- **Graphical server** – This is the sub-system that displays the graphics on your monitor. It is commonly referred to as the X server or just X.
- **Desktop environment** – This is the piece that the users actually interact with. There are many desktop environments to choose from (GNOME, Cinnamon, Mate, Pantheon, Enlightenment, KDE, Xfce, etc.). Each desktop environment includes built-in applications (such as file managers, configuration tools, web browsers, and games).
- **Applications** – Desktop environments do not offer the full array of apps. Just like Windows and macOS, Linux offers thousands upon thousands of high-quality software titles that can be easily found and installed. Most modern Linux distributions (more on this below) include App Store-like tools that centralize and simplify application installation. For example, Ubuntu Linux has the Ubuntu Software Center (a rebrand of GNOME Software? Figure 1) which allows you to quickly search among the thousands of apps and install them from one centralized location.


## Basic Commands
To find a file with an extension ".py" use the below command:
```
#find . -name '*.py' | xargs grep some_function
#cat hosts | xargs -I{} ssh root@{} hostname
```

## Introduction to Linux
### Command-Line Structure
A command has three components:
- **Command name**: This is just the name of the command.
- **Option(s)**:An option (also referred to as a flag) is a predefined value that changes the
behavior of the command. The format of options can vary. In some cases, the option
begins with a single hyphen followed by a single character; for example: ls -a. In other
cases, the option begins with two hyphens followed by a word; for example: ls --all.
In some rare cases, the option is just a single character with no hyphen. The format
depends on the command because some commands support the single-hyphen method
whereas others support the double-hyphen method (and some support both methods).
- **Arguments**:Arguments are used to provide additional information to the command.
This information could be things like a filename, user name, or host name.

Command: cp -r <filename1> <filename2>
</br>
cp : copy [Command]
</br>
-r : recursive [Option]
</br>
filename1 : Filename of the file which you wanna copy. [Argument]
</br>
filename2 : Filename of the file where you wanna copy. [Argument]
</br>

```
#cp -r ./fileHejJv3 ./test
```

### Man Page Categories
Many different types of man pages exist. For example, there are man pages for commands that regular users execute and man pages for commands that administrators execute. There are also man pages for libraries (programs used by other programs) and system configuration files.
These different types of man pages are broken into categories,10 as shown in the man page for the man command:
```
#man man
```
```
Output:
MAN(1)                                           Manual pager utils                                          MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is the system's manual pager.  Each page argument given to man is normally the name of a program, util-
       ity or function.  The manual page associated with each of these arguments is then found  and  displayed.   A
       section,  if provided, will direct man to look only in that section of the manual.  The default action is to
       search in all of the available sections following a pre-defined order (see DEFAULTS), and to show  only  the
       first page found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
```
Rest of the output is skipped.

In most cases, you don’t have to worry much about these categories. When you execute the man command, it first searches category 1 for the man page. If it doesn’t find it, it then searches the next category.11 Eventually it finds and displays the man page or displays an error if it can’t find the man page in any category:
```
# man nope
No manual entry for nope
```
In some cases you must specify the category. For example, there is a user command named passwd (category 1) and a file format named passwd (category 5). If you execute the man passwd command, the passwd command man page displays. To view the man page for the passwd file, you must execute the man 5 passwd command.

### Info Documentation
In addition to man pages, you might find info documentation helpful. Not all commands and files have info documentation, but for those that do, using it can be easier than using man pages. To use an info document, execute the info command followed by the command to
display; for example, info ls.
The documentation found in info pages tends to be more verbose than in man pages. The sections of info pages are also organized differently than man pages. Instead of one long document of text, info pages appear in hyperlinked sections. For example, if you scroll down the document for the ls command (use the down-arrow key on your keyboard), you see this:
```
#info ls
```
```
* Menu:
* Which files are listed::
* What information is listed::
* Sorting the output::
* Details about version sort::
* General output formatting::
* Formatting file timestamps::
* Formatting the file names::
```
This is a menu of subcategories you can jump to by placing your cursor on a menu item and pressing the Enter key. After you’re in a subcategory, type the letter u to go back up one level.
To see additional commands, press the H or ? key.

> NOTE:</br>
In the help section, press l to exit help and return to the info page. Use q to quit the info document and return to the command line.

> Tip: </br>
You can learn a lot from info documentation. Try executing the info command with no arguments. Then scroll down to the menu section, pick a category, press the Enter key, and start exploring.