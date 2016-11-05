---
title: Get monster gid
permalink: /Get_monster_gid/
---

Introduction
------------

The ability to control monsters was removed some time ago. To retrieve the GID of a particular monster, to allow further controls, you have to perform a source edit.

Open /src/map/script.c
----------------------

*Scroll to or find the function BUILDIN_FUNC(monster)*

**Find:**

       int owner;
        unsigned char type;

**Below add:**

       int mob_id;

**Find:**

       mob_once_spawn(sd,m,x,y,str,class_,amount,event,owner,type);

**Replace with:**

       mob_id = mob_once_spawn(sd,m,x,y,str,class_,amount,event,owner,type);
        script_pushint(st, mob_id);

Usage
-----

To use this command now, you can run the following:

    set .@MonsterID, monster("map", x, y, name, class, 1);

Please note, that this only works when **one monster is summoned**. If you wish to retrieve the GID of multiple monsters, you'll have to manually create a loop to summon each, and handle the GID after each summon. Such as below:

    for(set .@i, 0; 10 > .@i; set .@i, .@i + 1)
    {
        set .@MobID, monster("map", x, y, name, class, 1);

        // Do whatever with .@MobID here.
    }

[Category:Source Snippets](/Category:Source_Snippets "wikilink")