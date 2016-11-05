---
title: Showevent
permalink: /Showevent/
---

Syntax
------

-   [showevent](/showevent "wikilink") <state>, <color>;

Description
-----------

Show a colored mark in the mini-map like "viewpoint" and an emotion on top of a [NPC](/NPC "wikilink"). This is used to indicate that a NPC has a quest or an event to certain player/s.

State can be:

-   0 = disable (Used to disable and remove the mark and the emotion from the NPC.)
-   1 = exclamation emotion (Used to show an important quest event to certain player.)
-   2 = interrogation emotion (Used to show an non-important quest event to certain player.)
-   Other value may cause client crashes.

Color can be:

-   0 = yellow "Quest"
-   1 = orange "Job"
-   2 = green "Event"
-   3 = an MVP flag
-   other values show a transparent mark in the mini-map.

Examples
--------

[`showevent`](/showevent "wikilink")` 1,1; //Display exclamation emotion in orange with a 'Job' bubble.`

[Category:Script Command](/Category:Script_Command "wikilink")