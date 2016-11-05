---
title: Callsub
permalink: /Callsub/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [callsub](/callsub "wikilink") <label>{,<argument>,...<argument>};

Description
-----------

This command will go to a specified label within the current script (do NOT use quotes around it) coming in as if it were a '[callfunc](/callfunc "wikilink")' call, and pass it arguments given, if any, which can be recovered there with '[getarg](/getarg "wikilink")'. When done there, you should use the '[return](/return "wikilink")' command to go back to the point from where this label was called. This is used when there is a specific thing the script will do over and over, this lets you use the same bit of code as many times as you like, to save space and time, without creating extra NPC objects which are needed with '[callfunc](/callfunc "wikilink")'. A label is not callable in this manner from another script.

Examples
--------

            mes "[Woman]";
            mes "Lets see if you win";
            callsub Check,2;
            mes "Well done you have won";
            close;
        Check:
            if(!rand(getarg(0))) return;
            mes "Sorry you lost";
            close;