---
title: Adding new skills
permalink: /Adding_new_skills/
---

Introduction
------------

A large area where players have difficulty is adding new skills to the source and client. To implement new skills, it's required that you use an XRay client (if you don't want to use XRay, you will have to replace existing, un-used skills and edit their previous descriptions).

Below will be documentation on how to implement these new skills

Skill ID Rules
--------------

The skill
---------

The skill I will be working on is a simple one.

    Earth Bolt
    Max Level: 10
    Type: Active
    SP Cost: 20 + 5*SkillLV
    Target: 1 Enemy
    Cast Time: 2 sec
    Cool Down: 1 sec
    Duration: Instant
    Deals SkillLV bolts of Earth magic damage to one enemy, at 150% MATK per hit.

Basically, this skill should target 1 enemy, and deal 10 hits of 150% MATK, Earth elemental property and should be magic damage based.

Open /src/map/skill.h
---------------------

Scroll down until you find

       EL_STONE_HAMMER,
        EL_ROCK_CRUSHER,
        EL_ROCK_CRUSHER_ATK,
        EL_STONE_RAIN,

After here is where we add any additional skills. It's better to give the skills a custom ID to begin with. So, let's add our "Earth Bolt" skill.

After those, add

       MG_EARTHBOLT = 8443,

MG_ definitively means "Mage", you'll work out the acronyms as you scroll through the skills. We have defined the basis of the skill. As you can see, the skill id is set to '8443' since Earth Elemental's Stone Rain is set to 8442 (and is the last player accessible skill).

Open /src/map/skill.c
---------------------

This file is where we define the actual skill implementations. For single-target skills, all processing of that skill will go in *skill_castend_damage_id* (for damaging skills) or *skill_castend_nodamage_id* (for non-damage skills).

### Magic based skills

Because Earth Bolt is **damage** based, find the *skill_castend_damage_id* function and find:

       case AB_RENOVATIO:
        case AB_HIGHNESSHEAL:
        case AB_DUPLELIGHT_MAGIC:
        case WM_METALICSOUND:
        case MH_ERASER_CUTTER:

The reason we will be placing the *case* for Earth Bolt here is because:

           skill_attack(BF_MAGIC,src,src,bl,skillid,skilllv,tick,flag);

The BF_MAGIC quality means that the skill is magic based, and should be calculated under the magic battle calculations. So, after `case` `NJ_HUUJIN` add:

       case MG_EARTHBOLT:

### Weapon based skills

In the event of wanting to add a skill that's based on Weapon, rather than Magic, find:

       case WM_GREAT_ECHO:
        case GN_SLINGITEM_RANGEMELEEATK:
        case KO_JYUMONJIKIRI:
        case KO_SETSUDAN:
        case KO_KAIHOU:

And add the case after those. If we wanted Earth Bolt to be weapon based, it would look like this:

       case WM_GREAT_ECHO:
        case GN_SLINGITEM_RANGEMELEEATK:
        case KO_JYUMONJIKIRI:
        case KO_SETSUDAN:
        case KO_KAIHOU:
        case MG_EARTHBOLT:

However, we will stick to the Magic function instead.

Open /src/map/battle.c
----------------------

In this function, all main damage calculations are performed. And in seperate functions, the % modifiers for the skills are stored. Therefore, for our 150% damage, we add the extra 50% (since 100% is the default) in the appropriate function.

### Weapon based attacks

For **Weapon** based attacks, the modifiers are found in *battle_calc_weapon_attack*. Simply find:

       case NPC_VAMPIRE_GIFT:
            skillratio += ((skill_lv-1)%5+1)*100;
            break;

And add your damage modifier there. For example, if Earth Bolt was Weapon based, we would add:

       case MG_EARTHBOLT:
            skillratio += 50;
            break;

The *+= 50* simply means "Add 50% onto the 100%" for 150% ATK damage.

### Magic based attacks

For **Magic** based attacks, the modifiers are found in *battle_calc_magic_attack*. Simply find:

       case NPC_EARTHQUAKE:
            skillratio += 100 +100*skill_lv +100*(skill_lv/2);
            break;

And add the damage modifier below. Since Earth Bolt is magic based, we add it here.

       case MG_EARTHBOLT:
            skillratio += 50;
            break;

This now means that Earth Bolt will deal Magic damage at 150% MATK.

Skill database support
----------------------

Technically speaking, the basis of the skill is now in place. Of course, if you want to implement more complex skills, there's a lot more to it. A seperate section will be created in the future for this. But for now, we need to implement the skill database entries. The files below can be find within db/(pre/re)/. Only one from both (pre/re) need to be updated, it's one you use in your server.

