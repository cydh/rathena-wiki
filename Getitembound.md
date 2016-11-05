---
title: Getitembound
permalink: /Getitembound/
---

Syntax
------

`getitembound `<item id>`,`<amount>`,`<bound type>`{,`<account ID>`};`
`getitembound "`<item name>`",`<amount>`,`<bound type>`{,`<account ID>`};`

Description
-----------

This command behaves identically to [getitem](/getitem "wikilink"), but the items created will be bound to the target character as specified by the bound type. All items created in this manner cannot be dropped, sold, vended, auctioned, or mailed, and in some cases cannot be traded or stored.

Valid bound types are:

`Bound_Account : Account Bound item`
`Bound_Guild   : Guild Bound item`
`Bound_Party   : Party Bound item`
`Bound_Char    : Character Bound item`

Examples
--------

Give the item Jellopy (item ID: 909) to the player, and make it account-bound:

`getitembound 909,1,Bound_Account;`
`getitembound "Jellopy",1,Bound_Account;`

See Also
--------

-   [getitembound2](/getitembound2 "wikilink")
-   [Item Restrictions](/Custom_Items#Item_Restrictions "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")