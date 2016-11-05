---
title: Skilleffect
permalink: /Skilleffect/
---

Syntax
------

-   [skilleffect](/skilleffect "wikilink") <skill id>,<number>;
-   [skilleffect](/skilleffect "wikilink") "<skill name>",<number>;

Description
-----------

This command displays visual and aural effects of given skill on [currently attached character](/RID "wikilink"). The number parameter is for skill whose visual effect involves displaying of a number (healing or damaging). Note, that this command will not actually use the skill, it is intended for scripts, which simulate skill usage by the [NPC](/NPC "wikilink"), such as buffs, by setting appropriate status and displaying the skill's effect.

Examples
--------

[`mes`](/mes "wikilink")` "Be blessed!";`
`// Heal of 2000 HP`
[`heal`](/heal "wikilink")` 2000,0;`
[`skilleffect`](/skilleffect "wikilink")` 28,2000;`
`// Blessing Level 10`
[`sc_start`](/sc_start "wikilink")` 10,240000,10;`
[`skilleffect`](/skilleffect "wikilink")` 34,0;`
`// Increase AGI Level 5`
[`sc_start`](/sc_start "wikilink")` 12,140000,5;`
[`skilleffect`](/skilleffect "wikilink")` 29,0;`

This will heal the character with 2000 HP, buff it with Blessing Lv 10 and Increase AGI Lv 5, and display appropriate effects.

[Category:Script Command](/Category:Script_Command "wikilink")