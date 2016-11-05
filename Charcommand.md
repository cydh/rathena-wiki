---
title: Charcommand
permalink: /Charcommand/
---

Syntax
------

-   **charcommand** <command>;

Description
-----------

NOTE: This command is changed a bit on newer trunk versions, scroll down a bit for the new version!

On older trunk versions and stable:

command is the name of the current character ([strcharinfo](/strcharinfo "wikilink")(0)) followed by ':' and the command and it's parameters.

Newer Trunk version:

The big change is that the character name is no longer needed. This also enabled the commands to run without a player attached (according to Lance).

Examples
--------

On older trunk versions and stable:

`//Will be executed as if a lvl 99 GM done the #option command.`
`charcommand strcharinfo(0)+":#option 0 0 0 Roy";`

Newer Trunk version:

`//this would do the same as above, but now doesn't need a player attached by default.`
`charcommand "#option 0 0 0 Roy";`

[Category:Script Command](/Category:Script_Command "wikilink") [Category:Obsolete Script Command](/Category:Obsolete_Script_Command "wikilink")