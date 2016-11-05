---
title: OnBuyItem
permalink: /OnBuyItem/
---

Syntax
------

[OnBuyItem](/OnBuyItem "wikilink"):

Explanation
-----------

This special label triggers when a player buys an item.

It can be used with NPCs that require post-purchase [array](/array "wikilink") deletions or for aesthetic purposes, such as simply displaying zeny amounts.

Examples
--------

This will display a player's current zeny whenever they buy an item from any shop.

    -   script  zamt    -1,{

        OnBuyItem:
            dispbottom "You now have "+ Zeny +" zeny";
            end;

    }

[Category:Script Command](/Category:Script_Command "wikilink")