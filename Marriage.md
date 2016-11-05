---
title: Marriage
permalink: /Marriage/
---

Syntax
------

-   **marriage**(&lt;"spouse name"&gt;);

Description
-----------

This function will marry two characters, the [invoking character](/RID#Usage "wikilink") and the one referred to by given *spouse name*, together, setting them up as each other's marriage partner. No second function call has to be issued to make sure the marriage works both ways.

The function returns 1 upon success, or 0 if the marriage could not be completed, either because the other character was not found, because one of the two characters is already married or a baby character.

This will do nothing else for the marriage except setting up the spouse ID for both of these characters. No rings will be given and no effects will be shown.

Examples
--------

[`if`](/if "wikilink")`(`[`isloggedin`](/isloggedin "wikilink")`(`[`getcharid`](/getcharid "wikilink")`(3,$wed_groom$)))`
`{`
`    if(marriage($wed_groom$))`
`    {`
`        //Call Wedding effect`
`        `[`wedding`](/wedding "wikilink")`;`
`        //Give ring to Bride, and change to wedding sprite.`
`        `[`sc_start`](/sc_start "wikilink")` SC_Wedding,3600000,1;`
`        `[`getitem`](/getitem "wikilink")` 2635,1; //Bride_Ring`

The core part of the marriage script, where the actual marriage takes place.

[Category:Script Command](/Category:Script_Command "wikilink")