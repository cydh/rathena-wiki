---
title: Setcart
permalink: /Setcart/
---

Syntax
------

-   [setcart](/setcart "wikilink") <type>;
-   **[checkcart](/checkcart "wikilink")**();

Description
-----------

If <type> is 0 this command will remove the cart from the character. Otherwise it gives the invoking character a cart. The cart given will be cart number <type> and will work regardless of whether the character is a merchant class or not.

Note: the character needs to have the skill MC_PUSHCART to gain a cart

Return Values
-------------

| Value | Description                        |
|-------|------------------------------------|
| 0     | The Character doesn't have a cart. |
| 1     | The Character has a cart.          |

Examples
--------

[`if`](/if "wikilink")`(`[`hasquest`](/hasquest "wikilink")`(50000))`
`   `[`if`](/if "wikilink")`(`**`checkcart`**`()) `[`mes`](/mes "wikilink")` "But you already have a cart!";`
`   `[`else`](/else "wikilink")` `[`setcart`](/setcart "wikilink")` 1;`

[Category:Script_Command](/Category:Script_Command "wikilink")