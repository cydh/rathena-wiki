---
title: PC Search Inventory
permalink: /PC_Search_Inventory/
---

Check for a Item on Inventory/Equiped
-------------------------------------

`int pc_search_inventory(struct map_session_data *sd,int item_id)`

`pc_search_inventory(target,ItemID)`

-   Target
    -   sd = user
    -   bl = target
-   ItemID
    -   db/item_db.txt

Note: Can be used like this:

`if(pc_search_inventory(sd,501)>=10)`

This will check if the character has 10 or more Red Potions(501) on his inventory.

It is important that you understand that \*0\* is a valid return value. Therefore, if you're searching for items it is best you do it similarly:

`if ( (j = pc_search_inventory(sd, nameid)) >= 0 ) { etc; }`

[Category:Source_Functions](/Category:Source_Functions "wikilink")