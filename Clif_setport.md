---
title: Clif setport
permalink: /Clif_setport/
---

Syntax
------

`void `**`clif_setport`**`(uint16 port);`

Parameters
----------

-   **port** - New Map-Server's port.

Description
-----------

Defines a port to the Map-Server.

Example
-------

`if (strcmpi(w1, "map_port") == 0) {`
` clif_setport(atoi(w2));`
` map_port = (atoi(w2));`
`}`

(From map.c in **int map_config_read(char \*cfgName)**)
A new port would be set for the Map-Server using a parameter from 'map_port'.
**Note that it's not secure to redefine the port on the fly.**

[Category:Source_Functions](/Category:Source_Functions "wikilink")