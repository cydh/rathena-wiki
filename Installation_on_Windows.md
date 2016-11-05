---
title: Installation on Windows
permalink: /Installation_on_Windows/
---

Things You Will Need
====================

-   [TortoiseGIT](http://code.google.com/p/tortoisegit/)
-   [MySQL](http://www.mysql.com/downloads/mysql/)
-   [MySQL Workbench](http://www.mysql.com/downloads/workbench/)
-   [MSysGit](http://msysgit.github.io/)

GIT Clone
---------

***<big>Recommended to use Git Clone because [rAthena](https://github.com/rathena/rathena) is up-to-date</big>***

Compiling
---------

IP info
-------

Next let's get your IP info.

-   Windows XP

Click Start, then Run... type *cmd* and click OK. Type in *ipconfig* and press the Enter key. You should see something like this:

`Ethernet adapter Local Area Connection`
`Media State . . . . . . . . . . . : Media disconnected`
`Ethernet adapter Wireless Network Connection`
`Connection-specific DNS Suffix  . `
`IP Address. . . . . . . . . . . . : 192.xxx.x.x`
`Subnet Mask . . . . . . . . . . . : 255.255.255.0`
`Default Gateway . . . . . . . . . : 192.xxx.x.x`

-   Windows 7

Click Start and in the search box type *run* then type *cmd* and press then Enter key. Type in *ipconfig* and press the Enter key.

`Windows IP Configuration`
`Wireless LAN adapter Wireless Network Connection:`
`   Connection-specific DNS Suffix  . :`
`   Link-local IPv6 Address . . . . . : Gibberish`
`   IPv4 Address. . . . . . . . . . . : 192.xxx.x.xx < Your IP! (LAN IP)`
`   Subnet Mask . . . . . . . . . . . : 255.255.255.0`
`   Default Gateway . . . . . . . . . : 192.xxx.x.x`
`Ethernet adapter Local Area Connection:`
`   Media State . . . . . . . . . . . : Media disconnected`
`   Connection-specific DNS Suffix  . :`

In place of the x there will be numbers. Open notepad; go back to the console window and right-click it's window title and select option "Select..." then click and drag over your IP address (selection will appear in inverted colors), or just copy the whole thing. For Windows 7 you will need to right click the window with the text, and click mark; then click and drag. This IP address is known as your LAN IP. Next go to [whatismyip.net](http://www.whatismyip.net/) and take note of your IP address from there. This is your WAN IP, just for future reference to make it world-wide.

Conf Folder
-----------

Open char_athena.conf and map_athena.conf with notepad, wordpad, or your text editor of choice. If your LAN IP and WAN IP are same then put that one IP down for all of the IP locations. Char_athena: *login_ip* will be the LAN IP, *char_ip* will be WAN IP. Change *server_name* to the name you want your server to be. You can change *wisp_server_name* to what you would like it to be. *wisp_server_name* is the name that shows up when a character logs in and receives a PM about it being night. The rest of things that can be changed here will be explained later. Map_athena: *char_ip* is the LAN IP, *map_ip* is the WAN IP. Be sure to remove the // before each IP line. When you are done, it should look like this:

`// Character Server IP`
`// The map server connects to the character server using this IP address.`
`// NOTE: This is useful when you are running behind a firewall or are on`
`// a machine with multiple interfaces.`
`char_ip: 192.xxx.x.x < LAN IP`
`// The map server listens on the interface with this IP address.`
`// NOTE: This allows you to run multiple servers on multiple interfaces`
`// while using the same ports for each server.`
`//bind_ip: 127.0.0.1`
`// Character Server Port`
`char_port: 6121`
`// Map Server IP`
`// The IP address which clients will use to connect.`
`// Set this to what your server's public IP address is.`
`map_ip: 69.xxx.x.x < WAN IP`

Rename the import-tmpl folder to import. Leave the conf folder back to the main folder and rename save-tmpl to save.

After Installation
==================

After you have finished configuring at this point, you will need to setup the [MySQL server](/SQL_Installation "wikilink") that rAthena requires.
Once you have completed setting up your server, you may want to look at [Configuration](/:Category:Configuration "wikilink") and [Customization](/:Category:Customization "wikilink").

See Also
========

-   [SQL Installation](/SQL_Installation#For_Windows "wikilink")
-   [:Category:Configuration](/:Category:Configuration "wikilink")
-   [clientinfo.xml](/clientinfo.xml "wikilink")
-   [:Category:Data](/:Category:Data "wikilink")
-   [Custom Items](/Custom_Items "wikilink")
-   [Custom Mobs](/Custom_Mobs "wikilink")
-   [GIT Troubleshooting](/GIT_Troubleshooting "wikilink")

[Windows](/Category:Installation_Guides "wikilink")