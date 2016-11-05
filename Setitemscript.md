---
title: Setitemscript
permalink: /Setitemscript/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   setitemscript(<ItemID>,&lt;"{ new item script }"&gt;{,<flag>});

Description
-----------

Set a new script bonus to the Item. Very useful for game events. You can remove an item's itemscript by leaving empty the itemscript argument.

Parameters
----------

### Flag

Denotes which script of the item to modify. Default value is 0

| Flag | Script Type       |
|------|-------------------|
| 0    | Script            |
| 1    | On Equip Script   |
| 2    | On Unequip Script |

Examples
--------

    setitemscript 2637,"{ if(isequipped(2236)==0)end; if(getskilllv(26)){skill 40,1;}else{skill 26,1+isequipped(2636);} }";
    setitemscript 2639,"";