### skill_db.txt

For our Earth Bolt, we can now enter this:

    8443,5,8,1,2,0,0,10,1:2:3:4:5:6:7:8:9:10,yes,0,0,0,magic,0,0,MG_EARTHBOLT,Earth Bolt

This defines that:

`Earth` `Bolt` `has` `a` `range` `of` `5` `cells,` `hits` `multiple` `times,` `is` `Earth` `element` `and` `targets` `1` `enemy.` `It` `can` `be` `interrupted,` `and` `is` `of` `magic` `type` `damage.` `The` `amount` `of` `hits` `increases` `by` `1` `every` `level,` `with` `a` `maximum` `level` `of` `10.`

### skill_cast_db.txt

For our Earth Bolt, we can now enter this:

    8443,2000,1000,0,0,0

This defines that:

`Earth` `Bolt` `has` `a` `2` `second` `cast` `time,` `and` `a` `1` `second` `delay` `time.` `There` `is` `no` `after-cast` `walk-delay`

### skill_require_db.txt

For our Earth Bolt, we can now enter this:

    8443,0,0,25:30:35:40:45:50:55:60:65:70,0,0,0,99,0,0,none,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0

This defines that:

`Earth` `Bolt` `requires` `25` `SP` `at` `level` `1,` `30` `SP` `at` `level` `2` `..` `70` `SP` `at` `level` `10.` `Can` `be` `cast` `with` `any` `weapon,` `doesn't` `require` `a` `state` `and` `doesn't` `require` `any` `items` `to` `be` `consumed.`

### skill_tree.txt

This part of the database isn't necessary if it can't be learned by a class. However, if you want a class to learn a skill, you have to make an entry in skill_tree.txt. An example below:

    2,8443,10,19,5,20,5,0,0,0,0,0,0

This defines that:

`Earth` `Bolt` `can` `be` `learned` `by` `Mage,` `has` `a` `maximum` `level` `of` `10` `(for` `this` `class),` `and` `requires` `skill` `19` `(Firebolt)` `at` `level` `5,` `and` `skill` `20` `(Lightning` `Bolt)` `at` `level` `5.`

------------------------------------------------------------------------

Technically, this is usually all the areas that you'd usually cover with skill database files. There are more, but that's for you to explore.

XRay support
------------

To support the skill in the actual client, assuming you're using XRay (required to add new IDs for skills), you can do the following:

### ability_tab.txt

To add in the custom skill, find:

    NJ_ISSEN

And below it, add:

    MG_EARTHBOLT

### leveluseskillspamount.txt

To make the skill level-selectable, simply add an entry in leveluseskillspamount.txt in the data folder.

    8443#
    25#
    30#
    35#
    40#
    45#
    50#
    55#
    60#
    65#
    70#
    @

This will allow the skill to be level selectable.

Renewal/Non-Xray Support
------------------------

The following implementations are according to Revision 228 from Lua Project(2012-05-23)+. To support Renewal and post 10/13/2009 Clients (or the last Xray) we'd need to make use of .[lua](/lua "wikilink") and .[lub](/lub "wikilink") files.

The implementation is different between then many client versions, but there's generally 2 implementations:

### no skillinfoz folder

in data/lua files/skillinfo/skilltreeview.lua find:

    {"MG_FIREWALL", 18; Pos = 19, MaxLv = 10, NeedSkillList = {6, 12}}

change to:

    {"MG_FIREWALL", 18; Pos = 19, MaxLv = 10, NeedSkillList = {6, 12}},
    {"MG_EARTHBOLT",8443; Pos = 20, MaxLv = 10, NeedSkillList = {19,20}}

### has skillinfoz folder

skillid.lua find:

    ECLAGE_RECALL = 3035,

After Add:

    MG_EARTHBOLT = 8443,

