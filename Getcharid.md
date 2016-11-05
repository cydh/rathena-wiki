---
title: Getcharid
permalink: /Getcharid/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [getcharid](/getcharid "wikilink")(<type>{,"<character name>"});

Description
-----------

This function will return a unique ID number of the invoking character, or, if a character name is specified, of that character.

For most purposes other than printing it, a number is better to have than a name (people do horrifying things to their character names).

If the character is not in a party or not in a guild, the function will return 0 if guild or party number is requested. If a name is specified and the character is not found, 0 is returned.

If [getcharid](/getcharid "wikilink")(0) returns a zero, the script got called not by a character and doesn't have an attached [RID](/RID "wikilink"). Note that this will cause the map server to print "player not attached!" error messages, so it is preferred to use '[playerattached](/playerattached "wikilink")' to check for the character attached to the script.

Type Values
-----------

| Value | Description             |
|-------|-------------------------|
| 0     | Character ID number.    |
| 1     | Party ID number.        |
| 2     | Guild ID number.        |
| 3     | Account ID number.      |
| 4     | Battleground ID number. |

Examples
--------

[`if`](/if "wikilink")`( `**`getcharid`**`(2) == 0 ) `[`mes`](/mes "wikilink")` "Only members of a guild are allowed here!";`