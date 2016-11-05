---
title: Clif setip
permalink: /Clif_setip/
---

Syntax
------

`int `**`clif_setip`**`(const char* ip);`

Parameters
----------

-   **ip** - New Map-Server's IP.

Description
-----------

Defines a IP to the Map-Server.

Example
-------

`if (strcmpi(w1, "map_ip") == 0)`
`  map_ip_set = clif_setip(w2);`

(From map.c in **int map_config_read(char \*cfgName)**)
A new IP would be set for the Map-Server using a parameter from 'map_ip'.
**Note that it's not secure to redefine any type of ip on the fly.**
[Category:Source_Functions](/Category:Source_Functions "wikilink")