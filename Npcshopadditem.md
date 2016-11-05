---
title: Npcshopadditem
permalink: /Npcshopadditem/
---

Syntax
------

-   **npcshopadditem** "<name>",<item id>,<price>{,<item id>,<price>{,<item id>,<price>{,...}}};

== Description == This command will add more items at the end of the selling list for the specified npc shop. If you specify an item already for sell, that item will appear twice on the sell list.

The function returns 1 if shop was updated successfully, or 0 if not found. Also take note that you cannot use -1 to specify default selling price.