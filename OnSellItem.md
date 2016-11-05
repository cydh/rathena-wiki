---
title: OnSellItem
permalink: /OnSellItem/
---

Syntax
------

[OnSellItem](/OnSellItem "wikilink"):

Explanation
-----------

This special label triggers when a player sells an item.

It can be used with NPCs that require post-selling [array](/array "wikilink") deletions or for aesthetic purposes, such as simply displaying zeny amounts.

Examples
--------

This will display a player's current zeny whenever they sell an item from any shop.

    -   script  zamt    -1,{

        OnSellItem:
            dispbottom "You now have "+ Zeny +" zeny";
            end;

    }

[Category:Script Command](/Category:Script_Command "wikilink")