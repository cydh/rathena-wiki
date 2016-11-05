---
title: Map addflooritem
permalink: /Map_addflooritem/
---

Syntax
------

`int `**`map_addflooritem`**`(struct item *item_data,int amount,int m,int x,int y,int first_charid,int second_charid,int third_charid,int flags);`

==Parameters==

-   **item_data** - Item data.
-   **amount** - Amount of itens that will be added.
-   **m** - Map id, it's possible to get this id using [map_mapname2mapid](/map_mapname2mapid "wikilink")(const char\* name).
-   **x** - X coordinate.
-   **y** - Y coordinate.
-   **first_charid** - First character that will be able to pick the item up (ID)(MVP System).
-   **second_charid** - Second character that will be able to pick the item up (ID)(MVP System).
-   **third_charid** - Third character that will be able to pick the item up (ID)(MVP System).
-   **flags** -


0 - No flag.

&1 - MVP Item.

&2 - Do stacking check.

==Description== Makes an item appear on the ground using [clif_dropflooritem](/clif_dropflooritem "wikilink").
Returns 0 if something is wrong or item id if the item was added successfully.
==Example==

`map_addflooritem(&item_tmp,1,sd->bl.m,sd->bl.x,sd->bl.y,0,0,0,0);`

A item would appear on the floor in the player's location.
[Category:Source_Functions](/Category:Source_Functions "wikilink")