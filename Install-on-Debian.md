Basic DEB Installation guide
============================

APT-GET and APTITUDE can be used interchangeably depending upon the Debian based Operating System. It needs to be run with sudo or su (depending again on your OS).

`apt-get update`

This part of the article will use subversion to obtain the source code of EA. The structure of subversion will allow the user to download either the trunk or branch of RA. A trunk contains the latest code that would be useful if you are testing or really need a new feature. The branch contains stable source code that has gone through testing and bug fixes to ensure that the server will remain stable with the highest uptime possible.

Linux

This guide is assuming that you already have the operating system installed. Well first off let me congratulate you on your choice to run a linux server. I can honestly not think of any downsides to running a server with a linux operating system. These Guides also assume you have a 32bit version installed.

Deb Based Distributions of Linux

rAthena Installation Guide for Debian/Ubuntu/Knoppix/DSL/and Other DEB based Distro's Other Distro's are only applicable if they have APT-GET or Aptitude installed.

APT-GET - and - Aptitude

can be used in place of the other should you so choose but for the purposes of this guide and my own personal preference I choose to use apt-get

For Debian/Knoppix/and Other Distro's not including Ubuntu it may be necessary to substitute

sudo - for - su

To everyone who is running their Linux with a GUI (Graphical User Interface) I would recommend that you not get too attached to it since we will be using the Terminal/CLI (Command Line Interface). I will give instruction for install a MySQL 5.0 Server at the end. Necessary Programs

Required packages
-----------------

  [git]: http://packages.debian.org/stable/git
  [make]: http://packages.debian.org/stable/make
  [gcc]: http://packages.debian.org/stable/gcc
  [libmysqlclient-dev]: http://packages.debian.org/stable/libmysqlclient-dev
  [zlib1g-dev]: http://packages.debian.org/stable/zlib1g-dev
  [libpcre3-dev]: http://packages.debian.org/stable/libpcre3-dev
  [PCRE]: PCRE "wikilink"
  [libssl-dev]: http://packages.debian.org/stable/libssl-dev
  [`https://github.com/rathena/rathena.git`]: https://github.com/rathena/rathena.git
  [this section]: Transition_from_SVN_to_GIT#Notes_about_GIT "wikilink"

`[root]# apt-get install git make gcc libmysqlclient-dev zlib1g-dev libpcre3-dev`

### Cloning The Repository

You can obtain the latest version of rAthena by typing the following command. This will place rAthena in a folder called rAthena, but you are free to change it to whatever you like:

`git clone `[`https://github.com/rathena/rathena.git`][]` ~/rAthena`

#### Updating Existing Code

To pull the latest updates for rAthena you can do the following:

`git pull`

Please [this section][] if you're having issues with updating.

### Run configure script

### Compile

` make sql`
` chmod a+x login-server && chmod a+x char-server && chmod a+x map-server`

#### How to Recompile

Recompiling is the same as compiling except you always run this command after you configure it

` make clean sql`

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

MYSQL Installation
------------------

You may need to run a a distribution upgrade just in case you will be running your mysql in the same vps/dedicated server. To do so you may run the command line:

    apt-get dist-upgrade

After getting the upgrade done you may now install the mysql server, to do so:

    apt-get install mysql-server

You will be prompted with a blue screen asking for your Administration password, please note that you must use a secure password since this will be your root sql password. Once done you may need to check if your mysql server is running. To do so you can:

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