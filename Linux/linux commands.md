# Ankit Agarwal
## _Linux Commands, Most Used_

[![N|Solid](https://icons.iconarchive.com/icons/tatice/operating-systems/256/Linux-icon.png)](https://www.linux.com/what-is-linux/)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


1. [About Linux](#about-linux)
2. [What is Linux?](#what-is-linux)
3. [Basic Commands](#basic-commands)
4. [Introduction To Linux](#introduction-to-linux)
      * [Command-Line Structure](#command-line-structure)
      * [Man Page Categories](#man-page-categories)
      * [Info Documentation](#info-documentation)
5. [The Filesystem](#the-filesystem)
      * [Understanding the Filesystem](#understanding-the-filesystem)
      * [Learning the Most Used Directories](#learning-the-most-used-directories)
      * [Navigating the Filesystem](#navigating-the-filesystem)
      * [Managing the Filesystem](#managing-the-filesystem)
      * [Managing Directories](#Managing-Directories)
      * [Managing Files](#managing-files)
      * [Wildcards](#wildcards)
      * [Redirection](#Redirection)




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

- **Bootloader** ???  The software that manages the boot process of your computer. For most users, this will simply be a splash screen that pops up and eventually goes away to boot into the operating system.
- **Kernel** ??? This is the one piece of the whole that is actually called ?Linux?. The kernel is the core of the system and manages the CPU, memory, and peripheral devices. The kernel is the lowest level of the OS.
- **Init system** ??? This is a sub-system that bootstraps the user space and is charged with controlling daemons. One of the most widely used init systems is systemd? which also happens to be one of the most controversial. It is the init system that manages the boot process, once the initial booting is handed over from the bootloader (i.e., GRUB or GRand Unified Bootloader).
- **Daemons** ??? These are background services (printing, sound, scheduling, etc.) that either start up during boot or after you log into the desktop.
- **Graphical server** ??? This is the sub-system that displays the graphics on your monitor. It is commonly referred to as the X server or just X.
- **Desktop environment** ??? This is the piece that the users actually interact with. There are many desktop environments to choose from (GNOME, Cinnamon, Mate, Pantheon, Enlightenment, KDE, Xfce, etc.). Each desktop environment includes built-in applications (such as file managers, configuration tools, web browsers, and games).
- **Applications** ??? Desktop environments do not offer the full array of apps. Just like Windows and macOS, Linux offers thousands upon thousands of high-quality software titles that can be easily found and installed. Most modern Linux distributions (more on this below) include App Store-like tools that centralize and simplify application installation. For example, Ubuntu Linux has the Ubuntu Software Center (a rebrand of GNOME Software? Figure 1) which allows you to quickly search among the thousands of apps and install them from one centralized location.


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

In most cases, you don???t have to worry much about these categories. When you execute the man command, it first searches category 1 for the man page. If it doesn???t find it, it then searches the next category.11 Eventually it finds and displays the man page or displays an error if it can???t find the man page in any category:
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
This is a menu of subcategories you can jump to by placing your cursor on a menu item and pressing the Enter key. After you???re in a subcategory, type the letter u to go back up one level.
To see additional commands, press the H or ? key.

> Note:</br>
In the help section, press l to exit help and return to the info page. Use q to quit the info document and return to the command line.

> Tip: </br>
You can learn a lot from info documentation. Try executing the info command with no arguments. Then scroll down to the menu section, pick a category, press the Enter key, and start exploring.

# The Filesystem
## Understanding the Filesystem
Typically, new Linux users have some experience in another operating system, such as Microsoft Windows. One of the challenges of using the Linux filesystem is understanding that the layout is likely to be different than what you are used to.</br>
For example, in Microsoft Windows, physical drives are assigned letters, such as C: or F:. They may be visible under the My Computer icon. Linux doesn???t use drive letters or a My Computer icon. Instead, all drives, including network drives and removable media, are located under the root directory.</br>
The root directory is symbolized by the / character. This character is also used to separate directory and filenames in a path. Think of the path as directions to get to a file or directory.</br>
For example, the path /home/bob/sample.txt refers to a file named sample.txt that is in the bob directory. The bob directory is under the home directory, which in turn is under the root directory. See Figure 3.1 for a small example of a Linux filesystem.

## Learning the Most Used Directories
Thousands of directories are in a typical Linux filesystem. You should not worry about learning
about all of these directories when you first start learning Linux, but some are important
enough to learn now:
* **/home**???A user???s home directory; each user has a directory under the /home directory where she can store her files. This is one of the few places where the user should always have the right to create and manage files.
* **/root**???Root user???s home directory; the system administrator account on the system is called the root user. The home directory for the root user isn???t under the /home directory; instead it is under the /root directory.
* **/bin**???Executables (programs); most of the commands you execute as a regular user are placed here or in the /usr/bin directory.
* **/usr/bin**???Executables (programs); most of the commands you execute as a regular user are placed here or in the /bin directory.
* **/sbin**???Executables (programs) for system administrators; most of the commands you execute as a system administrator are placed here or in the **/usr/sbin** directory.
* **/usr/sbin**???Executables (programs) for system administrators; most of the commands you execute as a system administrators are placed here or in the **/sbin** directory.
* **/media**???Removable media (could also be /run/media); this is where you find the files for removable devices, such as CD-ROMs and USB drives.
* **/tmp**???Temporary files; typically, programs store files in this directory rather than placing files in a user???s home directory.

## Navigating the Filesystem
When using the command-line environment, you often need to refer to a directory structure to access a file or subdirectory. For example, you may want to view a file in a specific directory.</br>
When you first open a shell, you are automatically placed in your home directory. The directory you are in is referred to as your working directory or current directory. A common task is to switch the working directory to another directory, a process called change directory. </br>
A path or pathname is how you refer to a file or directory in the directory structure. The two types of pathnames are
* **Absolute**???A path that always starts from the root directory; for example, **/home/bob/sample.txt**
* **Relative**???A path that starts from the current directory; for example, if you are in the **/home** directory and want to access the sample.txt file that is under the bob directory (which is under the **/home** directory), you use **bob/sample.txt.**

```
root@308a62877e19:~# pwd
/root
root@308a62877e19:~# cd /usr/bin/
root@308a62877e19:/usr/bin# pwd
/usr/bin
```
Note that the prompt (root@308a62877e19:/usr/bin) indicates the current directory, so the pwd command isn???t always necessary. This isn???t always the case because the prompt is customizable.

## Managing the Filesystem
Now that you know how to move from one directory to another, you will want to see what is inside the directories. The ls command lists files in a directory:
```
root@308a62877e19:~# cd ~
root@308a62877e19:~# ls
test
```
By default the ls command displays all files in the current directory except hidden files. A hidden file has a . character at the beginning of the filename. To see all files, including hidden files, use the -a option to the ls command:
```
root@308a62877e19:~# ls -a
.  ..  .bash_history  .bashrc  .config  .lesshst  .profile  .vim  .viminfo  test
```
. represents the current directory and .. represents the directory above the current directories. You will always see these two hidden files regardless of which directory you are in.
Each of the hidden files (in some cases they are directories) that you see in this output contain information that modifies the user???s environment. For example, .bashrc and .profile modify how the BASH shell works for the current user.
How could you tell if .bashrc was a file or .mozilla was a directory? Use the -l option:

```
root@308a62877e19:~# ls -a -l ~
total 40
drwx------ 1 root root 4096 Apr 18 13:24 .
drwxr-xr-x 1 root root 4096 Apr 18 09:50 ..
-rw------- 1 root root  707 Apr 18 10:15 .bash_history
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
drwx------ 3 root root 4096 Apr 18 10:24 .config
-rw------- 1 root root   42 Apr 18 11:29 .lesshst
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
drwxr-xr-x 2 root root 4096 Apr 18 10:23 .vim
-rw------- 1 root root 6924 Apr 18 10:23 .viminfo
-rw-r--r-- 1 root root    0 Apr 18 13:24 test
```
When you use the -l option, each line describes detailed information for a file.
Let me explain one output with an example:
```
drwxr-xr-x 2 root root 4096 Apr 18 10:23 .vim
```
* **d** : File type(d - Directory)</br>
* **rwxr-xr-x** : Permissions</br>
* **2** : Hard Link Count</br>
* **root**: User Owner </br>
* **root**: Group Owner </br>
* **4096**: File size</br>
* **Apr 18 10:23**: Modification Time Stamp
* **.vim**: File Name

The details of the information provided by the ls -l command:
* **File type**???d means this is a directory whereas - means it is a plain file. There are additional file types, but these are the primary two you should know.
* **Permissions**???These are used to allow or disallow access to the file.
* **Hard link count**???This is a file that is hard linked and shares the same data block space with another filename.
* **User owner**???The user who owns the file has special access to the file. For example, only the user owner (and the root user) can change the permissions of a file.
* **Group owner**???Group owners have special access to the file via permissions.
* **File size**???The size of the file in bytes.
* **Modification timestamp**???The date and time the file was last modified.
* **Filename**???The name of the file.

## Managing Directories
To create a new directory, use the mkdir command:
```
root@308a62877e19:~# ls
test
root@308a62877e19:~# mkdir data
root@308a62877e19:~# ls -l
total 4
drwxr-xr-x 2 root root 4096 Apr 18 13:51 data
-rw-r--r-- 1 root root    0 Apr 18 13:24 test
```
Note a situation in which this could fail:
```
root@308a62877e19:~# ls
data
root@308a62877e19:~# mkdir test/samples
mkdir: cannot create directory 'test/samples': No such file or directory
```
This failure occurs because to make the samples directory in the test directory, the test directory must exist. To make both the samples and test directory, use the -p option to the mkdir command:
```
root@308a62877e19:~# ls
data
root@308a62877e19:~# mkdir -p test/samples
root@308a62877e19:~# ls
data  test
root@308a62877e19:~# ls test/
samples
```
To delete a directory that is empty, use the rmdir command:
```
root@308a62877e19:~# ls
data  test
root@308a62877e19:~# rmdir data/
root@308a62877e19:~# ls
test
```
The rmdir command only works on empty directories:
```
root@308a62877e19:~# ls
test
root@308a62877e19:~# rmdir test
rmdir: failed to remove 'test': Directory not empty
```
To delete an entire directory structure, including all the files and subdirectories, use the rm command with the -r option:
```
root@308a62877e19:~# ls
test
root@308a62877e19:~# rm -r test
root@308a62877e19:~# ls
root@308a62877e19:~#
```
> Note: </br>
The rm command is normally used to delete files. With the -r option, it can delete
directories and files.

Be careful when using the rm -r command. You could accidentally delete files that you really need to keep. Consider using the -i option when executing the rm -r command because this enables you to pick which files to delete. When prompted, answer y for yes and n for no:
```
root@308a62877e19:~# ls
root@308a62877e19:~# mkdir test1
root@308a62877e19:~# mkdir test2
root@308a62877e19:~# cd test1
root@308a62877e19:~/test1# touch file1.txt
root@308a62877e19:~/test1# touch file2.pdf
root@308a62877e19:~/test1# touch file3.html
root@308a62877e19:~/test1# ls
file1.txt  file2.pdf  file3.html
root@308a62877e19:~/test1# cd ..
root@308a62877e19:~# ls
test1  test2
root@308a62877e19:~# rm -ri test1
rm: descend into directory 'test1'? y
rm: remove regular empty file 'test1/file1.txt'? y
rm: remove regular empty file 'test1/file2.pdf'? y
rm: remove regular empty file 'test1/file3.html'? n
rm: remove directory 'test1'? n
root@308a62877e19:~# ls
test1  test2
root@308a62877e19:~# ls test1
file3.html
root@308a62877e19:~#
```

## Managing Files
To copy a file, use the cp command. You should have two arguments: what file to copy and where to copy it:
```
root@308a62877e19:~# ls
test1  test2
root@308a62877e19:~# cp /etc/hosts .
root@308a62877e19:~# ls
hosts  test1  test2
root@308a62877e19:~#
```
Recall that . represents the current directory.

Be careful when using the cp command because you can accidentally overwrite an existing file. This happens when the destination (where to copy the file) contains a file with the exact same name as an existing file:
```
root@308a62877e19:~# ls -l hosts
-rw-r--r-- 1 root root 174 Apr 18 14:03 hosts
root@308a62877e19:~# cp /etc/passwd hosts
root@308a62877e19:~# ls -l hosts
-rw-r--r-- 1 root root 1335 Apr 18 14:05 hosts
root@308a62877e19:~#
```
You can tell that the original file was overwritten because the file size changed (174 bytes to 1335 bytes) and the modification timestamp changed. To avoid overwriting an existing file, use the -i option:
```
root@308a62877e19:~# ls -l hosts
-rw-r--r-- 1 root root 1335 Apr 18 14:05 hosts
root@308a62877e19:~# cp -i /etc/passwd hosts
cp: overwrite 'hosts'? n
root@308a62877e19:~# ls -l hosts
-rw-r--r-- 1 root root 1335 Apr 18 14:05 hosts
root@308a62877e19:~#
```
> Tip: </br>
The rm-ri command is the same as the rm -ir command, which is the same as the rm -r -i command. In most cases, single character options can be combined and order doesn???t matter.

The -i option stands for ???interactive??? mode and prompts you if the cp command will end up overwriting an existing file.
Some additional useful commands to manage files include the following:
* **mv**???Used to move files or directories
* **rm**???Used to delete files
* **touch**???Creates an empty file or updates the modification timestamp of an existing file

## Wildcards
Suppose you want to copy all the files that end in .conf from the /etc directory to a directory called config in your home directory. You look in the /etc directory and realize that there are about 20 of these files. You don???t want to have to type in the name of each file. This is a case in which you want to use wildcards.
With wildcards, you can make use of special characters to match file or directory names. For example, you can list all the files in the /etc directory that end in .conf by executing the following command:
```
root@308a62877e19:~# ls -d /etc/*.conf
/etc/adduser.conf          /etc/e2scrub.conf  /etc/libaudit.conf  /etc/resolv.conf
/etc/ca-certificates.conf  /etc/gai.conf      /etc/mke2fs.conf    /etc/sysctl.conf
/etc/debconf.conf          /etc/host.conf     /etc/nsswitch.conf  /etc/ucf.conf
/etc/deluser.conf          /etc/ld.so.conf    /etc/pam.conf       /etc/xattr.conf
root@308a62877e19:~#
```
The * character represents ???zero or more characters in a filename.??? So, you are asking to see files in the /etc directory that begin with ???zero or more characters, followed by .conf.??? Using the * character, you can copy these files into a directory under your home directory (don???t worry if you get an error message for some of the files):
```
root@308a62877e19:~# ls
hosts  test1  test2
root@308a62877e19:~# mkdir config
root@308a62877e19:~# cp /etc/*.conf config/
root@308a62877e19:~# ls config/
adduser.conf          debconf.conf  e2scrub.conf  host.conf   libaudit.conf  nsswitch.conf  resolv.conf  ucf.conf
ca-certificates.conf  deluser.conf  gai.conf      ld.so.conf  mke2fs.conf    pam.conf       sysctl.conf  xattr.conf
root@308a62877e19:~#
```
Use the ? character to represent a single character. So, to display any files in the /etc directory that have filenames that are exactly four characters in length, execute the following command:
```
root@308a62877e19:~# ls -d /etc/????
/etc/dhcp  /etc/dpkg  /etc/ldap  /etc/mtab  /etc/perl  /etc/skel
root@308a62877e19:~#
```
The ? character will match any single character. If you want to match a specific character, you can use a set of square brackets, []. For example, to match a file in the /etc directory that begins with an a, b, or c character, execute the following command:
```
root@308a62877e19:~# ls -d /etc/[abc]*
/etc/adduser.conf  /etc/apparmor.d         /etc/bindresvport.blacklist  /etc/calendar
/etc/aliases       /etc/apt                /etc/binfmt.d                /etc/cron.d
/etc/aliases.db    /etc/bash.bashrc        /etc/ca-certificates         /etc/cron.daily
/etc/alternatives  /etc/bash_completion.d  /etc/ca-certificates.conf    /etc/cron.weekly
root@308a62877e19:~#
```
> **Using a Range in [ ]** </br>
Note that [abc] is the same as [a-c]. Using a - enables you to specify a range of permitted
characters. Just be sure it is a valid range according to the ASCII text table. You can view this
table by executing the command man ascii.

## Redirection
Suppose you run a command and you decide that you want to store the output of the command into a file for future use. In a situation like this, you can use a process called redirection. The idea is to redirect the output of a command into a file or another process. You can also redirect the input to a command from a file.

Each command has three data streams:
* **Standard input (stdin)**???The data that is sent into the command. This is not an argument but rather additional information that is being sent into a command. Typically, this data comes from a user who is executing the command. The user provides this data via the keyboard. This input could be redirected from a file or another process.
* **Standard output (stdout)**???The data that is sent from the command when all goes well. Typically, this appears on the screen, but it can be sent to a file or to another command.
* **Standard error (stderr)**???The data that is sent from the command when an error occurs. Typically, this appears on the screen, but it can be sent to a file or to another command.

To redirect stdout, use the > character after the command:
```
root@308a62877e19:~# cal 01 1994 > mycal
root@308a62877e19:~# cat mycal
    January 1994
Su Mo Tu We Th Fr Sa
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29
30 31
root@308a62877e19:~#
```


