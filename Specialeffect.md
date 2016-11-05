---
title: Specialeffect
permalink: /Specialeffect/
---

Syntax
------

-   specialeffect <effect>{, <target>{, "<NPC name>"}};

Description
-----------

This script command will display a given special effect on the attached, or specified if <NPC name> is provided, NPC. If <NPC name> is provided but the NPC does not exist then the script command will not perform. If the NPC does exist, but has no visible presence on the screen, then it is possible that the client may crash or behave peculiarly.

Parameters
----------

### Effect

The effect to display in the client. Some effects are unsupported in the client so it is recommended to find the ID of a working effect before using the ID in this command. **For a list of IDs**, please see

### Target

Specifies how the effect should be distributed graphically. By default, the target is flagged as AREA which means all players within client range will see the effect. Otherwise, when specified the effect will only apply and be sent to clients which match the target property.

### NPC Name

Specifies which NPC the effect should apply to, rather than the NPC which is currently running. If the NPC named does not exist then the effect will not be performed.

Examples
--------

-   Perform the item heal effect on the running NPC.

<!-- -->

    specialeffect 7;

-   Perform the item heal effect on the running NPC, but only visible to the attached player.

<!-- -->

    specialeffect 7, SELF;

-   Perform the item heal effect on the running NPC, but only visible to party members of the player attached, excluding the player.

<!-- -->

    specialeffect 7, PARTY_WOS;

[Category:Script Command](/Category:Script_Command "wikilink")