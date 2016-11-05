---
title: DynDNS Guide
permalink: /DynDNS_Guide/
---

Disclaimer
----------

This guide isn't meant to be a complete rAthena configuration guide, and it assumes you completed already the main configuration steps. If your server isn't working, please refer to the [Installation](/Installation "wikilink") and [:Category:Configuration](/:Category:Configuration "wikilink") guides before following this one.

In this guide will be shown how to configure your server to run with the DynDNS® service from [Dynamic Network Services, Inc.](http://dynamicnetworkservices.com/), but you can follow similar steps to setup it with any other Dynamic DNS service.
DynDNS® is registered trademarks of Dynamic Network Services Inc.

Requirements
------------

To follow this guide successfully, you will need:

-   A properly [installed](/Installation "wikilink") and [configured](/:Category:Configuration "wikilink") (including any port forwarding) rAthena. Either Linux or Windows version.
-   A [hexed Sakexe](/Hexing "wikilink") with the DNS Support option enabled.
-   Knowledge on how to create a [clientinfo.xml](/clientinfo.xml "wikilink") file.
-   Knowledge on how to obtain your LAN IP and Subnet mask.
-   Knowledge on how to install missing system packages (only in Linux)

Register an account
-------------------

Before setting up your server to use DunDNS, you need to register an account on [<http://www.dyndns.org>](http://www.dyndns.org). You'll find a "Create account" link near the top-right of their home page.

Fill the registration form as described in the following image, then follow the instructions you will get by email on how to activate your account:
[DynDNS account registration form](/Image:dysdns1.jpg "wikilink")

Go back to the DynDNS website and login with the new account you created.
It will show a list of actions you can perform. Choose "My Hosts", then "Add New Hostname". Fill the page as follows.
[DynDNS host creation form](/Image:dysdns2.jpg "wikilink")

Updater client
--------------

You can find an updater client for your OS in the DynDNS website. After you login, choose "Support" from the top menu, then "Update Clients" from the left menu.
Download either [DynDNS Updater (Windows)](http://www.dyndns.com/support/clients/windows.html) or [ddclient (Linux)](http://www.dyndns.com/support/clients/unix.html)

### Windows

**DynDNS Updater** You can refer to the official [DynDNS Updater Guide](https://www.dyndns.com/support/clients/dyndns-updater-guide.html#setup-install) to get help on the setup and configure steps.
Make sure you choose the "Install as a Service", "Show a Tray Icon" and "Start with Windows" options during the setup process.

### Linux

**ddclient**

#### Installation

If your Linux distribution offers the ddclient package in its own packages repository, install it with your favorite package manager (package name should be `ddclient`). Jump to the configuration section below.
Else, if your distribution doesn't provide any ddclient package, or you want to install the one on the DynDNS client, these are the steps to follow:

1.  Move the downloaded file (ddclient.tar.gz) to your home directory if you saved it anywhere else.
2.  Open a Console/Terminal and move to your home directory
    `$` `cd`
3.  Extract the downloaded tarball
    `$` `tar` `xzvf` `ddclient.tar.gz`
4.  Move to the extracted folder
    `$` `cd` `ddclient-*`
5.  Get root privileges (one of the following commands, depending on your distribution)
    `$` `sudo` `su`
    `$` `su`
6.  Copy the ddclient executable to the proper directory
    `#` `cp` `ddclient` `/usr/sbin/`
7.  Setup ddclient's startup script
    -   On gentoo:
        `#` `cp` `sample-etc_rc.d_init.d_ddclient` `/etc/init.d/ddclient`
        `#` `rc-config` `add` `ddclient` `default`
    -   On RedHat/Fedora/CentOS:
        `#` `cp` `sample-etc_rc.d_init.d_ddclient` `/etc/rc.d/init.d/ddclient`
        `#` `/sbin/chkconfig` `--add` `ddclient`
    -   On debian/\*ubuntu:
        `#` `cp` `sample-etc_rc.d_init.d_ddclient` `/etc/init.d/ddclient`
        `#` `update-rc.d` `ddclient` `defaults`
    -   On SuSE:
        `#` `cp` `sample-etc_rc.d_init.d_ddclient.lsb` `/etc/init.d/ddclient`
        `#` `insserv` `ddclient`
    -   On any other system:
        PM the [guide author](http://www.eathena.ws/board/index.php?act=Msg&CODE=4&MID=144476) asking for help with your \*nix distribution and it will get added to this list

8.  Create the config directory for the program
    `#` `mkdir` `/etc/ddclient`

#### Configuration

Configuration for ddclient is done through a text-format config file (`/etc/ddclient/ddclient.conf`)

1.  If you didn't do this yet, get root privileges (one of the following commands, depending on your distribution)
    `$` `sudo` `su`
    `$` `su`
2.  Open the config file in your favorite text editor (replace `vim` with the text editor you prefer)
    `#` `vim` `/etc/ddclient/ddclient.conf`
3.  Edit the below template to complete/write the config file:<code><nowiki>\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#
4.  Basic configuration file for ddclient
5.  6.  /etc/ddclient/ddclient.conf
    1.  1.

daemon=300 \# check every 300 seconds cache=/tmp/ddclient.cache pid=/var/run/ddclient.pid \# record PID in file. ssl=no \# use ssl-support. Works with ssl-library

use=web, web=checkip.dyndns.com/, web-skip='IP Address'

1.  1.  Replace Username with the username you used to register in the DynDNS website

login=Username

1.  1.  Replace Password with the password you used to register in the DynDNS website

password=Password

1.

protocol=dyndns2 server=members.dyndns.org wildcard=yes

1.  1.  Replace your-host-name.game-server.cc with the real host name you added to your DynDNS account

your-host-name.game-server.cc

1.

</nowiki></code>

1.  Start the ddclient updater
    -   On gentoo/debian/\*ubuntu/SuSE:
        `#` `/etc/init.d/ddclient` `start`
    -   On RedHat/Fedora/CentOS:
        `#` `/etc/rc.d/init.d/ddclient` `start`
    -   On any other system:
        PM the [guide author](http://www.eathena.ws/board/index.php?act=Msg&CODE=4&MID=144476) asking for help with your \*nix distribution and it will get added to this list

rAthena settings
----------------

You will need to configure rAthena properly in order to allow it to use the newly created DynDNS address.
Below are the required settings (use your favorite text editor to edit the files). Replace: `LAN_IP` with your LAN IP address, `DYNDNS_HOST` with your DynDNS Hostname and `SUBNET_MASK` with your LAN Subnet Mask.

-   `conf/login_athena.conf` `bind_ip:` `LAN_IP`
-   `conf/char_athena.conf` <code>login_ip: LAN_IP

bind_ip: LAN_IP char_ip: DYDNDNS_HOST</code>

-   `conf/map_athena.conf` <code>char_ip: LAN_IP

bind_ip: LAN_IP map_ip: DYNDNS_HOST</code>

-   `conf/subnet_athena.conf` `subnet:` `SUBNET_MASK:LAN_IP:LAN_IP`

Client settings
---------------

The client needs to be configured as well in order to let it connect through the DynDNS hostname. Edit the [clientinfo.xml](/clientinfo.xml "wikilink") file as follows:

-   Your client (the one you will use to connect from the same computer as the server or from the LAN)\[code\]
    <address>
    LAN_IP

    </address>
    \[/code\]

-   Normal client (the one you will give to players to connect from the Internet)\[code\]
    <address>
    DYNDNS_HOST

    </address>
    \[/code\]

Useful Links
------------

-   ["Installation Support" section in forums](http://rathena.org/board/forum/24-installation-support/) (Questions related to installation/setup issues)
-   ["rAthena Server Support" section in forums](http://rathena.org/board/forum/23-rathena-server-support/) (general support questions related to rAthena configuration)
-   ["Client & Patcher Support" section in forums](http://rathena.org/board/forum/19-client-patcher-support/) (for any issue with client, data folders and GRF packs)

[Category:Client Configuration](/Category:Client_Configuration "wikilink") [Category:Configuration](/Category:Configuration "wikilink")