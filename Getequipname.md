---
title: Getequipname
permalink: /Getequipname/
---

Syntax
------

-   [getequipname](/getequipname "wikilink") <equipment slot>;

Description
-----------

Returns the item's [jname](/jname "wikilink") equipped on the <equipment slot>. If the character is not wearing any equipment on <equipment slot>, it will return an empty [string](http://en.wikipedia.org/wiki/String_%28computer_science%29).

Type Values
-----------

| Value          | Equivalent Number | Description                                     |
|----------------|-------------------|-------------------------------------------------|
| EQI_HEAD_TOP | 1                 | Upper head gear.                                |
| EQI_ARMOR     | 2                 | Armor (such as shirts, coats and plates).       |
| EQI_HAND_L   | 3                 | What is in your Left hand.                      |
| EQI_HAND_R   | 4                 | What is in your Right hand.                     |
| EQI_GARMENT   | 5                 | Garment (such as mufflers, hoods, manteaus).    |
| EQI_SHOES     | 6                 | What foot gear the player has on.               |
| EQI_ACC_L    | 7                 | Left accessory slot; Accessory 1.               |
| EQI_ACC_R    | 8                 | Right accessory slot; Acessory 2.               |
| EQI_HEAD_MID | 9                 | Middle Headgear (such as masks and glasses).    |
| EQI_HEAD_LOW | 10                | Lower Headgear (such as beards and some masks). |

Examples
--------

    if (getequipname(3) == "") { // EQI_HAND_L
        mes "Come back when you're wearing something on your Left Hand!!";
    } else {
        mes "Nice, I see you got a "+getequipname(EQI_HAND_L)+" with you!";
    }
    close;

See Also
--------

-   [getequipid](/getequipid "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")