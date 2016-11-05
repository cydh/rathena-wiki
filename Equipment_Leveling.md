---
title: Equipment Leveling
permalink: /Equipment_Leveling/
---

Introduction and Important Notices
----------------------------------

<small>''(Original topic by Epoque: [Equipment leveling system](http://www.eathena.ws/board/index.php?showtopic=201038)) ''</small>

Well, I suddenly had the urge to change the whole Refine system for Ragnarok. Don't ask me why, it was a spur of the moment thing. So, I ended up re-modelling the system and implemented a "weapon leveling" system instead.

Now, please bear in mind this was created on trunk 13304. So there may be incompatibility issues at the moment. I plan on importing it into earlier revision(s), so I'll release multiple diff patches.

So, the diff is online. There are a few notes I should include though:

-   This was built on trunk so there may be incompatibilities between [trunk and stable](/Trunk&Stable "wikilink") at the moment
-   This was built on rAthena r13304. Again, some incompatibilities could take place.
-   This is just a test release to obtain some feedback. I do realize there may be bugs, I'll be fixing it up after this
-   There is currently an issue with the wlv_takeexp: option, where sometimes certain items at a certain level drastically increases the amount of base experience the player earns. Again, trying to figure out what's wrong with this (though I have no clue D:)
-   This completely replaces the refine system for Ragnarok. If you have any NPCs that allow refining, please remove them because this uses the refine system as a method of storing level information (only way to append the level infront of equipment)
-   This is only designed for SQL version of rAthena, I haven't yet implemented a TXT version

**Test this at your own risk**. Like I said, this was just a little project I made up. Took me a couple of days, and I'll be porting it to Stable and earlier revisions of the SVN too.

Other Information
-----------------

I modified @refine also, so that if your equipment's maximum level is set differently than other equipment, or perhaps you've lowered all equipment's levels to below 10 (or increased it?), then @refine will only refine to the maximum that you set for the level of that equipment. IE, if you set an Armor to only level to level 5, it will only refine using @refine to level 5.

I recommend you only test this by downloading the Head Revision of the SVN and applying it to that to play with it. Importing it into a pre-existing project could cause many complications. It's recommended to just play with for now. (It's only a fun little side-project, nothing that should be implemented large-scale unless you really want to)

Installation
------------

You can download the .diff file [here](http://www.darkorigin.org/WLevelling.diff) , and simply use TortoiseSVN to apply that patch to your <server>\\src\\ folder. This will modify SQL queries and some of the structures required to hold the EXP information.

How to apply this diff for Linux First cd into the directory where you Athena is located and then into the src folder then do the following:

`wget `[`http://www.darkorigin.org/WLevelling.diff`](http://www.darkorigin.org/WLevelling.diff)
`patch < WLevelling.diff`

Then, copy the attached files to the stated locations:

`Copy this file to db\equip_exp.txt`
`Copy this file to db\item_exp.txt`

After this, open conf\\battle\\items.conf and append the following to the bottom:

<code>

    // How much user experience will go towards the equipment for levelling?
    // Value is x/100 (so 1 = 0.01%, 100 = 1%)
    // If the value is less than 0, the experience gained will be fixed to -wlv_userexp
    // IE: wlv_userexp: -50 will fix EXP after every kill to 50 for the equipment
    // NOTE: 0 = disable the entire levelling system
    wlv_userexp: 5

    // What is the maximum level for the equipment to obtain
    // The minimum is 1 and the maximum is 20.
    // NOTE: 0 = default maximum refine (10)
    wlv_maxlevel: 5

    // Take away EXP for the weapon from the user's gained experience?
    // NOTE: Recommended set to 0/no at the moment. There's an EXP bug.
    // 1 : Player Gained EXP = Base EXP - Weapon EXP
    // 0 : Player Gained EXP = Base EXP (Weapon still gains x% EXP)
    wlv_takeexp: 0

    // What is the maximum EXP a piece of equipment can gain?
    // NOTE: 0 = disabled
    wlv_maxexp: 0

    // Can equipment level up multiple times in a go? (Note 1)
    wlv_multilevel: yes

    // Will the user still benefit from the DEF bonuses for each level? (Note 1)
    wlv_gaindefbonus: no

</code>

And, finally, perform the following MySQL Query on your database:

`` ALTER TABLE `inventory` ADD `exp` MEDIUMINT(10) NOT NULL DEFAULT '0'; ``
`` ALTER TABLE `cart_inventory` ADD `exp` MEDIUMINT(10) NOT NULL DEFAULT '0'; ``
`` ALTER TABLE `storage` ADD `exp` MEDIUMINT(10) NOT NULL DEFAULT '0'; ``
`` ALTER TABLE `guild_storage` ADD `exp` MEDIUMINT(10) NOT NULL DEFAULT '0'; ``

Optionally, you can change the "+" symbol in-game by editing your client using PSPad HEX editor:

Find (NOT in Text search mode):

`2F2F 0000 2B25 6420 0000`

Replace with:

`2F2F 0000 4C76 2E25 6420`

And you should be pretty much set. I do want feedback on this system if possible, since I want to flatten out any bugs and officially release this as a full release.

Thanks!

[Category:Customization](/Category:Customization "wikilink") [Category:Source Snippets](/Category:Source_Snippets "wikilink")