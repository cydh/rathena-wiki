---
title: Adding new mapflag
permalink: /Adding_new_mapflag/
---

Introduction
------------

When scripting, or creating custom automated events, you may wish to add your own custom mapflags. In order to do so, you'll need to complete some source edits. This article will explain how.

------------------------------------------------------------------------

This article was originally created by [TecnoCronus](http://www.eathena.ws/board/index.php?showuser=273955) on the eAthena forums.

Open /src/map/map.h
-------------------

**Find:**

`unsigned src4instance : 1; // To flag this map when it's used as a src map for instances`

**Add below:**

`unsigned mymapflag : 1;`

Open /src/map/script.c
----------------------

**Find:**

`MF_GUILDLOCK`

**Replace with:**

`MF_GUILDLOCK, // Added comma for then next map-flag.`
`MF_MYMAPFLAG`

------------------------------------------------------------------------

**Find:**

`case MF_GUILDLOCK:        script_pushint(st,map[m].flag.guildlock); break;`

**Below add:**

`case MF_MYMAPFLAG:        script_pushint(st,map[m].flag.mymapflag); break;`

------------------------------------------------------------------------

**Find:**

`case MF_GUILDLOCK:     map[m].flag.guildlock=1; break;`

**Below add:**

`case MF_MYMAPFLAG:     map[m].flag.mymapflag=1; break;`

------------------------------------------------------------------------

**Find:**

`case MF_GUILDLOCK:     map[m].flag.guildlock=0; break;`

**Below add:**

`case MF_MYMAPFLAG:     map[m].flag.mymapflag=0; break;`

Open /src/map/npc.c
-------------------

**Find:**

`else if (!strcmpi(w3,"guildlock"))`
`   map[m].flag.guildlock=state;`

**Below add:**

`else if (!strcmpi(w3,"mymapflag"))`
`   map[m].flag.mymapflag=state;`

Open /db/const.txt
------------------

**Find:**

`mf_guildlock`<tab>`45`

**Below add:**

`mf_mymapflag`<tab>`46`

Conclusion
----------

Recompile and you can now set "mymapflag" to any value. Remember, you can rename the mapflag to whatever, and later use the flag option anywhere else in your source code.

[Category:Source Snippets](/Category:Source_Snippets "wikilink")