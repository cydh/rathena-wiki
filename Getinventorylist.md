---
title: Getinventorylist
permalink: /Getinventorylist/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [getinventorylist](/getinventorylist "wikilink");

Description
-----------

This command sets a bunch of arrays with a complete list of whatever the invoking character has in their inventory, including all the data needed to recreate these items perfectly if they are destroyed. Here's what you get:

Return Values
-------------

| Value                         | Description                                                 |
|-------------------------------|-------------------------------------------------------------|
| @inventorylist_id\[\]        | array of item ids.                                          |
| @inventorylist_amount\[\]    | their corresponding item amounts.                           |
| @inventorylist_equip\[\]     | whether the item is equipped or not.                        |
| @inventorylist_refine\[\]    | for how much it is refined.                                 |
| @inventorylist_identify\[\]  | whether it is identified.                                   |
| @inventorylist_attribute\[\] | whether it is broken.                                       |
| @inventorylist_card1\[\]     | These four arrays contain card data for the items.          |
| @inventorylist_card2\[\]     | These data slots are also used to store names               |
| @inventorylist_card3\[\]     | inscribed on the items, so you can explicitly check         |
| @inventorylist_card4\[\]     | if the character owns an item made by a specific craftsman. |
| @inventorylist_expire\[\]    | expire time (Unix time stamp). 0 means never expires.       |
| @inventorylist_count         | the number of items in these lists.                         |

Notes
-----

This could be handy to save/restore a character's inventory, since no other command returns such a complete set of data, and could also be the only way to correctly handle an NPC trader for carded and named items who could resell them - since NPC objects cannot own items, so they have to store item data in variables and recreate the items.

Notice that the variables this command generates are all local and numeric.

**Be careful to use @inventorylist_count instead of getarraysize(@inventorylist_id), because the array doesn't get cleared before the execution of getinventorylist... so it could contain old data at indexes higher than @inventorylist_count.**

Examples
--------

        getinventorylist;
        for(set .@i,0; .@i < getarraysize(@inventorylist_id); .@i++){
            if(@inventorylist_id[.@i] == 512){ // 512 is the item id for apple
                mes "You have an apple with you!";
                close;
            }
        }
        mes "You don't have an apple with you :(";
        close;