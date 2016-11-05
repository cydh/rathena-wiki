---
title: Defpattern
permalink: /Defpattern/
---

Syntax
------

-   **defpattern** <set number>,&lt;"regular expression pattern"&gt;,&lt;"event label"&gt;;

Description
-----------

This command defines a [PCRE](/PCRE "wikilink") pattern in given pattern set, which triggers an event, when a player chat line matches the [regular expression](/wikipedia:Regular_expression "wikilink"). Parameter *set number* can be any number to identify the set, to add the pattern to. The *event label* must be inside the same NPC, as the defpattern command. Typically this command is called in the [OnInit](/OnInit "wikilink") label.

Initially a newly created pattern set is disabled and must be enabled with [activatepset](/activatepset "wikilink"), before it starts to match chat against the patterns. Once a pattern set is enabled, all public chat in the vicinity of the NPC is matched against all patterns inside the set, and if one of them matches, *event label* is called. Each match inside the PCRE pattern will result in a variable being set, but at most 10 ($@p1$ through $@p9$, and $@p0$ for the entire matched string), before the event label script is run.

To reset a pattern set, [deletepset](/deletepset "wikilink") must be used to delete the old set, and defpattern to populate the set with new patterns.

Examples
--------

`prontera,150,150,0 script  Strange Spot    -1,{`
`    `[`mes`](/mes "wikilink")` "^808080You wonder, what this could be for...^00000";`
`    `[`close`](/close "wikilink")`;`
`OnHealPlayer:`
`    `[`percentheal`](/percentheal "wikilink")` 100, 100;`
`    `[`specialeffect2`](/specialeffect2 "wikilink")` EF_HEAL;`
`    `[`end`](/end "wikilink")`;`
`OnInit:`
`    defpattern 1, "([^:]+):.*\\sheal plz(\\s.*)?", "OnHealPlayer";`
`    `[`activatepset`](/activatepset "wikilink")` 1;`
`}`

This makes the NPC heal everyone in it's vicinity, who says "heal plz".

See also , which extensively demonstrates the usage of PCRE commands.

[Category:Script Command](/Category:Script_Command "wikilink")