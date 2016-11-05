---
title: Checkweight
permalink: /Checkweight/
---

Syntax
------

-   [checkweight](/checkweight "wikilink")(<item id>,<amount>{,<item id>,<amount>,<item id>,<amount>,...});
-   [checkweight](/checkweight "wikilink")("<item name>",<amount>{,"<item name>",<amount>,"<item name>",<amount>,...});
-   **checkweight2**(<id_array>,<amount_array>);

Description
-----------

These functions will compute and return 1 if the total weight of the specified number of specific items does not exceed the invoking character's carrying capacity, and 0 otherwise. It is important to see if a player can carry the items you expect to give them, failing to do that may open your script up to abuse or create some very unfair errors.

The second function will check an array of items and amounts, and also returns 1 on success and 0 on failure.

The functions, in addition to checking to see if the player is capable of holding a set amount of items, also ensure the player has room in their inventory for the item(s) they will be receiving.

If multiple items are involved, it is best to use **checkweight2**, since it can check for all the elements stored in an array. Refer to the last [example](/Checkweight#Examples "wikilink").

Like '[getitem](/getitem "wikilink")', this function will also accept an 'english name' from the database as an argument.

Return Values
-------------

| Value | Description                                                  |
|-------|--------------------------------------------------------------|
| 0     | Return if the player does exceed his/her carrying limit.     |
| 1     | Return if the player does not exceed his/her carrying limit. |

Examples
--------

[`if`](/if "wikilink")` (`[`checkweight`](/checkweight "wikilink")`(512,10)) {`
`   `[`getitem`](/getitem "wikilink")` 512,10;`
`} `[`else`](/else "wikilink")` {`
`   `[`mes`](/mes "wikilink")` "Sorry you cannot hold this amount of apples";`
`}`
[`close`](/close "wikilink")`;`

Or to put this another way:

[`if`](/if "wikilink")` (`[`checkweight`](/checkweight "wikilink")`("Apple",10) == 0) {`
`   `[`mes`](/mes "wikilink")` "Sorry you cannot hold this amount of apples";`
`} `[`else`](/else "wikilink")` {`
`   `[`getitem`](/getitem "wikilink")` 512,10;`
`}`
[`close`](/close "wikilink")`;`

Both examples have the same effect.

Since r19841:

[`if`](/if "wikilink")` (!`[`checkweight`](/checkweight "wikilink")`(512,10,513,5)) { `[`mes`](/mes "wikilink")` "Sorry you cannot hold this amount of apples and banana";`

`setarray .@items[0],512,513;`
`setarray .@qtys[0],10,5;`
[`if`](/if "wikilink")` (!`**`checkweight2`**`(.@items,.@qtys)) { `[`mes`](/mes "wikilink")` "Sorry you cannot hold this amount of apples and banana";`

[Category:Script Command](/Category:Script_Command "wikilink")