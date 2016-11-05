---
title: Mob event variables
permalink: /Mob_event_variables/
---

Introduction
------------

### Purpose

If you've ever wanted to store additional information in variables when a monster dies and it's event script is triggered, this article should help adding your new entries.

### Example

Let's say that when a monster is summoned, we want to be able to read the monster's level (the level of the monster killed) and the class of the monster (the monster ID in the database) so that we can grant additional bonuses. To do this, we would need to modify the source to add this new information.

*While this could be done via OnNPCKillEvent (and using killedrid as the variable), this is not the optimum script to use, as this will be called with every monster killed on every map.*

Open
-----

*Scroll to or find the function mob_dead*

------------------------------------------------------------------------

**Find:**

    if( sd && battle_config.mob_npc_event_type )
    {
        pc_setglobalreg(sd,"killerrid",sd->bl.id);
        npc_event(sd,md->npc_event,0);
    }
    else if( mvp_sd )
    {
        pc_setglobalreg(mvp_sd,"killerrid",sd?sd->bl.id:0);
        npc_event(mvp_sd,md->npc_event,0);
    }

This piece of code is called when the monster dies, and has an event label attached to it. Within this code, we notice two important pieces of information:

    pc_setglobalreg(sd,"killerrid",sd->bl.id);
    pc_setglobalreg(mvp_sd,"killerrid",sd->bl.id);

These two lines (in the two seperate if blocks) represent assigning a variable to the character who killed the mob, which will subsequently be passed into the label event.

### Adding a custom integer

If we wish to add an integer (a number) using the blocks from above, we simply need to do another:

`pc_setglobalreg(sd,` `"variable` `name",` `value);`

In the example I provided, if we wish to store the monster's class id and the level, we need to add:

    pc_setglobalreg(sd, "monsterid", md->class_);
    pc_setglobalreg(sd, "monsterlevel", md->level);

We must also copy this code into the *mvp_sd* block, so our code would look like this overall:

    if( sd && battle_config.mob_npc_event_type )
    {
        pc_setglobalreg(sd,"killerrid",sd->bl.id);
        pc_setglobalreg(sd, "monsterid", md->class_);
        pc_setglobalreg(sd, "monsterlevel", md->level);
        npc_event(sd,md->npc_event,0);
    }
    else if( mvp_sd )
    {
        pc_setglobalreg(mvp_sd,"killerrid",sd?sd->bl.id:0);
        pc_setglobalreg(mvp_sd, "monsterid", md->class_);
        pc_setglobalreg(mvp_sd, "monsterlevel", md->level);
        npc_event(mvp_sd,md->npc_event,0);
    }

### Adding a custom string

To add a custom string, much like copying the monster's name into a variable, it's not much different. Simply follow the instructions above, but instead use a code as such:

`pc_setglobalreg_str(sd,` `"monstername$",` `md->name);`

Simply copy this for the *mvp_sd* block too, and you will be able to read 'monstername$' in the script.

Conclusion
----------

Following this article, you should be able to customise what information gets passed into variables when a mob event label is called. This may be extremely useful for custom hunting quests and such, if you wish to store more information for rewards and such.

[Category:Source Snippets](/Category:Source_Snippets "wikilink")