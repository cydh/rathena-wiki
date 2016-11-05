---
title: Clif charselectok
permalink: /Clif_charselectok/
---

Syntax
------

`int `**`clif_charselectok`**`(int id, uint8 ok);`

==Parameters==

-   **id** - Player's map_id
-   **ok** - Flag that will be sent to the client


1 - Ok

2 - Not ok

==Description== Reply from Char-Server
Tells the player if he can connect to the char-server to select a character.
*I tried to debug this function, but I couldn't reproduce the packet using 2011-03-15aRagexeRE, I'm not sure if this function is still beeing used.*
==Example==

`clif_charselectok(2000001, 1);`

The client of the player id 2000001 would be able to connect to select a character.
[Category:Source_Functions](/Category:Source_Functions "wikilink")