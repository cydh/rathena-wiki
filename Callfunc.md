---
title: Callfunc
permalink: /Callfunc/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [callfunc](/callfunc "wikilink") "<function>"{,<argument>,...<argument>};
-   [callfunc](/callfunc "wikilink")("<function>"{,<argument>,...<argument>});

Description
-----------

This command lets you call up a function NPC. A function NPC can be called from any script on any map server. Using the 'return' command it will come back to the place that called it.

You can pass arguments to your function - values telling it what exactly to do - which will be available there with getarg() (see 'getarg') Notice that returning is not mandatory, you can end execution right there.

If you want to return a real value from inside your function NPC, it is better to write it in the function form, which will also work and will make the script generally cleaner.

Examples
--------

        place,50,50,6   script  Woman   115,{
            mes "[Woman]"
            mes "Lets see if you win";
            callfunc "funcNPC";
            mes "Well done you have won";
            close;
        }
        function    script  funcNPC {
            if(rand(2)) return;
            mes "Sorry you lost";
            close;
        }

        place,50,50,6   script  Man 115,{
            mes "[Man]"
            mes "Gimme a number!";
            next;
            input .@number;
            if (callfunc("OddFunc",.@number)) mes "It's odd!";
            else mes "It's even";
            close;
        }
        function    script  OddFunc {
            if (getarg(0)%2) return 1; // it's odd
            return 0; // it's even
        }