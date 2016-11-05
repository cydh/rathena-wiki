---
title: Statusup
permalink: /Statusup/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [statusup](/statusup "wikilink") <stat>;

Description
-----------

This command will bump a specified stat of the invoking character up by one permanently. Stats are to be given as number, but you can use these constants to replace them:

-   bStr - Strength
-   bVit - Vitality
-   bInt - Intelligence
-   bAgi - Agility
-   bDex - Dexterity
-   bLuk - Luck

Note: Only '[statusup](/statusup "wikilink")' and '[statusup2](/statusup2 "wikilink")' can modify the value of base stats, not '[set](/set "wikilink")'.

Examples
--------

     statusup bStr;       // Permanently adds 1 base strength w/o using statuspoints.
     set bStr, bStr+1;   // Will not function.  Might freeze NPC script.