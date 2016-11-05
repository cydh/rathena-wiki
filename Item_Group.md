---
title: Item Group
permalink: /Item_Group/
---

Description
-----------

An Item Group is a set of items that can be retrieved through the [getrandgroupitem](/getrandgroupitem "wikilink") and [getgroupitem](/getgroupitem "wikilink") script commands. An item's ID belonging to a group can also be retrieved using the [groupranditem](/groupranditem "wikilink") command. Examples of Item Groups include Old Blue Box, Old Purple Box, Old Card Album and Gift Box items.

All Item Groups are being read from or and . Available Item Group IDs can be found at under the *//Item Group ID* section.

Structure
---------

`GroupID,ItemID,Rate{,Amount,Random,isAnnounced,Duration,isNamed,isBound}`

-   **GroupID**: ID or name of the group if defined at const.txt
-   **ItemID**: Available item_id that will be obtained from this item group. Supports AegisName of the item.
-   **Rate**: Probability to get the item. This is not a percentage value, but is calculated as **Item's Rate**/**Total Group's Rate Value** chance.
-   **Amount**: Amount of item that will be obtained.
-   **Random**: The item group's sub group. If set to '0', the item will always be obtained. If *Rate* is also specified and *Random* is set to '0', the item will always be obtained and there is a chance to get the item again.
-   **isAnnounced**: If set to 1, it will be broadcasted to the server that the item has been obtained by the player.
-   **Duration**: Makes the item a rental item, and the given value determines the expiration time in minutes. Only use for non-stackable items (e.g., weapons, armors).
-   **isNamed**: Inscribes the item with the obtainer's name.
-   **isBound**: Binds the obtained item. See [getitembound](/getitembound "wikilink") for valid bound types.

Custom Item Group
-----------------

To create a custom item group, create a text (.txt) file in the db/import folder using the structure specified above. For example, we create a file named item_customegg.txt with the following content:

`IG_CustomEgg1,Jellopy,1   // 1/6 chance`
`IG_CustomEgg1,910,2   // 2/6 chance`
`IG_CustomEgg1,911,3   // 3/6 chance`

Add the text file's location to import/item_group_db.txt. Using our previous example:

`import: db/import/item_customegg.txt`

Then, open db/const.txt and search for the *//Item Group ID* section. Add your custom Item Group at the bottom of the list, and use an ID based on the last number available:

`IG_Lucky_Silvervine_Fruit_Box_III10    420`
`IG_Lucky_Silvervine_Fruit_Box_III110   421`
**`IG_CustomEgg1` `422`**

Use @reloaditemdb to implement the changes. You can now use groupranditem, getrandgroupitem and getgroupitem commands to procure the items.

See also
--------

-   Item Group Documentation:

[Category:Database](/Category:Database "wikilink")