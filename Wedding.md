---
title: Wedding
permalink: /Wedding/
---

Syntax
------

-   **wedding**;

Description
-----------

This command will call up wedding effects - the music and confetti - centered on the invoking character.

Example
-------

The following code is a snippet from

`if (`[`marriage`](/marriage "wikilink")`($wed_groom$)) {`
`   //Call Wedding effect`
`   `**`wedding`**`;`
`   //Give ring to Bride, and change to wedding sprite.`
`   `[`sc_start`](/sc_start "wikilink")` SC_Wedding,3600000,1;`
`   `[`getitem`](/getitem "wikilink")` 2635,1; //Bride_Ring`
`   //Give ring to Groom, and change to wedding sprite.`
`   `[`attachrid`](/attachrid "wikilink")`(`[`getcharid`](/getcharid "wikilink")`(3,$wed_groom$));`
`   sc_start SC_Wedding,3600000,1;`
`   getitem 2634,1; //Bridegroom_Ring`
`   `[`detachrid`](/detachrid "wikilink")`;`
`   //Switch Script progression back to Bride`
`   attachrid(getcharid(3,$wed_bride$));`
`   `[`cutin`](/cutin "wikilink")` "wedding_bomars02",2;`
`   `[`mapannounce`](/mapannounce "wikilink")` "prt_church","I now pronounce you, "+$wed_groom$+" and "+$wed_bride$+", husband and wife.",bc_map;`
`}`

[Category:Script_Command](/Category:Script_Command "wikilink")