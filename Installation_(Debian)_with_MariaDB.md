---
title: Installation (Debian) with MariaDB
permalink: /Installation_(Debian)_with_MariaDB/
---

[Debian](/Category:Installation_Guides "wikilink")

Why replace MySQL with MariaDB
==============================

MariaDB is a binary drop in replacement for MySQL. That means everything still works exactly the same as before but better!
You may ask why should you replace MySQL with MariaDB. Here's the reasons.

-   MariaDB is Open Source Software.
-   MariaDB has quicker security releases.
-   MariaDB's performance beats MySQL's performance.
-   MariaDB is compatible with your MySQL compatible software and tools.
-   MariaDB is starting to be more popular than MySQL.

Installing rAthena and MariaDB on Debian based distro
=====================================================

Set up MariaDB
--------------

First, we'll tell our system about where to download MariaDB by going to [MariaDB download page](https://downloads.mariadb.org/mariadb/repositories/). Select your OS and your OS version then select MariaDB 5.5. After that, MariaDB server installation instruction will appear on the bottom of the page.

Prerequisite
------------

This article will guide you on how to use Git to obtain the source code of rAthena, build it from source and installing MariaDB in place of MySQL.
This article is based on [Installation (Debian)](/Installation_(Debian) "wikilink") article.
This guide is assuming that you already have the operating system installed. Well first off let me congratulate you on your choice to run a linux server. I can honestly not think of any downsides to running a server with a linux operating system.

Deb Based Distributions of Linux

rAthena Installation Guide for Debian/Ubuntu/Knoppix/DSL/and Other DEB based Distro's Other Distro's are only applicable if they have APT-GET or Aptitude installed.

APT-GET - and - Aptitude

can be used in place of the other should you so choose but for the purposes of this guide and my own personal preference I choose to use apt-get

For Debian/Knoppix/and Other Distro's not including Ubuntu it may be necessary to substitute

sudo - for - su

To everyone who is running their Linux with a GUI (Graphical User Interface) I would recommend that you not get too attached to it since we will be using the Terminal/CLI (Command Line Interface). Necessary Programs

Required packages
-----------------

-   [git](http://packages.debian.org/stable/git)
-   [make](http://packages.debian.org/stable/make)
-   [gcc](http://packages.debian.org/stable/gcc)
-   [libmariadbclient-dev](http://packages.ubuntu.com/trusty-updates/libmariadbclient-dev)
-   [zlib1g-dev](http://packages.debian.org/stable/zlib1g-dev)
-   [libpcre3-dev](http://packages.debian.org/stable/libpcre3-dev) (optional, for [PCRE](/PCRE "wikilink") support)
-   [libssl-dev](http://packages.debian.org/stable/libssl-dev) (required, for compiling with MariaDB 5.5)

`[root]# apt-get install git make gcc libmariadbclient-dev zlib1g-dev libpcre3-dev build-essential mariadb-client`

Create a non-root Linux user
----------------------------

By the [principle of least privilege](/wikipedia:Principle_of_least_privilege "wikilink"), it is recommended you do **NOT** run rAthena as root.

1.  Type the following command to create a non-root Linux account:

        useradd --create-home --shell /bin/bash rathena4444

    `--create-home` = create the user's home directory

    `--shell` = sets their login shell to [Bash](/wikipedia:Bash_(Unix_shell) "wikilink")

    **`rathena4444`** = the login name of the new Linux account

    *`4444`* = pick your own random numbers to make the username more unique

2.  Set a password for the new user (run this command and follow the prompts):

        passwd rathena4444

Cloning The Repository
----------------------

You can obtain the latest version of rAthena by typing the following command. This will place rAthena in a folder called rAthena, but you are free to change it to whatever you like:

`git clone `[`https://github.com/rathena/rathena.git`](https://github.com/rathena/rathena.git)` ~/rAthena`

### Updating Existing Code

To pull the latest updates for rAthena you can do the following:

`git pull`

Please [this section](/Transition_from_SVN_to_GIT#Notes_about_GIT "wikilink") if you're having issues with updating.

Run configure script
--------------------

### Compile

` make server`
` chmod a+x login-server && chmod a+x char-server && chmod a+x map-server`

### How to Recompile

Recompiling is the same as compiling except you always run this command after you configure it

` make clean`
` make server`

How to Start
------------

Use the following commands:

To Start:

    ./athena-start start

To Stop:

    ./athena-start stop

To Restart:

    ./athena-start restart

if u get error like this : -bash: ./athena-start: /bin/sh^M: bad interpreter

just install dos2unix

    apt-get install dos2unix

then run :

    dos2unix athena-start

now u will able to use ./athena-start start after chmod a+x athena-start

Database Installation
---------------------

You may need to check if your MariaDB server is running. To do so you can:

    service mysql status

If its offline you can turn it on using this command line:

    service mysqld start

If it's online you can start creating your database by running the following command lines:

     mysql -u root -p

You will be asked to type in your root or administration password, after logging in successfully type the following commands to start making your ragnarok database.

     mysql> CREATE DATABASE (your ragnarok database name);

You need to create new user for your ragnarok database.

      mysql> GRANT ALL ON yourragnarokdatabasename.* TO yourdatabaseusername@localhost IDENTIFIED BY "yourdesiredpassword";

Now its time to create required tables. Exit mysql console, by using ctrl + c and start with:

     mysql -u username -password yourragnarokdatabasename  < /path/to/your/ragnarok folder/trunk/sql-files/main.sql

and all the other necessary sql files.

and done. Now all you have to do is edit your configuration files etc.

See Also
========

--Note: You're going to have to do the database work too. Create a database for your information