---
title: Multiple servers
permalink: /Multiple_servers/
---

Description
===========

The first server is set up as usual
-----------------------------------

1.  IP address
2.  MySQL database(s)
3.  Ports

The second server
-----------------

1.  That the same IP address at all.
2.  Other base Sql. (to the login server is not required/login table will not used)
3.  Here the most interesting. Ports map and char server set different than the first server. A Login server port in all config files both on the first server. ie 6900.

Starting
--------

1.  Run entirely the first server.
2.  A second server that's run only Map and Char server. (recommendation: map_server_sql and char_server_sql set different name or you can accidentally kill first server)

As a result, we succeeded 2 servers (server selection appears after entering a username and password in the game)

Potential issues
----------------

-   With that settings an Autotrade-Merchant on Server A is kicked by the login-server when you login to Server B. Opportunity to correct this defect not yet known
-   If there is warp type script to warp player cross map-server, example you have Payon at map-server 2 and want because your map-server 1 doesn't have Payon, map-server 1 will try to warp player to map-server 2. This is will makes map-server 1 crashed (map-server that using warp script). This issue only if you try to warp player to other map-server by script, everything is OK by using atcommand or warp portal. For now, you can do tricky-trick first, devs are working on this.

Scheme
======

[native|center|alt=Servers Scheme|Servers Scheme](/File:Multiple_servers_scheme.png "wikilink")

[Category:Installation](/Category:Installation "wikilink")