---
title: Getguildmaster
permalink: /Getguildmaster/
---

Syntax
------

-   [getguildmaster](/getguildmaster "wikilink")(<guild id>)

Description
-----------

This function return the name of the master of the guild which has the specified ID number. If there is no such guild, "null" will be returned.

Examples
--------

[`if`](/if "wikilink")` (`[`getcharid`](/getcharid "wikilink")`(2)) {`
`   `[`mes`](/mes "wikilink")` "Your guild master's name is:";`
`   `[`mes`](/mes "wikilink")` `[`getguildmaster`](/getguildmaster "wikilink")`(`[`getcharid`](/getcharid "wikilink")`(2));`
`} `[`else`](/else "wikilink")` {`
`   `[`mes`](/mes "wikilink")` "You are not in a guild.";`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")