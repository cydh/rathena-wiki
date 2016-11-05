---
title: Adopt
permalink: /Adopt/
---

Syntax
------

-   [adopt](/adopt "wikilink") "parent name","parent name","novice name";

Description
-----------

This command will set up a novice as a baby of a married couple. All three are referred to by character name. The correct variables are set on all three characters in the same call. The command will unequip anything the novice has equipped and make them a Job_Baby class, as well as send them a 'your job has been changed' message.

Beware of calling this from inside a 'callfunc' function, cause upon successful adoption, this command returns a zero, as if it were a function. This is likely to screw up execution of a 'return' command. You may try to call it as a function instead, but it doesn't return anything upon an error, which may also cause script execution to throw up errors.

Nothing will happen (and nothing will be returned either) if either future parent is below base level 70 and/or if any of the three characters is not found online.

[Category:Script Command](/Category:Script_Command "wikilink") [Category:Obsolete Script Command](/Category:Obsolete_Script_Command "wikilink")