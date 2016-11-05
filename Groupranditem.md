---
title: Groupranditem
permalink: /Groupranditem/
---

Syntax
------

-   [groupranditem](/groupranditem "wikilink") <group id>{,<sub_group>};

Description
-----------

Returns the item_id of a random item picked from the group specified. The different groups are constructed in the db/ directory ( (or RE equivalent)).

'sub_group' is used to get the available random items of item group from specified random group. More info, just like the [getrandgroupitem](/getrandgroupitem "wikilink").

Examples
--------

When used in conjunction with other functions, you can get a random item.
For example, for a random pet lure:

[`getitem`](/getitem "wikilink")` `[`groupranditem`](/groupranditem "wikilink")`(15),1;`

Item script for Old Blue Box:
[getitem](/getitem "wikilink") [groupranditem](/groupranditem "wikilink")(IG_BlueBox),1;

This could translate to the following, as they both mean the same thing:
[getitem](/getitem "wikilink") [groupranditem](/groupranditem "wikilink")(1),1;

Or make everything random!

[`set`](/set "wikilink")` @groupid,`[`rand`](/rand "wikilink")`(1,62);`
[`set`](/set "wikilink")` @randvalue,`[`rand`](/rand "wikilink")`(1,999);`
[`getitem`](/getitem "wikilink")` `[`groupranditem`](/groupranditem "wikilink")`(@groupid),@randvalue;`
[`dispbottom`](/dispbottom "wikilink")` "You've been given a random amount of random items from a random item group.";`

See also
--------

-   [Item Group](/Item_Group "wikilink")
-   [getgroupitem](/getgroupitem "wikilink")
-   [getrandgroupitem](/getrandgroupitem "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")