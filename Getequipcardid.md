---
title: Getequipcardid
permalink: /Getequipcardid/
---

Syntax
------

-   [getequipcardid](/getequipcardid "wikilink")(<equipment position>,<card slot>)

Description
-----------

Returns value from equipped item slot in the indicated slot.

-   equipment position = any of the **EQI_** constants in
-   card slot = 0,1,2,3 (Card Slot N)

Examples
--------

This function returns 255, 254, -255 (for card 0, if the item is produced). It's useful when you want to check item cards or if it's [signed](/getnameditem "wikilink"). Useful for such quests as "Sign this refined item with players name" etc.

[Category:Script Command](/Category:Script_Command "wikilink")