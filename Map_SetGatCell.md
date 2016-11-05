---
title: Map SetGatCell
permalink: /Map_SetGatCell/
---

Function to change gat cell type
--------------------------------

`void map_setgatcell(int m, int x, int y, int gat)`
`map_setgatcell(m,x,y,gat);`

-   m = Map ID number
-   x = x corrdinate of cell
-   y = y corrdinate of cell
-   gat = type of cell to change to

Notes:

-   gat = 0 (walkable and shootoverable ground and not water)(normal ground)
-   gat = 1 (not walkable and not shootoverable ground and not water)(wall)
-   gat = 3 (walkable and shootoverable ground and water)
-   gat = 5 (not walkable and shootoverable ground and not water)

[Category:Source_Functions](/Category:Source_Functions "wikilink")