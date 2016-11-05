---
title: Isequippedcnt
permalink: /Isequippedcnt/
---

Syntax
------

-   **isequippedcnt**(<card id>{,<card id>{,<card id>{,<card id>}}})

Description
-----------

This function is similar to [isequipped](/isequipped "wikilink"), but instead of 1 or 0, it will return the number of cards in the list given that were found on the invoking character.

If a given parameter is not a card, the function returns the amount of that item equipped on the invoking character.

Example
-------

[`if`](/if "wikilink")` (`**`isequippedcnt`**`(4001,4005,4033,4196)=4) `[`mes`](/mes "wikilink")` "Finally got all four poring cards?";`

[Category:Script Command](/Category:Script_Command "wikilink")