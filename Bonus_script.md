---
title: Bonus script
permalink: /Bonus_script/
---

Syntax
------

-   **bonus_script** "
    <script code>
    ",<duration>{,<flag>{,<type>{,<char_id>}}};

Description
-----------

This command will attach a script to a player for a given duration, in seconds. After that time, the script will automatically expire. The same bonus cannot be stacked. By default, this bonus will be stored on \`bonus_script\` table when player logs out.

Note that the maximum number of 'bonus_script' commands that can run simultaneously for a player is 10 (MAX_PC_BONUS_SCRIPT in 'src/map/pc.h').

| Flag | Description                  |
|------|------------------------------|
| &1   | Remove when dead.            |
| &2   | Removable by Dispell.        |
| &4   | Removable by Clearance.      |
| &8   | Remove when player logs out. |
||

| Type | Description |
|------|-------------|
| 0    | Buff        |
| 1    | Debuff      |

Example
-------

`// Apple gives you +5 Str bonus for 1 minute when it's consumed.`
`512,Apple,Apple,0,15,,20,,,,,0xFFFFFFFF,63,2,,,,,,{ bonus_script "{ bonus bStr,5; }",60; },{},{}`

[Category:Script Command](/Category:Script_Command "wikilink")