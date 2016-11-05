---
title: Getstrlen
permalink: /Getstrlen/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [getstrlen](/getstrlen "wikilink")("<string>");

Description
-----------

This function will return the length of the string given as an argument. It is useful to check if anything input by the player exceeds name length limits and other length limits and asking them to try to input something else.

Examples
--------

        mes "The word 'Hello' has "+getstrlen("Hello")+" characters.";
        // output: The word 'Hello' has 5 characters.