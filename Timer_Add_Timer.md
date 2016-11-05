---
title: Timer Add Timer
permalink: /Timer_Add_Timer/
---

This function adds a temporary timer .
--------------------------------------

`int add_timer(unsigned int tick, TimerFunc func, int id, int data)`

`add_timer(Tick, Function, GID, Args);`

-   **Tick:**
    -   Time that it will be executed (In Milliseconds)
    -   ie. gettick()+300000
    -   in 5 minutes
-   **Function:** - Linked Function (ie. battle_delay_damage_sub)
-   **GID:** - Game ID (ie. mob_data-&gt;block_list.id)
-   **Args:** - Additional Arguments (ie. (int)script_state)

[Category:Source_Functions](/Category:Source_Functions "wikilink")