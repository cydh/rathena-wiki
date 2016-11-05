---
title: Screen
permalink: /Screen/
---

**Screen** is a full-screen window manager that multiplexes a physical terminal between several processes, typically interactive shells. Each virtual terminal provides the functions of the DEC VT100 terminal and, in addition, several control functions from the ANSI X3.64 (ISO 6429) and ISO 2022 standards (e.g., insert/delete line and support for multiple character sets). There is a scrollback history buffer for each virtual terminal and a copy-and-paste mechanism that allows the user to move text regions between windows. When screen is called, it creates a single window with a shell in it (or the specified command) and then gets out of your way so that you can use the program as you normally would. Then, at any time, you can create new (full-screen) windows with other programs in them (including more shells), kill the current window, view a list of the active windows, turn output logging on and off, copy text between windows, view the scrollback history, switch between windows, etc. All windows run their programs completely independent of each other. Programs continue to run when their window is currently not visible and even when the whole screen session is detached from the users terminal.

Do I have Screen?
-----------------

Usually screen is already on some systems by default. to check if your system has screen simply type:

`screen`

If you get a bash error, you do not have Screen.

### So where is it?

Screen can be gotten many different ways and from many different places dependingon your operating system. Currently I only know a few. So those will be here. ALot of \*nix operating systems have there own repository of programs where you can get to them with a simple key phrase.

#### Gentoo

`emerge -vp screen`

If there is a package matching that it shoudl show. alternatively you can goto

