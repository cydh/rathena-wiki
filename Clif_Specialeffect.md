---
title: Clif Specialeffect
permalink: /Clif_Specialeffect/
---

Syntax
------

`int `**`clif_specialeffect`**`(struct block_list* bl, int type, enum send_target target);`

Parameters
----------

-   **bl** - Pointer to a block list, which identifies the game object, on which the effect is shown.
-   **type** - Indicates, which effect shown (see EF_\* constants in db/const.txt for all possible values or doc/effect_list.txt for a description of each effect).
-   **target** - Range of clients to show this effect on (look for ALL_CLIENT in clif.h or db/const.txt for all possible values).

Description
-----------

Notifies clients that an effect should be displayed on bl. Causes each client to display a visual effect usually centered on the game object identified by bl.

Example
-------

`clif_specialeffect(&sd->bl, 11, AREA_WOS);`

This would show the Endure skill visual effect on given player for everyone in his or her range, except the player him- or herself.

[Category:Source_Functions](/Category:Source_Functions "wikilink")