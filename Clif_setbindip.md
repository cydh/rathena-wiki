---
title: Clif setbindip
permalink: /Clif_setbindip/
---

Syntax
------

`void `**`clif_setbindip`**`(const char* ip);`

Parameters
----------

-   **ip** - New Map-Server's Bind Ip.

Description
-----------

Defines a Bind IP to the Map-Server.

Example
-------

`if (strcmpi(w1, "bind_ip") == 0)`
` clif_setbindip(w2);`

(From map.c in **int map_config_read(char \*cfgName)**)
A new Bind IP would be set for the Map-Server using a parameter from 'bind_ip'.
**Note that it's not secure to redefine any type of ip on the fly.**
[Category:Source_Functions](/Category:Source_Functions "wikilink")