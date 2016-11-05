---
title: Awake
permalink: /Awake/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [awake](/awake "wikilink") "NPC Name";
-   **[sleep](/sleep "wikilink")** <milliseconds>;
-   **[sleep2](/sleep2 "wikilink")** <milliseconds>;

Description
-----------

These commands are used to control the pause of a NPC. Commands [sleep](/sleep "wikilink") and [sleep2](/sleep2 "wikilink") will pause the script for the given amount of milliseconds. Awake is used to cancel a sleep. When awake is called on a NPC it will run as if the sleep timer ran out, and thus making the script continue. Sleep and sleep2 basically do the same, but the main difference is that sleep will not keep the [RID](/RID "wikilink"), while sleep2 does.

Examples
--------

    sleep 10000; //pause the script for 10 seconds and ditch the RID (so no player is attached anymore)
    sleep2 5000; //pause the script for 5 seconds, and continue with the RID attached.
    awake "NPC"; //Cancels any running sleep timers on the NPC 'NPC'.