in data/lua files/skillinfo/skilldescript.lua find:

        [SKID.MG_THUNDERSTORM] = {

            "Thunder Storm",
            "Max Level:^777777 10 ^000000",
            "Type:^777777 Offensive ^000000",
            "SP Cost:^777777 24 + 5*SkillLV ^000000",
            "Target:^777777 cell ^000000",
            "Range:^777777 9 cells ^000000",
            "Cast Time:^777777 1*SkillLV sec ^000000",
            "Cool Down:^777777 2 sec ^000000",
            "Duration:^777777 0.2*SkillLV sec ^000000",
            "Effect:^777777 Hits every Enemy in a 5x5 area around the targeted cell with 1 Wind Element Bolt per level at a rate of 1 bolt every 0.2 seconds. Each bolt does 0.8*MATK Wind element damage. ^000000",
            "[LV 1]^777777 1 Bolt ^000000",
            "[LV 2]^777777 2 Bolts ^000000",
            "[LV 3]^777777 3 Bolts ^000000",
            "[LV 4]^777777 4 Bolts ^000000",
            "[LV 5]^777777 5 Bolts ^000000",
            "[LV 6]^777777 6 Bolts ^000000",
            "[LV 7]^777777 7 Bolts ^000000",
            "[LV 8]^777777 8 Bolts ^000000",
            "[LV 9]^777777 9 Bolts ^000000",
            "[LV 10]^777777 10 Bolts ^000000",
        },

After Add:

        [SKID.MG_EARTHBOLT] = {
            "Earth Bolt",
            "Max Level:^777777 10 ^000000",
            "Type:^77777 Active ^000000",
            "SP Cost:^777777 20 + 5*SkillLV ^000000",
            "Target:^777777 1 Enemy ^000000",
            "Cast Time:^777777 2 sec ^000000",
            "Cool Down:^777777 1 sec ^000000",
            "Duration:^777777 Instant ^000000",
            "Effect: ^777777 Deals SkillLV bolts of Earth magic damage to one enemy, at 150% MATK per hit.^000000"
        },

skilltreeview.lua change:

    [JOBID.JT_MAGICIAN] = {
            [1] = SKID.MG_STONECURSE,
            [2] = SKID.MG_COLDBOLT,
            [3] = SKID.MG_LIGHTNINGBOLT,
            [4] = SKID.MG_NAPALMBEAT,
            [5] = SKID.MG_FIREBOLT,
            [6] = SKID.MG_SIGHT,
            [8] = SKID.MG_SRECOVERY,
            [9] = SKID.MG_FROSTDIVER,
            [10] = SKID.MG_THUNDERSTORM,
            [11] = SKID.MG_SOULSTRIKE,
            [12] = SKID.MG_FIREBALL,
            [13] = SKID.MG_ENERGYCOAT,
            [18] = SKID.MG_SAFETYWALL,
            [19] = SKID.MG_FIREWALL
        },

to:

        [JOBID.JT_MAGICIAN] = {
            [1] = SKID.MG_STONECURSE,
            [2] = SKID.MG_COLDBOLT,
            [3] = SKID.MG_LIGHTNINGBOLT,
            [4] = SKID.MG_NAPALMBEAT,
            [5] = SKID.MG_FIREBOLT,
            [6] = SKID.MG_SIGHT,
            [8] = SKID.MG_SRECOVERY,
            [9] = SKID.MG_FROSTDIVER,
            [10] = SKID.MG_THUNDERSTORM,
            [11] = SKID.MG_SOULSTRIKE,
            [12] = SKID.MG_FIREBALL,
            [13] = SKID.MG_ENERGYCOAT,
            [18] = SKID.MG_SAFETYWALL,
            [19] = SKID.MG_FIREWALL,
            [20] = SKID.MG_EARTHBOLT
        },

skillinfolist.lua Change:

        [SKID.ECL_SEQUOIADUST] = {
            "ECL_SEQUOIADUST";
            SkillName = "Sequoia Dust",
            MaxLv = 1,
            SpAmount = { 0 },
            bSeperateLv = false,
            AttackRange = { 7 },
        }

To:

        [SKID.ECL_SEQUOIADUST] = {
            "ECL_SEQUOIADUST";
            SkillName = "Sequoia Dust",
            MaxLv = 1,
            SpAmount = { 0 },
            bSeperateLv = false,
            AttackRange = { 7 },
        },
        [SKID.MG_EARTHBOLT] = {
            "MG_EARTHBOLT";
            SkillName = "Earth Bolt",
            MaxLv = 10,
            SpAmount = { 25, 30, 35, 40, 45, 50, 55, 60, 65, 70 },
            _NeedSkillList = {
                { SKID.MG_FIREBOLT, 5},
                { SKID.MG_LIGHTNINGBOLT, 5}
            }
            },

### Finishing up

You can add the rest of the information in skillnametable.txt, skilldesctable2.txt and you'll need to add the appropriate Sprite and BMP file for the skill. Use the name MG_EARTHBOLT as the name of the file, and for the entries in the two text files.

[Category:Source Snippets](/Category:Source_Snippets "wikilink") [Category:Customization](/Category:Customization "wikilink")