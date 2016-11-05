---
title: Status Heal
permalink: /Status_Heal/
---

This function heals the target by some amount defined by HP or SP.
------------------------------------------------------------------

`int status_heal(struct block_list *bl,int hp,int sp, int flag)`

`status_heal(target, HP, SP, Flag);`

-   **target:**
    -   src - user
    -   bl - skill target
-   **HP:** - Amount healed in HP
-   **SP:** - Amount healed in SP
-   **Flag:**
    -   1 - Forced heal, there is no way to block (not even berserk)
    -   2 - Show the amount healed above your head

Note: 3 will be forced and show amount healed. [Category:Source_Functions](/Category:Source_Functions "wikilink")