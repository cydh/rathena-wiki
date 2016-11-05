---
title: Changebase
permalink: /Changebase/
---

Syntax
------

-   **changebase** <job ID number>{,<account ID>};

Description
-----------

This will change the appearance of the invoking character, unless an account ID is given, to that of a specified job class. Nothing but appearance will change. This command is used in item scripts for "Wedding Dress" and "Tuxedo" so the character like job 22, which is the job number of the wedding sprites. It would be entered in the equip bonus section of an item.

Examples
--------

### In Items

`2338,Wedding_Dress,Wedding Dress,5,43000,,500,,0,,0,119529470,7,0,16,,0,1,0,{ `[`bonus`](/bonus "wikilink")` bMdef,15; changebase 22; }`

### In NPCs

[`mes`](/mes "wikilink")` "[Test NPC]";`
[`mes`](/mes "wikilink")` "Would you like to change your sprite?";`
[`if`](/if "wikilink")`(`[`select`](/select "wikilink")`("- Yeah, that'd be /AWSM!", "- No, wth are you on about?!") == 1)`
`   `[`mes`](/mes "wikilink")` "Excellent!";`
`   `[`mes`](/mes "wikilink")` "I will now make you look like a....";`
`   `[`changebase`](/changebase "wikilink")` 4072;`
`   `[`mes`](/mes "wikilink")` "^FF0000Shadow Chaser^000000!!";`
[`else`](/else "wikilink")
`   `[`mes`](/mes "wikilink")` "But but.. Shadow Chasers are /awsm T.T";`
[`close`](/close "wikilink")`;`

[Category:Script_Command](/Category:Script_Command "wikilink")