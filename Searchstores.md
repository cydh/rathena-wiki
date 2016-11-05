---
title: Searchstores
permalink: /Searchstores/
---

Syntax
------

-   **searchstores** <uses>,<effect>;

Description
-----------

Invokes the store search window, which allows to search for both vending and buying stores. Parameter uses indicates, how many searches can be started, before the window has to be reopened. Effect value affects, what happens, when a result item is double-clicked and can be one of the following:

-   0 = Shows the store's position on the mini-map and highlights the shop sign with yellow color, when the store is on same map as the invoking player.
-   1 = Directly opens the shop, regardless of distance.

Examples
--------

`searchstores 10,1;`

Item Universal_Catalog_Gold (10 uses, effect: open shop)

See Also
--------

-   [buyingstore](/buyingstore "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")