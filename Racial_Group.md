---
title: Racial Group
permalink: /Racial_Group/
---

Intro
=====

This page will try to explain the file

What is it for?
---------------

The mob_race2_db.txt file is used to define groups of monsters "racially".

Usage and Syntax
----------------

The structure of the Race should be configured like this

    Race2ID,MobID1,MobID2,MobID3,...,MobID9

Race2ID would determine the ID of the monsters you have set, followed by the Mob IDs of the monster to be listed in the group.

It should not be confused with Race, but should be treated rather as a group, i.e. a group of similar monsters.

Example
-------

Adding this in would create a Racial Group between Poring, Drops, Poporing, and Marin.

    // Poring Clan (Custom)
    7,1002,1113,1031,1595

For additional info, read [Goblin Leader Card](http://ratemyserver.net/index.php?iname=goblin+leader+card&page=item_db&quick=1&isearch=Search).