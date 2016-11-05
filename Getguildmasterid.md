---
title: Getguildmasterid
permalink: /Getguildmasterid/
---

Syntax
------

-   [getguildmasterid](/getguildmasterid "wikilink")(<guild id>);

Description
-----------

This function will return the character ID number of the guild master of the guild specified by the ID. 0 if the character is not a guild master of any guild.

Examples
--------

<NPC Header>` {`
`   `[`set`](/set "wikilink")` .@guild_id, `[`getcharid`](/getcharid "wikilink")`(2);`
`   `[`if`](/if "wikilink")` (.@guild_id == 0) {`
`       `[`mes`](/mes "wikilink")` "You are not in a guild.";`
`   } `[`else`](/else "wikilink")` {`
`       `[`mes`](/mes "wikilink")` "Your Guild Master's char_id is:";`
`       `[`mes`](/mes "wikilink")` `[`getguildmasterid`](/getguildmasterid "wikilink")`(.@guild_id);`
`   }`
`   `[`close`](/close "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")