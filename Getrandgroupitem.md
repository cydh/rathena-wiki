---
title: Getrandgroupitem
permalink: /Getrandgroupitem/
---

Syntax
------

-   [getrandgroupitem](/getrandgroupitem "wikilink") <group id>,<quantity>{,<sub_group>};

Description
-----------

Similar like [groupranditem](/groupranditem "wikilink"), this command allows players to obtain the specified quantity of a random item from the group "<group id>". The different groups and their group number are specified in db/(pre-)re/item_group_db.txt

For example, obtaining three of the same random item from Old Blue Box:

`getrandgroupitem(1,3);`
`getrandgroupitem(IG_BlueBox,3); //see const.txt at 'Item Group ID' section`

If quantity is 0, and if the item(s) at specified IG_ has defined amount, the amount of the item that will be obtained, will according to the amount on that IG_ data.

By default, if getrandgroupitem is used to get random item from IG_ which has more than defined random group, it always read random group 1, other item that as random item at random group &gt; 2 never been touched. Use 'sub_group' to choose which random group will be obtained.

Examples
--------

### Item Group List

`IG_ExGetGroupItem,Coat,2,2,1`
`IG_ExGetGroupItem,Muffler,2,3,1`
`IG_ExGetGroupItem,Yggdrasilberry,10,7,1`
`IG_ExGetGroupItem,Yggdrasilberry,10,7,2`
`IG_ExGetGroupItem,Seed_Of_Yggdrasil,5,15,2`

### Script Command Usage

`'getrandgroupitem(IG_ExGetGroupItem,1)'`

-   Player has chance to get 1x Coat or 1x Muffler or 1x Yggdrasilberry. Player never has chance to get Seed_of_Yggdrasil because it is in different random group.

`'getrandgroupitem(IG_ExGetGroupItem,0)'`

-   Player has chance to get 2x Coat or 3x Muffler or 7x Yggdrasilberry. Player never has chance to get Seed_of_Yggdrasil because it is in different random group.

`'getrandgroupitem(IG_ExGetGroupItem,0,2)'`

-   Player has chance to get 10x Yggdrasilberry or 15x Seed_of_Yggdrasil. Player never has chance to get Coat, Muffler, and Yggdrasilberry because it is in different random group.

See also
--------

-   [Item Group](/Item_Group "wikilink")
-   [getgroupitem](/getgroupitem "wikilink")
-   [groupranditem](/groupranditem "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")