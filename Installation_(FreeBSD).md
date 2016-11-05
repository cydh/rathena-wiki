---
title: Installation (FreeBSD)
permalink: /Installation_(FreeBSD)/
---

This article is aimed at installing and getting [rAthena](/rAthena "wikilink") to run successfully on a machine running [FreeBSD](/wikipedia:FreeBSD "wikilink") 7.1-RELEASE. It is assumed that FreeBSD was installed with the ports collection and enabled Linux Threading on install. This guide will NOT teach you how to network FreeBSD, install FreeBSD or configure any additional system settings (besides the ones needed to run rAthena and its dependancies).

Before we Start
===============

We will primarily working from the /home/user directory. Your primary user will need to be in the 'wheel' group and be able to su into root. Remember that I will include either $ or \#, depending on who you should be. $ indicates you should be your primary user, and \# indicates you should be root.

Required software
=================

We are going to use FreeBSD's ports collection to download, install and use most of these programs. It is assumed you already installed the ports collection, if you have not, I suggest you do that now.

wget
----

wget is Linux's download manager and is a very handy tool to have regardless of if we're going to use it. <code>

    # whereis wget
    wget: /usr/ports/www/wget
    # cd /usr/ports/www/wget && make && make install
    # make clean
    # rehash

</code>

gmake
-----

gmake, or GNUMake, is the GCC compiler used for FreeBSD. This is how we will create our binaries. <code>

     # whereis gmake
    gmake: /usr/ports/devel/gmake
    # cd /usr/ports/devel/gmake && make && make install
    # make clean
    # rehash

</code>

unrar
-----

unrar is a tool to unrar .rar's in BSD. <code>

     # whereis unrar
    unrar: /usr/ports/archivers/unrar
    $ cd /usr/ports/archivers/unrar
    $ make clean
    $ make install
    $ rehash

</code>

GCC
---

GCC is the GNU Compiler Collection and front ends for C, C++ and other languages. Chances are this will already be installed on the machine, but if not, here's what we do: <code>

    # wget http://www.netgull.com/gnu/gcc/gcc-###.tar.gz (Where ## is the version number. visit the mirror to find out)
    # tar -xvf gcc-###.tar.gz
    # cd gcc*
    # make && make install
    # make clean
    # rehash

</code>

gdb
---

GDB is always handy to have on a development machine, as it can take backtraces of crashes and lay them out for you to see what went wrong. chances are, this will also be installed with FreeBSD, but if it's not, here's how we will install it: <code>

    # wget http://ftp.gnu.org/gnu/gdb/gdb-###.tar.gz (again, where ### is the version number, check out the mirror)
    # tar -xvf gdb-###.tar.gz
    # cd gdb*
    # make && make install
    # make clean
    # rehash

</code>

git
---

[Git](https://github.com/rathena/rathena) is the versioning system used for rAthena and how we will get our copy of rAthena. <code>

    # whereis git
    git: /usr/ports/devel/git
    # cd /usr/ports/devel/git && make && make install
    # make clean
    # rehash

</code>

Now, let's go ahead and download rAthena. We'll use git for this.

    $ su root
    # adduser //create a rathena user
    # exit
    $ su rathena
    $ cd /home/rathena
    $ git clone https://github.com/rathena/rathena.git rathena
    $

Now, we can populate the tables with the .sql files in rAthena. Navigate to your /sql-files/ folder in the rAthena files you just checked out.

    $ cd /home/rathena/rathena/sql-files
    $ mysql -uuser -ppassword ragnarok < main.sql
    $ mysql -uuser -ppassword ragnarok < logs.sql

Now, you'll want to follow the steps in the [:Category:Configuration](/:Category:Configuration "wikilink") and [Connecting](/Connecting "wikilink") pages to get your rAthena configured. Once you've made all your source changes, you can compile rAthena. While you're in the root of your rAthena folder, issue the following commands to compile your server:

    $ ./configure
    $ gmake clean
    $ gmake server
    $ rehash

**Important Note:** If you are using a 32 bit FreeBSD you have to use

    $ ./configure --disable-64bit

instead

*NOTE:* You should **NEVER** run rAthena as root! This is why you should have setup a new user and this is why you've assigned him/her permissions in the /home/rathena/rathena/ directory! NB : It's better to compile as user instead of root as you wont have permision to alter output file.

And to start your servers, you can simply use the following command:

    $ ./athena-start <command> (start | stop | restart | status)

And that should be it! You should now have a running rAthena on your FreeBSD machine!

[Category:Installation Guides](/Category:Installation_Guides "wikilink")