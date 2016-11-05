---
title: PlayBGM
permalink: /PlayBGM/
---

Syntax
------

-   **playBGM** &lt;"file name"&gt;;
-   **playBGMall** &lt;"file name"&gt;, &lt;"map name"&gt;\[, <x0>, <y0>, <x1>, <y1>\];

Description
-----------

These commands change temporarily the background music for the [currently attached](/RID#Usage "wikilink") player or multiple players respectively. The parameter *file name* must specify a file, which is stored inside the BGM folder inside the RO folder. Both "BGM\\" before and ".mp3" after the file name can be omitted, the client adds these by itself, when necessary.

When **playBGMall** is given only *map name*, background music is changed for all players in given map, otherwise only in specified area.

Examples
--------

`playBGM "01";`

Changes the background music of the invoking player to the title music.

See Also
--------

-   [soundeffect](/soundeffect "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")