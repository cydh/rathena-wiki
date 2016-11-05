---
title: Setriding
permalink: /Setriding/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [setriding](/setriding "wikilink") {<flag>};

Description
-----------

If <flag> is 0 this command will remove the mount from the character. Otherwise it give the invoking character a PecoPeco (if they are a Knight series class) or a GrandPeco (if they are a Crusader seriesclass). Unlike 'setfalcon' and 'setcart' this will not work at all if they aren't of a class which can ride.

Return Values
-------------

| Value | Description                                                    |
|-------|----------------------------------------------------------------|
| 0     | Will return if the player has a peco and remove it.            |
| 1     | Will return if the player does not have a peco and set a peco. |

Fact
----

Remember to check if the player is riding before setting a peco.

Examples
--------

    if(BaseJob != Job_Swordman && BaseClass == Job_Swordman && checkriding() == 0 && getskilllv("KN_RIDING") > 0)
        setriding;
    close;