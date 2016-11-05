---
title: Getgroupitem
permalink: /Getgroupitem/
---

Syntax
------

-   [getgroupitem](/getgroupitem "wikilink") <group_id>;

Description
-----------

Gives item(s) to the attached player based on item group contents, usage of this script command for getting items from groups that listed in [Item Package](https://github.com/rathena/rathena/blob/master/db/re/item_packages.txt). This is not working like 'getrandgroupitem' which only give 1 item for specified item group.

For contants, see the "Item Group ID" section in 'db/const.txt'.

More info can be found on [Item Group Documentation](https://github.com/rathena/rathena/blob/master/doc/item_group.txt)

Examples
--------

### Item Group List

`IG_MyItemGroup,Knife,0,1,0 //a "must" item`
`IG_MyItemGroup,Dagger,0,1,0 //a "must" item`
`IG_MyItemGroup,Stiletto,5,1,1 //random at group 1`
`IG_MyItemGroup,Stiletto_,2,1,1 //random at group 1`
`IG_MyItemGroup,Stiletto,5,1,2 //random at group 2`
`IG_MyItemGroup,Dagger_,4,1,2 //random at group 2`

### Script Command Usage

`getgroupitem(IG_MyItemGroup);`

-   Player always gets 1x Knife and 1x Dagger
-   Player has chance to get 1x Stiletto by chance 5/7 from group 1
-   Player has chance to get 1x Stiletto_ by chance 2/7 from group 1
-   Player has chance to get 1x Stiletto by chance 5/9 from group 2
-   Player has chance to get 1x Dagger_ by chance 4/9 from group 2

See also
--------

-   [Item Group](/Item_Group "wikilink")
-   [getrandgroupitem](/getrandgroupitem "wikilink")
-   [groupranditem](/groupranditem "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")