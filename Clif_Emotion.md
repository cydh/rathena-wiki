---
title: Clif Emotion
permalink: /Clif_Emotion/
---

Syntax
------

`void `**`clif_emotion`**`(struct block_list *bl,int type);`

Parameters
----------

-   **bl** - Pointer to a block list, which identifies the game object, which shows the emotion.
-   **type** - Indicates, which emotion the game object uses (see e_\* constants in db/const.txt for all possible values).

Description
-----------

Notifies all clients in bl's area (including bl itself, if it identifies a player), that bl is using an emotion. Causes each client to display an emotion above bl's head, depending on type.

Example
-------

`clif_emotion(&sd->bl, 9);`

This would show a (...) emotion above the head of given player. All players in his or her vicinity would be able to see this as well.

[Category:Source_Functions](/Category:Source_Functions "wikilink")