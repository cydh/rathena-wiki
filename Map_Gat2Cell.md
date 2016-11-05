---
title: Map Gat2Cell
permalink: /Map_Gat2Cell/
---

Function to return struct mapcell for gat cell type
---------------------------------------------------

`static struct mapcell map_gat2cell(int gat)`
`map_gat2cell(gat);`

-   gat = cell type

Notes:

-   gat = 0 (walkable and shootoverable ground and not water)(normal ground)
-   gat = 1 (not walkable and not shootoverable ground and not water)(wall)
-   gat = 3 (walkable and shootoverable ground and water)
-   gat = 5 (not walkable and shootoverable ground and not water)

[Category:Source_Functions](/Category:Source_Functions "wikilink")