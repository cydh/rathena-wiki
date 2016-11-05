---
title: Delitem
permalink: /Delitem/
---

Syntax
------

-   **delitem** <item id>, <amount>\[, <account id>\];
-   **delitem** &lt;"item name"&gt;, <amount>\[, <account id>\];

Description
-----------

This command will take a specified amount of given item from the [invoking](/RID#Usage "wikilink") character. The items are destroyed - there is no way an [NPC](/NPC "wikilink") can simply own and have an inventory of items, other than by destroying and recreating them when needed.

Before items are deleted, the script should check, if the player has given amount of items. If there are not enough items, they are deleted anyway, but the script is terminated with an error then, to prevent exploits. If the specified item does not exist, nothing will be deleted, but the script is terminated with an error as well.

If *account id* is given, the items are deleted from the character, which is currently online on that account instead. If the player is not online, the script terminates.

Examples
--------

`delitem 502, 10;  // Orange_Potion`

Removes 10 Orange Poitions from currently attached character.

`delitem 617, 0, 2000110;  // Old_Violet_Box`

Removes 1 Old Violet Box from an online player on account 2000110.

[Category:Script Command](/Category:Script_Command "wikilink")