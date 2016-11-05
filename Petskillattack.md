---
title: Petskillattack
permalink: /Petskillattack/
---

Syntax
------

-   **petskillattack** <skill id>,<skill level>,<rate>,<bonusrate>;
-   **petskillattack** "<skill name>",<skill level>,<rate>,<bonusrate>;
-   **petskillattack2** <skill id>,<damage>,<number of attacks>,<rate>,<bonusrate>;
-   **petskillattack2** "<skill name>",<damage>,<number of attacks>,<rate>,<bonusrate>;

Description
-----------

These two commands will make the pet cast an attack skill on the enemy the pet's owner is currently fighting. Skill IDs and levels are as per [petskillsupport](/petskillsupport "wikilink").
'petskillattack2' will make the pet cast the skill with a fixed amount of damage inflicted and the specified number of attacks.

All commands with delays and durations will only make the behavior active for the specified duration of seconds, with a delay of the specified number of seconds between activations. Rates are a chance of the effect occurring and are given in percent. 'bonusrate' is added to the normal rate if the pet intimacy is at the maximum possible.

The behavior modified with the above mentioned commands will only be exhibited if the pet is loyal and appropriate configuration options are set in

Examples
--------

    petskillattack 76,5,50,10;

This would give the pet the skill Lex Divina at level 5. It has a 50% chance to cast, but is increased by 10% if the pet has full intimacy.

    petskillattack2 15,150,1,50,20;

    petskillattack2 "MG_FROSTDIVER",150,1,50,20;

This would give the pet the skill Frost Diver and would cause 150 damage. It has a 50% chance to cast, but is increased by 20% if the pet has full intimacy.

If the skill has multiple hits, it can be

    petskillattack2 "LK_SPIRALPIERCE",1000,10,50,20;

It gives pet Spiral Pierce skill with 10 hits, each hit will deals 100 damage.

[Category:Script_Command](/Category:Script_Command "wikilink")