[`http://packages.gentoo.org/search/?sstring=screen;offset=40`](http://packages.gentoo.org/search/?sstring=screen;offset=40)

which shows you if screen is there.

#### Fedora Core

`yum search screen`

This should bring up a number of results. you want the one that says SCREEN.

#### Debian

[`http://packages.debian.org/stable/misc/screen`](http://packages.debian.org/stable/misc/screen)

You may also use debians easy to use apt=get. I suggest search first.

`apt-cache search screen --names-only`

If it is there/present then do

`apt-get screen`

The othe rmethod is to use wget and compile yourself.

`wget `[`http://ftp.debian.org/debian/pool/main/s/screen/screen_4.0.2.orig.tar.gz`](http://ftp.debian.org/debian/pool/main/s/screen/screen_4.0.2.orig.tar.gz)

#### Others

As with Debian, you can also use wget to retrieve the package for most other operating systems (given wget is installed!)

`wget `[`ftp://mirrors.kernel.org/gnu/screen/screen-4.0.2.tar.gz`](ftp://mirrors.kernel.org/gnu/screen/screen-4.0.2.tar.gz)

### Installing Screen

If you got it from a repository like with yum or emerge then th eoperating system installs it for you. If you downloaded it the old fashion way then you need to decompress the file and compile the program.

`tar zxvf screen-4.0.2.tar.gz ( or whatever it's called )`

After that

`cd screen-4.0.2`
`./configure`
`make`
`make install`

This should configure/make/install screen If y ou run into any issues read the read me for screen. It is very thought out and decently written.

Using Screen
------------

Screens interface is fairly simple. It seems the developers had the new \*nix crowd in mind when the developed it. Screens functions are

`screen`
`screen -r`
`screen -r PID`
`screen -wipe`
`screen -help`

### Screen

This function Gets you INTO screen. Some systems require you to hit a key before proceeding into screen mode. TO get out of screen mode you type exit. There is another function in this mode called DETACH. This detahces your current screen allowing you to do other stuff while what you had running in screen is still runing. This is achieved by typing Ctrl+A and then Ctrl+D in that order in succesion.

### Screen -r

Screen -r shows you what screens are currently active. they show you whats active in the screens and what the screen PID's are. However if you only have ONE active screen it will auto matically attach that screen. Hint: if you just wanne get the list of active screen and you aren't sure if there is only one screen or more active type

`screen --list`

or

`screen -ls`

#### Screen -r PID

This function goes with Screen -r. Once you retrieve a PID of a screen you want to resume by using the command screen -r. You simply type in screen -r PID and the screen reattaches. The PID stands for Process ID.

SO lets say you wanted to resume a porno download that i slocated in a screen. And this screens PID is 13625. You would then type

`screen -r 13625`

and that screen would be reattached. You also can use the socketname (when its unique) when you started the screen with

`screen -S Socketname`

Example:

`screen -S Map-server`

#### Screen -D PID

This function Detaches a screen with is currently attached (used by another user or maybe a "ghost user"). You also can use Screen -D Socketname if you used a unique Socketname while starting the screen.

### Screen -Wipe

Screen -Wipe is used to wipe ALL dead screens. SOmetimes this command is needed after you are disconnected from your server via SSH while you have screens currently attached.

This command is needed when one of the following happen.

`Screen errors and believes some screens are already attached`
`Something happens and the processes are no longer valid yet screen won't let go of them`

### Screen -Help

Normal Help Syntax to bring up the help menu. The current help should show th efollowing for you.

    Options:
    -a            Force all capabilities into each window's termcap.
    -A -[r|R]     Adapt all windows to the new display width & height.
    -c file       Read configuration file instead of '.screenrc'.
    -d (-r)       Detach the elsewhere running screen (and reattach here).
    -dmS name     Start as daemon: Screen session in detached mode.
    -D (-r)       Detach and logout remote (and reattach here).
    -D -RR        Do whatever is needed to get a screen session.
    -e xy         Change command characters.
    -f            Flow control on, -fn = off, -fa = auto.
    -h lines      Set the size of the scrollback history buffer.
    -i            Interrupt output sooner when flow control is on.
    -l            Login mode on (update /var/run/utmp), -ln = off.
    -list         or -ls. Do nothing, just list our SockDir.
    -L            Turn on output logging.
    -m            ignore $STY variable, do create a new screen session.
    -O            Choose optimal output rather than exact vt100 emulation.
    -p window     Preselect the named window if it exists.
    -q            Quiet startup. Exits with non-zero return code if unsuccessful.
    -r            Reattach to a detached screen process.
    -R            Reattach if possible, otherwise start a new session.
    -s shell      Shell to execute rather than $SHELL.
    -S sockname   Name this session <pid>.sockname instead of <pid>.<tty>.<host>.
    -t title      Set title. (window's name).
    -T term       Use term as $TERM for windows, rather than "screen".
    -U            Tell screen to use UTF-8 encoding.
    -v            Print "Screen version 4.00.02 (FAU) 5-Dec-03".
    -wipe         Do nothing, just clean up SockDir.
    -x            Attach to a not detached screen. (Multi display mode).
    -X            Execute <cmd> as a screen command in the specified session.

Examples
--------

### Starting/Stoping

#### SQL only

Edit: \*\*\*\*server.sh (3 Files) Replace

`./****-server`

With

`./****-server_sql`

#### Both

Create: Starting.sh (chmod 700)(For Fast Server Start up)

`screen -A -m -d -S loginserver ~/files/stable/login-server.sh`
`screen -A -m -d -S charserver ~/files/stable/char-server.sh`
`screen -A -m -d -S mapserver ~/files/stable/map-server.sh`

Create: Stoping.sh (chmod 700)(For fast server shut down... may result in a ~5 min rollback)

`screen -S mapserver -X quit`
`screen -S charserver -X quit`
`screen -S loginserver -X quit`

Console: Make sure all script ale executeable

`chmod 700 *.sh *_sql`

#### Using The Script

-   Staring The Sever

`./Starting.sh`

-   Emergency Shutdown

`./Stoping.sh`

-   Attach Charserver

`screen -r charserver`

-   Attach Mapserver

`screen -r mapserver`

-   Attach Loginserver

`screen -r loginserver`

-   Dettach from inside a screen

`Ctrl + A Then D`

-   Restart a server from inside the screen

- press (once only!)

`Ctrl + C`

-   Stop a server from inside the screen (clean shut down)

`Ctrl + C`

Wait until server shut down completly and then press again (to prevent restart - else it autorestarts after 5 secounds)

`Ctrl + C`

Troubleshooting
---------------

Q: I cannot seem to get this to work.
A: Take your time and read the documentation. A lot is explained in there.

External Links
--------------

**Tutorials**
Various tutorials on the web about screen:

-   [GNU screen: An Introduction and Beginner's Tutorial](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
-   [How to use Screen](http://www.redbrick.dcu.ie/help/tutorials/screen)
-   [Introduction to screen](http://www.linuks.mine.nu/irc/screen/)
-   [Using screen by David Dorgan](http://www.linuxgazette.com/node/122)
-   [Installing and Using GNU Screen](http://www.sun.com/bigadmin/features/articles/gnu_screen.html) - includes specific information about installing screen on a Solaris system.
-   [Tutorial: Use GNU Screen (in UNIX)](http://cosmic.homeunix.net/blog/old/00000018.html)
-   [A Brief Introduction to Screen](http://www.zorg.org/linux/screen.shtml)
-   [Using the screen package](http://www.linuxquestions.org/questions/answers/297)
-   [Screen: The Terminal Multiplexer](http://www.bangmoney.org/presentations/screen.html)

Disclaimer and copyrights
-------------------------

Some of the info contained in this guide were obtained from the GNU website as they created Screen. In cooperation with the GPL, this guide is freely distributable and usable by anybody unless used for the explicit purpose of gaining financial wealth.

This guide also conforms with XHTML and WC3 standards.

[Category:Technical Guides](/Category:Technical_Guides "wikilink")