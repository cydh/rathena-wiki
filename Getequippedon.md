---
title: Getequippedon
permalink: /Getequippedon/
---

Introduction
------------

### Why use this command

An often unknown feature of equipment is that they can be slotted wherever they like. More specifically, cards can be defined to be slotted in more than just one type of equipment. You can define that a card can be equipped in either an Armor, a Shield or a Garment. The only problem is that, if you want a card to perform different scripts when in different items, you may run into problems finding which type of equipment the card is slotted in.

This command is designed to combat the problem, and to return the type of item the card is slotted in.

### Example of a card

    4490,Multislot_Card,Multislot Card,6,2,,10,,,,,,,,52,,,,,{},{},{}

This card can be slotted in an Armor (16), a Shield (32) or a Garment (4) *(16 + 32 + 4 = 52)*. However, let's say that you want the following effects to apply:

    [Slotted in Shield]
    MDEF + 3
    [Slotted in Armor]
    DEF + 4
    [Slotted in Garment]
    FLEE + 10

We wouldn't be able to differentiate where the card is currently slotted without coding a long, complicated function to find out. This wouldn't be very effective when the player's status has to be recalculated.

Open /src/map/script.c
----------------------

Insert the following code somewhere:

    /*=======================================================
    * Returns where the current item is equipped.
    *-------------------------------------------------------*/
    BUILDIN_FUNC(getequippedon)
    {
        int i = current_equip_item_index; // Store here for neater code.
        TBL_PC *sd;
        if ((sd = script_rid2sd(st))!= NULL)
        {
            switch(i)
            {
                case EQI_HAND_L:
                    script_pushint(st, (sd->inventory_data[i]->type == IT_ARMOR ? EQP_SHIELD : EQP_WEAPON));
                    break;
                default:
                    script_pushint(st, sd->status.inventory_data[i].equip);
                    break;
            }
        }
        else
            script_pushint(st,0);
        return 0;
    }

------------------------------------------------------------------------

Find

       BUILDIN_DEF(getequippercentrefinery,"i"),

Add below

       BUILDIN_DEF(getequippedon,""),

Usage
-----

To use this command now, perhaps for the aformentioned card, use it as follows:

    4490,Multislot_Card,Multislot Card,6,2,,10,,,,,,,,52,,,,,{ if(getequippedon()==EQP_ARMOR) { bonus bDef,4; } else
    if(getequippedon()==EQP_SHIELD) { bonus bMdef,3; } else bonus bFlee,10; },{},{}

[Category:Source Snippets](/Category:Source_Snippets "wikilink")