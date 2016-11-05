---
title: Equip
permalink: /Equip/
---

Syntax
------

-   [equip](/equip "wikilink") <item id>;
-   [autoEquip](/autoEquip "wikilink") <item id>,<option>;

Description
-----------

These commands are to equip a equipment on the attached character. The equip function will equip the item ID given when the player has this item in his/her inventory, while the autoequip function will equip the given item ID when this is looted. The option parameter of the autoequip is 1 or 0, 1 to turn it on, and 0 to turn it off.

Examples
--------

`// This will equip a 1104 (falchion) on the character if this is in the inventory.`
`equip 1104;`

`// The invoked character will now automatically equip a falchion when it's looted.`
`autoequip 1104,1;`
`// The invoked character will no longer automatically equip a falchion.`
`autoequip 1104,0;`

[Category:Script Command](/Category:Script_Command "wikilink")