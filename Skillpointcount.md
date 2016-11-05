---
title: Skillpointcount
permalink: /Skillpointcount/
---

Syntax
------

-   [skillpointcount](/skillpointcount "wikilink")()

Description
-----------

Returns the total amount of skill points a character possesses (SkillPoint+SP's used in skills). This command can be used to check the currently attached characters total amount of skill points. This means the skill points used in skill are counted, and added to SkillPoints (number of skill points not used).

Examples
--------

`//This will set the temp character variable .@skillPoints to the amount of skill points,`
`//and then tell the player the value.`
`   `[`set`](/set "wikilink")` .@skillPoints, `[`skillpointcount`](/skillpointcount "wikilink")`();`
`   `[`mes`](/mes "wikilink")` "You have "+ .@skillPoints +" skill points in total!";`
`   `
`//Self-explanatory... :P`
`   `[`if`](/if "wikilink")` (`[`skillpointcount`](/skillpointcount "wikilink")`() > 20)`
`       `[`mes`](/mes "wikilink")` "Wow, you have more then 20 Skill Points in total!";`

[Category:Script Command](/Category:Script_Command "wikilink")