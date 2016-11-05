---
title: Installation
permalink: /Installation/
---

This article is aimed at downloading RAthena and any dependancies required to run it. In this article, you are expected to know basic file and program management of the OS you are attempting to run RAthena on. (Or use Google to search for the answers)

System Requirements
-------------------

RAthena runs on variety of 32-bit and 64-bit (limited) operating systems, including Windows, Linux and Unix. Hardware requirements are ones of typical server environment, whether virtual or dedicated.

Program Requirements
--------------------

To run RAthena, the following programs must be installed on the machine that will run RAthena:

### \*nix based

For \*nix, most of these programs will come as [Packages](/wikipedia:Software_package_%28installation%29 "wikilink") with your OS, for example, the FreeBSD Ports collection, or Debians apt-get or aptitude. Please see your OS's help/support pages to find out how to utilize package installations. As a general rule, the following packages will be required to compile RAthena:
[wget](http://www.gnu.org/software/wget/), [subversion](http://subversion.tigris.org/), [GCC](http://gcc.gnu.org/), [make](http://www.gnu.org/software/make/) (if running \*BSD, gmake is needed instead of make.)

#### libmysqlclient15-dev

libmysqlclient15-dev is the library for MySQL and is **required** to compile an SQL version of RAthena. This will most likely need to be installed via packages.

### Windows based

Depending on how you want to compile, one of two methods can be used. We **highly recommend** the use of [Visual C++](http://www.microsoft.com/Express/vc/). [Cygwin](http://www.cygwin.com/) can also be used. If cygwin is used, you have some configuration to do, please see below:

> Expand the development or devel branch in Cygwin and make sure GCC and Make are checked. These are the only 2 things you need, the others are up to you whether you want to download them or not. The downloading and installation of packages may take some time depending on your packages, their size, your network speed, and the remote server's network speed. This shouldn't take too long if it's just GCC and Make.

You will also need [subversion](http://subversion.tigris.org/)

Installing software
-------------------

### Linux OS's

A simple make and make install is all that is needed for most of the packages. You can find [instructions](/:Category:Installation "wikilink") and readmes in each of the downloads for your distro telling you how to install and compile each package. Once subversion is installed, you can download RAthena's latest source via the [SVN](/SVN "wikilink").
<code>

    ~$ svn co https://rathena.svn.sourceforge.net/svnroot/rathena/trunk

</code> for trunk, or
<code>

    ~$ svn co https://rathena.svn.sourceforge.net/svnroot/rathena/branches/stable

</code> If you want to use stable.

### Windows OS's

When using SVN in Windows, all your commands are in a right click menu integrated into the Windows Shell.
[Image:svnwindows.jpg](/Image:svnwindows.jpg "wikilink")
Simply create a new folder, right click on it and select 'SVN Checkout...' and a dialog box will appear.
[Image:checkout.jpg](/Image:checkout.jpg "wikilink")
Enter your URL (in the example above, simply add /trunk after the URL to checkout Trunk, or /branches/stable for stable) and TSVN will download a fresh copy of RAthena's SVN to that folder.

Compiling
---------

Please see [Compiling](/Compiling "wikilink") for more detailed instructions.

For your OS, you will need to compile binaries if you had downloaded RAthena via the SVN. you can then move on to [:Category:Configuration](/:Category:Configuration "wikilink") and then running RAthena.

See Also
--------

-   [Installation per OS](/:Category:Installation "wikilink")
-   [SVN](/SVN "wikilink")
-   [Installing SQL for RAthena use](/Installing_SQL "wikilink")

[Category:Basics](/Category:Basics "wikilink")