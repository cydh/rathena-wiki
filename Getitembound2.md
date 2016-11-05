---
title: Getitembound2
permalink: /Getitembound2/
---

Syntax
------

-   **getitembound2** <item id>,<amount>,<identify>,<refine>,<attribute>,<card1>,<card2>,<card3>,<card4>,<bound type>{,<account ID>};
-   **getitembound2** "<item name>",<amount>,<identify>,<refine>,<attribute>,<card1>,<card2>,<card3>,<card4>,<bound type>{,<account ID>};

Description
-----------

This command behaves identically to 'getitem2', but the items created will be bound to the target character as specified by the bound type. All items created in this manner cannot be dropped, sold, vended, auctioned, or mailed, and in some cases cannot be traded or stored.

Valid bound types are:

`Bound_Account : Account Bound item`
`Bound_Guild   : Guild Bound item`
`Bound_Party   : Party Bound item`
`Bound_Char    : Character Bound item`