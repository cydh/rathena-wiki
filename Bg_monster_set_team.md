---
title: Bg monster set team
permalink: /Bg_monster_set_team/
---

Syntax
------

-   [bg_monster_set_team](/bg_monster_set_team "wikilink") <GID>,<Battle Group>;

Description
-----------

This command will change the allegiance if a monster in battlegrounds. [GID](/GID "wikilink") can be set when spawning the monster via the [bg_monster](/bg_monster "wikilink") command.

Examples
--------

`   `[`end`](/end "wikilink")`;`
`OnEnable:`
`   `[`mapannounce`](/mapannounce "wikilink")` "A guardian has been summoned for Battle Group 2!",bc_map,"0xFFCE00";`
`   `[`set`](/set "wikilink")` $@Guardian, `[`bg_monster`](/bg_monster "wikilink")`($@BG_2,"bat_a01",268,204,"Guardian",1949,"NPCNAME::OnMyMobDead");`
`   `[`initnpctimer`](/initnpctimer "wikilink")`;`
`   `[`end`](/end "wikilink")`;`
[`OnTimer`](/OnTimer "wikilink")`1000:`
`   `[`stopnpctimer`](/stopnpctimer "wikilink")`;`
`   `[`mapannounce`](/mapannounce "wikilink")` "Erm, sorry about that! This monster was meant for Battle Group 1.",bc_map,"0xFFCE00";`
`   `[`bg_monster_set_team`](/bg_monster_set_team "wikilink")` $@Guardian, $@BG_1;`
`   `[`end`](/end "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink") [Category:Battlegrounds_Command](/Category:Battlegrounds_Command "wikilink")