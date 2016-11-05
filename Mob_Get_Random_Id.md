---
title: Mob Get Random Id
permalink: /Mob_Get_Random_Id/
---

Get a random mob ID
-------------------

`int mob_get_random_id(int type, int flag, int lv)`

`mob_get_random_id(type, flag, lv)`

-   type = Where to take the mob ID
    -   0 = dead branch list
    -   1 = poring list
    -   2 = bloody branch list
-   flag:
    -   &1 = Apply success chance on the list (otherwise, its totally random)
    -   &2 = Apply level check
    -   &4 = Mob cant be mode BOSS
    -   &8 = Mob must earn EXP
-   lv = Mob Level to be checked

[Category:Source_Functions](/Category:Source_Functions "wikilink")