---
title: Monster death timer
permalink: /Monster_death_timer/
---

Introduction
------------

### Information

For some quests, you may want to summon a monster that only exists for a certain amount of time. In order to do this, it may be easier to add a new command which will allow you to setup an auto-mated death timer on the monster itself.

This way, there's no dependencies on script timers, and the death will be personal the monster itself.

### Pre-requisites

In order for this command to work, you'll need to install the [retrieve monster GID edit](/Get_monster_gid "wikilink") first.

Open /src/map/script.c
----------------------

**Place this code somewhere:**

    /*==========================================
     * Adds a death timer to a monster [Epoque]
     *------------------------------------------*/
    BUILDIN_FUNC(deathtimer)
    {
        int block_id;
        unsigned int tick;
        struct mob_data* md;

        block_id = script_getnum(st, 2);
        tick = script_getnum(st, 3);
        md = map_id2md(block_id);

        if(md == NULL)
            return 0;

        if(md->kill_timer > 0)
        {
            delete_timer(md->kill_timer, mob_death_timer);
            md->kill_timer = INVALID_TIMER;
        }

        md->kill_timer = add_timer(gettick()+tick, mob_death_timer, md->bl.id, 0);

        return 1;
    }

**Find:**

       BUILDIN_DEF(changequest, "ii"),

**Below add:**

`   BUILDIN_DEF(deathtimer, "ii"),`

Open /src/map/mob.h
-------------------

**Find:**

`   short min_chase;`

**Below add:**

`   int kill_timer;`

**Find:**

    int mob_countslave(struct block_list *bl);

**Below add:**

`int mob_death_timer(int tid, unsigned int tick, int id, intptr data);`

Open /src/map/mob.c
-------------------

**Find:**

    void mob_revive(struct mob_data *md, unsigned int hp)
    {
        unsigned int tick = gettick();

**Above add:**

    int mob_death_timer(int tid, unsigned int tick, int id, intptr data)
    {
        struct mob_data* md;

        if( !(md = map_id2md(id)) || md->kill_timer == INVALID_TIMER )
            return 0;

        if( status_isdead(&md->bl) )
            return 0;

        status_kill(&md->bl);

        return 1;
    }

Usage
-----

To use the command, you can use it this way:

    set .@MobID, monster("map", x, y, name, class, 1);
    deathtimer .@MobID, 30000; // Automatically kills the monster after 30 seconds.

The alternative (through basic scripts) is this:

    -  script  MobControl  -1,{
    OnInit:
        monster "map", x, y, name, class, 1, "MobControl::OnMobKilled";
        initnpctimer;
        end;

    OnTimer30000:
        killmonster "map", "MobControl::OnMobKilled";
        end;

    OnMobKilled:
        end;
    }

[Category:Source Snippets](/Category:Source_Snippets "wikilink")