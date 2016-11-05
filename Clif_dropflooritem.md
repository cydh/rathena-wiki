---
title: Clif dropflooritem
permalink: /Clif_dropflooritem/
---

Syntax
------

`int `**`clif_dropflooritem`**`(struct flooritem_data *fitem);`

==Parameters==

-   **fitem** - Floor item data (usually defined in [map_addflooritem](/map_addflooritem "wikilink"))

==Description== Makes an item appear on the ground. Always return 0.
It's better to use [map_addflooritem](/map_addflooritem "wikilink") (map.c) to make an item apear, also that function already defines an object of flooritem_data.
==Example== See [map_addflooritem](/map_addflooritem "wikilink") (map.c).
[Category:Source_Functions](/Category:Source_Functions "wikilink")