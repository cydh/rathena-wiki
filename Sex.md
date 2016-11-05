---
title: Sex
permalink: /Sex/
---

Syntax
------

-   **sex**

Description
-----------

**Sex** is a condition used to identify if the player is using a male or female character, depending the response the displayed dialogue can be altered, this however requires an [if](/if "wikilink") statement as it would else only returns an integer.

Upon using the condition **sex**, the server will return either the value 0 for female or 1 for male.

Examples
--------

` `[`if`](/if "wikilink")`(Sex) mes "Hello Sir"; else mes "Hello Mam";`
` //With a simple visible if statement`

` `[`mes`](/mes "wikilink")` "Welcome, " + (Sex?"Mr.":"Mrs.") + " " + `[`strcharinfo`](/strcharinfo "wikilink")`(0);`
` //Using it within a sentence structure and a hidden if statement`

[Category:Script_Command](/Category:Script_Command "wikilink")