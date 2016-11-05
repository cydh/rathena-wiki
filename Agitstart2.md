---
title: Agitstart2
permalink: /Agitstart2/
---

Syntax
------

-   **agitstart2**;
-   **agitend2**;

Description
-----------

These two commands initialize the start and end the [War of Emperium](/War_of_Emperium "wikilink"): Second Edition respectively.

The commands by themselves only set an server-internal flag, that guild siege is in effect and run **OnAgitStart2** or **OnAgitEnd2** event labels on all currently loaded scripts, which contain this label. These are typically WoE:SE scripts located in **npc/guild2**, which are responsible the actual starting and ending of the guild siege.

Example
-------

[`OnInit`](/OnInit "wikilink")`:`
`    `[`if`](/if "wikilink")`(`[`gettime`](/gettime "wikilink")`(3)<15 || gettime(3)>=17)`
`    {`
`        `[`end`](/end "wikilink")`;`
`    }`
[`OnClock`](/OnClock "wikilink")`1500:`
`    agitstart2;`
`    end;`
`OnClock1700:`
`    agitend2;`
`    end;`

A basic WoE:SE controller script, which resumes the siege, even when the server is started during the WoE:SE period.

[Category:Script Command](/Category:Script_Command "wikilink")