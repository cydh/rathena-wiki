---
title: Adding new bonuses
permalink: /Adding_new_bonuses/
---

Introduction
------------

### Purpose

If you want to add some uniquity to your server, you may want to consider adding custom bonuses. These are simply, item bonuses which can be added to items, to grant new and interesting features. Depending on how unique you wish your server to be, you may consider adding several new bonuses and adapt them into your server.

### Example

For this article, we will consider adding a new bonus which adds an x/10% chance of skipping consumption of ammo when attacking (this means, arrows, bullets etc.). The bonus would look like this:

`bonus bSkipAmmo,x; // x/10% chance to skip consumption of ammo.`

Open /src/map/map.h
-------------------

*Scroll down to the enum _sp block*

------------------------------------------------------------------------

**Find:**

`SP_ADD_SKILL_BLOW, SP_SP_VANISH_RATE, SP_MAGIC_SP_GAIN_VALUE, SP_MAGIC_HP_GAIN_VALUE //2041-2044`

**What is this?**

Generically, any new bonuses should be added here. This is an enumerator of all special target variables, these define what our bonuses should be called and how we should reference them.

**What to do?**

In order to add a new bonus, we must extend the enumerator and add our bonus slot. Using the example for bSkipAmmo, we shall add a new slot called `SP_SKIPAMMO`:

`SP_ADD_SKILL_BLOW, SP_SP_VANISH_RATE, SP_MAGIC_SP_GAIN_VALUE, SP_MAGIC_HP_GAIN_VALUE, //2041-2044`
`SP_SKIPAMMO //2045-?`

*Note that a comma was added after **SP_MAGIC_HP_GAIN_VALUE**.*

Now we have a definite reference to our bSkipAmmo (= 2045). We can proceed to setting up variables to store this.

Open /src/map/pc.h
------------------

**Find:**

`short sp_vanish_rate;`
`short sp_vanish_per;   `
`unsigned short unbreakable;    // chance to prevent ANY equipment breaking [celest]`
`unsigned short unbreakable_equip; //100% break resistance on certain equipment`
`unsigned short unstripable_equip;`

**What is this?**

If you look at the structure, you'll notice that these are a small portion of variables that will be reset *everytime* the player changes equipment, or status effects are induced. These store bonuses from equipment.

**What to do?**

We need to add an entry for our *bSkipAmmo* bonus, we need a variable to store the **x** value.

`unsigned short skip_ammo;`

This will now be a variable that stores the percentage chance of skipping ammo usage.

Open /src/map/status.c
----------------------

*Scroll to or find the function status_calc_pc_*

------------------------------------------------------------------------

**Find:**

`+ sizeof(sd->sp_vanish_rate)`
`+ sizeof(sd->sp_vanish_per)`
`+ sizeof(sd->unbreakable)`
`+ sizeof(sd->unbreakable_equip)`
`+ sizeof(sd->unstripable_equip)`

**What is this?**

This is a part of the code that will reset all bonuses back to 0 or "turned off" whenever equipment is changed etc, and they will be set back up later on in the script. If you notice, the variables mentioned here are the same as the ones listed in */src/map/pc.h*. We can add our custom variable here.

**What to do?**

**Below add:**

`+ sizeof(sd->skip_ammo)`

This will mean that our *skip_ammo* variable is reset when necessary.

Open /src/map/pc.c
------------------

*Scroll to or find the function pc_bonus*

------------------------------------------------------------------------

**Find:**

`case SP_ATK_RATE:`
`   if(sd->state.lr_flag != 2)`
`       sd->atk_rate += val;`
`   break;`

**What is this?**

This is, very simply, the source code for the bonus *bAtkRate*. From here, we will be adding our custom bonus.

**What to do?**

If you look at the *pc_bonus* arguments, we see *int type, int val*. The variable *val* holds the information passed via the *bonus* command. So, in order to add the skip ammo code:

**Below add:**

`case SP_SKIPAMMO:`
`   if(sd->state.lr_flag != 2)`
`       sd->skip_ammo += val;`
`   break;`

*Note the **sd-&gt;state.lr_flag**, all this does is check if the equipment running the script **is not** an ammo.*

------------------------------------------------------------------------

There, we now have the fundamentals of the skip ammo in place. At this point, you'll be able to assign *sd-&gt;skip_ammo* with a value by parsing **bonus bSkipAmmo,x;** after we add the *db/const.txt* entry.

Open /src/map/battle.c
----------------------

To continue our example, I will show you the necessary area to add the code for the "skipping ammo" check. This will give you an idea of how to use the variable attached to the player.

*Scroll to or find the function battle_consume_ammo*

------------------------------------------------------------------------

**Find:**

`if (!battle_config.arrow_decrement)`
`   return;`

**Below add:**

`if ( sd->skip_ammo > 0 && sd->skip_ammo > rand()%1000 )`
`   return;`

**What does this do?**

Since bSkipAmmo is x/10% (x/1000 chance), we simply check if *skip_ammo* is above 0, and then do a *rand()* function (which returns a random number) and specify that it should be out of 1000 (*%1000*).

If it returns true, then it will skip the ammo consumption.

Open /db/const.txt
------------------

**Find:**

`bMagicHPGainValue`<tab>`2044`

**Below add:**

`bSkipAmmo`<tab>`2045`

Conclusion
----------

Using this article as a guide-line, you should be able to understand the basic concept of adding your own custom bonuses. If you wish to utilise *bonus2, bonus3, bonus4 and bonus5*, then I recommend you take a look at *pc_bonus2* etc in the file and work out the rest.

[Category:Source Snippets](/Category:Source_Snippets "wikilink") [Category:Customization](/Category:Customization "wikilink")