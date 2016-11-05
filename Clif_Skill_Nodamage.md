---
title: Clif Skill Nodamage
permalink: /Clif_Skill_Nodamage/
---

Syntax
------

`int `**`clif_skill_nodamage`**`(struct block_list* src, struct block_list* dst, int skill_id, int heal, int fail);`

Parameters
----------

-   **src** - Specifies the source object of the no-damage skill. Can be NULL.
-   **dst** - Specifies the skill affected (destination) object.
-   **skill_id** - ID of the skill to display.
-   **heal** - Heal value, if the skill effect displays HP or SP gain, otherwise skill level.
-   **fail** - Whether the skill failed or not.

Description
-----------

Displays a skill effect on *dst* from *src*, and is responsible for *screaming* the name by *src*, of a non-damaging skill. If used with incompatible skill, the *dst* object (ex. player) will only scream the name, but no effect will be shown, likewise if *fail* is set to 1. *heal* (skill level) of -1 will disable *src* from screaming the skill name.

Example
-------

`clif_skill_nodamage(&sd->bl, &tsd->bl, AL_HEAL, 12000, 0);`

Will make player *sd* scream 'Heal !!' and show a heal effect of 12,000 HP on player *tsd*.

[Category:Source Functions](/Category:Source_Functions "wikilink")