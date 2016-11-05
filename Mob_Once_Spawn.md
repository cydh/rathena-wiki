---
title: Mob Once Spawn
permalink: /Mob_Once_Spawn/
---

Mob Spawn
---------

`int mob_once_spawn (struct map_session_data *sd, char *mapname, short x, short y, const char *mobname, int class_, int amount, const char *event)`

`mob_once_spawn(sd,"mapname", x, y, "Name", mob_class, Count, "Event");`

-   "mapname" = Map Name ("this" is actual map)
-   X and Y = Map coordenates
-   "Name" = Name that will show
    -   "--ja--" Will show the name in collumn "Japanese" in mob_db
    -   "--en--" Will show the name in collumn "English" in mob_db
    -   [status_get_name](/status_get_name "wikilink")(src) Will show character name
-   mob_class = Mob ID
-   Count = Amount to be spawned
-   Event = Event that will start On Mob Death

[Category:Source_Functions](/Category:Source_Functions "wikilink")