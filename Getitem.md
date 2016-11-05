---
title: Getitem
permalink: /Getitem/
---

Syntax
------

-   [getitem](/getitem "wikilink") <item id>,<amount>{,<account ID>};
-   [getitem](/getitem "wikilink") "<item name>",<amount>{,<account ID>};

Description
-----------

This command will give a specific amount of specified items to the target character. If the character is not online, nothing will happen. If <character ID> is not specified, items will be created in the invoking character inventory instead.

In the first and most commonly used version of this command, items are referred to by their database ID number found inside .

Giving an item ID of -1 will give a specified number of random items from the list of those that fall out of Old Blue Box. Unlike in all other cases, these will be unidentified, if they turn out to be equipment. This is exactly what's written in the Old Blue Box's item script.

Other negative IDs also correspond to other random item generating item tables:

Giving an item ID of -2 will produce the effects of Old Violet Box. Giving an item ID of -3 will produce the effects of Old Card Album. Giving an item ID of -4 will produce the effects of Gift Box. Giving an item ID of -5 will produce the effects of Worn Out Scroll, which, in current SVN, drops only Jellopies anyway.

This transaction is logged if the log script generated transactions option is enabled.

You may also create an item by it's name in the 'english name' field in the item database:

Which will do what you'd expect. If it can't find that name in the database, apples will be created anyway. It is often a VERY GOOD IDEA to use it like this.

This is used in pretty much all NPC scripts that have to do with items and quite a few item scripts. For more examples check just about any official script.

Examples
--------

`getitem 502,10; // The person will receive 10 apples`
`getitem 617,1;  // The person will receive 1 Old Violet Box`
`getitem "RED_POTION",10;`

See Also
--------

-   [getitem2](/getitem2 "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")