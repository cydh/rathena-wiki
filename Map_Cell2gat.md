---
title: Map Cell2gat
permalink: /Map_Cell2gat/
---

Function to return gat type of given cell
-----------------------------------------

`static int map_cell2gat(struct mapcell cell)`
`map_cell2gat(cell);`

-   cell = struct mapcell

Notes: will return one of the following numbers

-   0 (walkable and shootoverable ground and not water)(normal ground)
-   1 (not walkable and not shootoverable ground and not water)(wall)
-   3 (walkable and shootoverable ground and water)
-   5 (not walkable and shootoverable ground and not water)

[Category:Source_Functions](/Category:Source_Functions "wikilink")