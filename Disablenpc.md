---
title: Disablenpc
permalink: /Disablenpc/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [disablenpc](/disablenpc "wikilink") "<NPC object name>";
-   **[enablenpc](/enablenpc "wikilink")** "<NPC object name>";

Description
-----------

These two commands will disable and enable, respectively, an NPC object specified by name. The disabled NPC will disappear from sight and will no longer be triggerable in the normal way. It is not clear whether it will still be accessible through '[donpcevent](/donpcevent "wikilink")' and other triggering commands, but it probably will be. You can disable even warp NPCs if you know their object names, which is an easy way to make a map only accessible through walking half the time. Then you '[enablenpc](/enablenpc "wikilink")' them back.

You can also use these commands to create the illusion of an NPC switching between several locations, which is often better than actually moving the NPC - create one NPC object with a visible and a hidden part to their name, make a few copies, and then disable all except one.

Examples
--------

    prontera,100,100,4  script  Tim 81,{
        disablenpc "timsbrothertom";
        mes "Hey you, I disabled my brother Tom by accident :S";
        mes "Can you help me to enable him back?";
        next;
        if(select("Yes, sure!:No!") == 2) close;
        enablenpc "timsbrothertom";
        mes "Thank you very much! He is back now :)";
        close;
    }
    prontera,102,100,4  script  Tom#1::timsbrothertom   81,{
        mes "Hi, I'm Tims brother!";
        close;
    }