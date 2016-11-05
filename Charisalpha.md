---
title: Charisalpha
permalink: /Charisalpha/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [charisalpha](/charisalpha "wikilink")("<string>",<position>);

Description
-----------

This function will return 1 if the character number Position in the given string is a letter, 0 if it isn't a letter but a digit or a space.

Examples
--------

    if(charisalpha("test 1234",2))
        mes "It's a letter!";
    else
        mes "It's not a letter... :(";