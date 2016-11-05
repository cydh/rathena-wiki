---
title: Resetlvl
permalink: /Resetlvl/
---

Syntax
------

-   [resetlvl](/resetlvl "wikilink") <type>;
-   [resetlvl](/resetlvl "wikilink")(<type>);

Description
-----------

This is a character reset command, meant mostly for rebirth script supporting Advanced jobs, which will reset the invoking character's stats and level depending on the action type given. Valid action types are:

1.  Base level 1, Job level 1, 0 skill points, 0 base xp, 0 job xp, wipes the status effects, sets all stats to 1.
2.  Base level 1, Job level 1, 0 skill points, 0 XP/JXP. Skills and attribute values are not altered.
3.  Base level 1, base xp 0. Nothing else is changed.
4.  Job level 1, job xp 0. Nothing else is changed.

In all cases it will also unequip everything the character has on.

Examples
--------

[`resetlvl`](/resetlvl "wikilink")` 1;`
[`resetlvl`](/resetlvl "wikilink")`(1);`

[Category:Script Command](/Category:Script_Command "wikilink")