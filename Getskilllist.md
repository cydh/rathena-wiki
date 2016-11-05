---
title: Getskilllist
permalink: /Getskilllist/
---

Syntax
------

-   [getskilllist](/getskilllist "wikilink");

Description
-----------

Retrieves a list of skills associated with the currently attached player. This command requires a player to be actively running or attached ([attachrid](/attachrid "wikilink")) to the script which calls this script command in order to obtain the list of skills and to be able to store the list within a selection of temporary character variables.

When used, this script command which store all the player skills in temporary character variables as follows:

-   @skilllist_id\[\] : an integer array holding all of the player skill IDs
-   @skilllist_lv\[\] : an integer array holding all of the player skill levels
-   @skilllist_flag\[\] : an integer array holding all of the player skill flags (See: [Skill](/skill#flag "wikilink"))
-   @skilllist_count : an integer variable holding the total number of skills stored

Examples
--------

`getskilllist;`
`for( `[`set`](/set "wikilink")` @i, 0; @skilllist_count > @i; `[`set`](/set "wikilink")` @i, @i + 1 )`
`{`
`     `[`mes`](/mes "wikilink")` "Skill #" + @skilllist_id[@i] + " is lv. " + @skilllist_lv[@i];`
`}`
[`close`](/close "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink")