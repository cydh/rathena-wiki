---
title: Killmonster
permalink: /Killmonster/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [killmonster](/killmonster "wikilink") "<map name>","<event label>"{,<type>};

Description
-----------

This command will kill all monsters that were spawned with '[monster](/monster "wikilink")' or '[areamonster](/areamonster "wikilink")' and have a specified event label attached to them. Commonly used to get rid of remaining quest monsters once the quest is complete.

If the label is given as "All", all monsters which have their respawn times set to -1 (like all the monsters summoned with '[monster](/monster "wikilink")' or '[areamonster](/areamonster "wikilink")' script command, and all monsters summoned with GM commands, but no other ones - that is, all non-permanent monsters) on the specified map will be killed regardless of the event label value.

As of r12876 [killmonster](/killmonster "wikilink") now supports an optional argument type. Using 1 for type will make the command fire "OnMyMobDead" events from any monsters that do die as a result of this command.