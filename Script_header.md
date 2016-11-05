---
title: Script header
permalink: /Script_header/
---

The [script header](/script_header "wikilink") is the first 15 or so lines of a script file that contain information identifying the script.

Example
-------

    //===== rAthena Script =======================================
    //= Warper
    //===== By: ==================================================
    //= Darkchild
    //===== Current Version: =====================================
    //= 2.1
    //===== Compatible With: =====================================
    //= rAthena SVN
    //===== Description: =========================================
    //= Generic warper...
    //===== Additional Comments: =================================
    //=
    //============================================================

Format
------

### Script Name

-   line 2: the name of the script

`//===== rAthena Script =======================================`
`//= Warper`

### Author Name

-   line 4: the name of the author

`//===== By: ==================================================`
`//= Darkchild`

### Current [Version](/wikipedia:Software_versioning "wikilink")

-   line 6: the current version of the script
-   new scripts start at 1.0

`//===== Current Version: =====================================`
`//= 1.0`

### Compatible With

-   line 8: the SVN version of rAthena that this script is compatible with
-   if unsure, put *rAthena SVN*

`//===== Compatible With: =====================================`
`//= rAthena SVN`

-   if the script requires a script command or source modification that was recently added, indicate like so

`//===== Compatible With: =====================================`
`//= rAthena SVN, revision 12345+`

### Description

-   line 10: a short (one line) description of the script
-   try to limit description to 3 lines max

`//===== Description: =========================================`
`//= Generic warper...`

### Additional Comments

-   line 12+: additional remarks about the script, for example: more description, list of variables it uses, special installation/configuration instructions

`//===== Additional Comments: =================================`
`//= `
`//============================================================`

-   this section can also be used to list [Changelog](/wikipedia:Changelog "wikilink") messages
-   list them in numerical order, first at the top and last change at the bottom

`//===== Additional Comments: =================================`
`//= 1.0 by Darkchild`
`//= 1.1 by jabs`
`//= 1.2 by Lupus (placement fixed in Amatsu)`
`//= 1.3 fixed Louyang label typo, added warp and WARPRA into `
`//=     Nifleheim. Also sorted all names in alphabet order [Lupus]`
`//= 1.4 fixed morroc warp npc overlaying kafra [Aria]`
`//= 1.4a Added Ayothaya and Einbroch to list, and town Warpra's [Fredzilla]`
`//= 1.4b fixed Izlude warp npc overlaying BBS [Justin84]`
`//= 1.5 Added this NPC to more places [Lupus]`
`//= 1.6 Rewrote a lot. Changed the sprite, some locations. [Poki#3]`
`//= TODO Add an option for selecting the level of the dungeon. [Poki#3]`
`//= 1.7 Temporary? Added F_ClearGarbage to clear unused/outdated variables [Lupus]`
`//= 1.8 Removed Duplicates [Silent]`
`//= 1.9 Optimized for the greater good. [Kisuka]`
`//= 2.0 Fixed warp for AntHell and Yuno. [Kisuka]`
`//= 2.1 Moved AntHell warp agent to the new anthell entrance. [brianluau]`
`//============================================================`

Other Guidelines
----------------

-   Avoid using TABs in the script header because people use different text editors and their [tab size](/wikipedia:Tab_key "wikilink") might be different than yours.
-   If you want text to line up vertically, uses spaces.

`//= 1.3 fixed Louyang label typo, added warp and WARPRA into `
`//=     Nifleheim. Also sorted all names in alphabet order. [Lupus]`

-   Do **not** leave unnecessary trailing TABs/spaces at the end of lines. (A space after a word in the middle of a sentence that is split over multiple lines is okay).

`//= 1.3 fixed Louyang label typo, added warp and WARPRA into `
`//=     Nifleheim. Also sorted all names in alphabet order. [Lupus]`

-   If the script header is getting too long (more than 30 lines, or more than half your screen height), consider moving part or all of the Changelog from the [Additional Comments](/Script_header#Additional_Comments "wikilink") section to the bottom of the file.

[Category:RAthena](/Category:RAthena "wikilink")