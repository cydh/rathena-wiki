---
title: Getskilllv
permalink: /Getskilllv/
---

Syntax
------

-   **getskilllv**(<skill id>)
-   **getskilllv**("<skill name>")

Description
-----------

This function returns the level of the specified skill that the invoking character has. If they don't have the skill, 0 will be returned. The full list of character skills is available in or , depending on your renewal status.

Examples
--------

There are two main uses for this function, it can check whether the character has a skill or not, and it can tell you if the level is high enough.

Example 1:

`        if (`**`getskilllv`**`(152)) `[`goto`](/goto "wikilink")` L_HasSkillThrowStone;`
`        `[`mes`](/mes "wikilink")` "You don't have Throw Stone";`
`        close;`
`    L_HasSkillThrowStone:`
`        mes "You have got the skill Throw Stone";`
`        `[`close`](/close "wikilink")`;`

Example 2:

`       if (`**`getskilllv`**`(28) >= 5) goto L_HasSkillHeallvl5orMore;`
`       if (`**`getskilllv`**`(28) == 10) goto L_HasSkillHealMaxed;`
`       mes "You heal skill is below level 5";`
`       close;`
`   L_HasSkillHeallvl6orMore:`
`       mes "Your heal level is 5 or more";`
`       close;`
`   L_HasSkillHealMaxed:`
`       mes "Your heal level has been maxed";`
`       close;`

[Category:Script_Command](/Category:Script_Command "wikilink")