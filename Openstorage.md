---
title: Openstorage
permalink: /Openstorage/
---

Syntax
------

-   [openstorage](/openstorage "wikilink");

Description
-----------

This will open the character's [Kafra](/Kafra "wikilink") storage window on the client connected to the invoking character. It can be used from any kind of [NPC](/NPC "wikilink") or [item script](/item_script "wikilink"), not just limited to Kafra Staff.

The storage window opens regardless of whether there are open NPC dialogs or not, but it is preferred to close the dialog before displaying the storage window, to avoid any disruption when both windows overlap.

Examples
--------

[`mes`](/mes "wikilink")` "I will now open your stash for you";`
[`close2`](/close2 "wikilink")`;`
[`openstorage`](/openstorage "wikilink")`;`
[`end`](/end "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink")