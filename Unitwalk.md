---
title: Unitwalk
permalink: /Unitwalk/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [unitwalk](/unitwalk "wikilink") <GID>,<x>,<y>{,"<event label>"};
-   [unitwalkto](/unitwalkto "wikilink") <GID>,<Target GID>{,"<event label>"};

Description
-----------

This command will tell a <GID> to walk to a position, defined either as a set of coordinates or another object. The command returns a 1 for success and 0 upon failure.

If coordinates are passed, the <GID> will walk to the given x,y coordinates on the unit's current map. While there is no way to move across an entire map with 1 command use, this could be used in a loop to move long distances.

If an object ID is passed, the initial <GID> will walk to the <Target GID> (similar to walking to attack). This is based on the distance from <GID> to <Target ID>. This command uses a hard walk check, so it will calculate a walk path with obstacles. Sending a bad target ID will result in an error.

An optional Event Label can be passed as well which will execute when the <GID> has reached the given coordinates or <Target GID>.

Examples
--------

        // Makes player walk to the coordinates (150,150).
        unitwalk getcharid(3),150,150;

            // Performs a conditional check with the command and reports success or failure to the player.
        if(unitwalk(getcharid(3),150,150))
            dispbottom "Walking you there...";
        else
            dispbottom "That's too far away, man.";

            // Makes player walk to another character named "WalkToMe".
        unitwalkto getcharid(3),getcharid(3,"WalkToMe");