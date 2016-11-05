---
title: Adding new statuses
permalink: /Adding_new_statuses/
---

Information
-----------

When modifying your server, the time may come when you need to add or ammend status effects, and the bonuses or the 'scripts' that they provide. To do so, will require some source modifications, but will result in the ability to create and initialize status effects.

Open
-----

You will notice a large enumerator called "sc_type", which defines the different statuses. When creating a new status, we need to move to the *end* of the enumerator, and add a custom SC type like below:

       SC_HELLPOWER = 294,
        SC_INVINCIBLE, //295
        SC_INVINCIBLEOFF,
        SC_CUSTOMSTATUS, // This is our custom status effect

        SC_MAX, //Automatically updated max, used in for's to check we are within bounds.

Note that SC_CUSTOMSTATUS is placed *before* the SC_MAX entry. Any new status effects must be placed before SC_MAX and preceed with a comma. Here we have declared a new status effect, so we can now move onto use it.

Open
-----

Jump to the function *status_change_start*:

### Status effect immunity

       undead_flag = battle_check_undead(status->race,status->def_ele);
        //Check for inmunities / sc fails
        switch (type)
        {

This block is where we actually perform any checks, such as circumstances which disallow a status from being used. For example, let's say that SC_CUSTOMSTATUS cannot be inflicted when the target has SC_BLIND active.

       case SC_CUSTOMSTATUS:
            if(sc->data[SC_BLIND])
                return 0;
        break;

And now, if the target has SC_BLIND active, the status will not be inflicted at all.

### Status effect curing

       //Before overlapping fail, one must check for status cured.
        switch (type)
        {

This block actually cancels *other* status effects if your status effect is being activated. Like the above, it's not necessary, but let's say that SC_CUSTOMSTATUS *removes* SC_BLIND.

       case SC_CUSTOMSTATUS:
            status_change_end(bl, SC_BLIND, -1);
            break;

As simple as that, now whenever SC_CUSTOMSTATUS is inflicted, SC_BLIND will be removed.

### val1, val2, val3 and val4

           case SC_REBIRTH:
                val2 = 20*val1; //% of life to be revived with
                break;

If you find this piece of code, it means you're in the actual block which manipulates val1, val2, val3, val4 and tick. This is especially useful when altering status effects that have been initialized by skills.

           case SC_CUSTOMSTATUS:
                val2 = val1 * 30; // HIT reduced by 30 per val1.
                break;

In this block of code, we set the 'val2' property of SC_CUSTOMSTATUS to *val1 \* 30*. Therefore, if val1 is set to 1, val2 is 30, is val1 is set to 2, val2 is 60. Usually, skills pass **skill_lv** (the level of the skill used) into val1, which means you can adjust the settings for val2, val3 and val4 based on the skill level used.

### Using the status effect

Jump to the function *status_calc_hit*:

       if(sc->data[SC_MERC_HITUP])
            hit += sc->data[SC_MERC_HITUP]->val2;

As you can see, SC_MERC_HITUP directly influences the HIT rate as calculated in *status_calc_hit*. We can add a custom code which will also modify HIT, such as below:

       if(sc->data[SC_CUSTOMSTATUS])
            hit -= sc->data[SC_CUSTOMSTATUS]->val2;

This means that HIT will be decreased by whatever value is in val2 (as calculated in *status_change_start*).

Open
-----

### Implementing

Find

    SC_INVINCIBLEOFF<tab>296

Add below

    SC_CUSTOMSTATUS<tab>297

And there you go. The status effect *SC_CUSTOMSTATUS* is now ready for use.

### Using the status

    sc_start SC_CUSTOMSTATUS, 60000, 2;

This will start SC_CUSTOMSTATUS, it will last for 60 seconds and it will remove SC_BLIND if it is active. The '2' is the *val1* entry, which means that *val2 = 2 \* 30;*, which will cause HIT to be decreased by 60 for 60 seconds.

[Category:Source Snippets](/Category:Source_Snippets "wikilink") [Category:Customization](/Category:Customization "wikilink")