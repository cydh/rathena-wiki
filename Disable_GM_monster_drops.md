---
title: Disable GM monster drops
permalink: /Disable_GM_monster_drops/
---

Introduction
------------

If your server has several GMs, it may be wise to disable monsters dropping items should they attack them. If you feel insecure about your GMs, it might be wise to implement this modification in order to limit how far they can use their GM abilities.

GMs may be able to warp to dungeons and warp around to actively seek MvPs, or may be able to cast many skills with few limitations. The optimum idea would be to disable them from doing this completely, however it restricts the commands the GMs can use. Instead, we can set a limit on what level GMs must be in order to receive drops.

Open /src/map/battle.h
----------------------

**Find:**

`   int bg_flee_penalty;`

*'Below add:*

`   int gm_monsterdrop_lv;`

Open /src/map/battle.c
----------------------

**Find:**

`   { "bg_flee_penalty",                    &battle_config.bg_flee_penalty,                 20,     0,      INT_MAX,        },`

**Below add:**

`   { "gm_monsterdrop_lv",                  &battle_config.gm_monsterdrop_lv,                0,     0,      99,        },`

Open /src/map/mob.c
-------------------

*Scroll to or find the function mob_db*

------------------------------------------------------------------------

**Find:**

`   if(src && src->type == BL_MOB)`
`       mob_unlocktarget((struct mob_data *)src,tick);`

**Below add:**

`   if( (mvp_sd && pc_isGM(mvp_sd)) || (sd && pc_isGM(sd)) )`
`   {`
`       if( mvp_sd && pc_isGM(mvp_sd) < battle_config.gm_monsterdrop_lv )`
`           type |= 1;`
`       else if( sd && pc_isGM(sd) < battle_config.gm_monsterdrop_lv )`
`           type |= 1;`
`   }`

Open /conf/battle/gm.conf
-------------------------

**Find:**

`// [GM] Can't be kicked from a chat? (No or mimimum GM level)`
`gm_kick_chat: no`

**Below add:**

`// [GM] Minimum GM level to receive drops from monsters (0 = disabled.)`
`gm_monsterdrop_lv: 40`

------------------------------------------------------------------------

*When set to 40, a GM must be **equal to or above** GM level 40 in order to receive drops.*

[Category:Source Snippets](/Category:Source_Snippets "wikilink")