---
title: Strcharinfo
permalink: /Strcharinfo/
---

Syntax
------

-   [strcharinfo](/strcharinfo "wikilink")(<type>);

Description
-----------

This function will return either the name, party name or guild name for the invoking character. Whatever it returns is determined by type.

If a character is not a member of any party or guild, an empty string will be returned when requesting that information.

Type Values
-----------

| Value | Description                              |
|-------|------------------------------------------|
| 0     | Character's name.                        |
| 1     | The name of the party they're in if any. |
| 2     | The name of the guild they're in if any. |
| 3     | The name of the map where the player is. |

Examples
--------

[`mes`](/mes "wikilink")` "Hi " + `[`strcharinfo`](/strcharinfo "wikilink")`(0) + ", nice to meet you :)";`
[`if`](/if "wikilink")` (`[`getcharid`](/getcharid "wikilink")`(1))`
`   mes "Your party name is " + strcharinfo(1);`
`if (getcharid(2))`
`   mes "Your guild name is " + strcharinfo(2);`
`mes "You are standing on the map " + strcharinfo(3) + ".";`

[Category:Script Command](/Category:Script_Command "wikilink")