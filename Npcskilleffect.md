---
title: Npcskilleffect
permalink: /Npcskilleffect/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   **npcskilleffect** <skill id>,<number>,<x>,<y>;
-   **npcskilleffect** "<skill name>",<number>,<x>,<y>;

Description
-----------

This command behaves identically to '[skilleffect](/Skilleffect "wikilink")' however, the effect will not be centered on the invoking character's sprite, nor on the NPC sprite. It will be centered at map coordinates given on the same map as the invoking character.

Example
-------

Here are some samples which might be a help to you:

#### An example script using skill ID

`       mes "This will cast Skill ID 21 on map coordinates 143 180";`
`       npcskilleffect 21,10,143,180;`

#### An example script using skill name

`       mes "This will cast MG_THUNDERSTORM on map coordinates 143 180";`
`       npcskilleffect "MG_THUNGDERSTORM",10,143,180;`