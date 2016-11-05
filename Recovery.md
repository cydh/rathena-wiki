---
title: Recovery
permalink: /Recovery/
---

Syntax
------

-   **recovery** <type>{,<option>,<revive_flag>{,<map name>}};

Description
-----------

This command will revive and fully restore the HP/SP of the selected characters. It returns 1 upon successful use.

| type          | option                               |
|---------------|--------------------------------------|
| **0: Player** | Character ID number                  |
| **1: Party**  | Party ID number                      |
| **2: Guild**  | Party ID number                      |
| **3: Map**    | Map name (a string)                  |
| **4: All**    | None (takes <revive_flag> as option) |

If no option is specified, the invoking player's character ID, party ID, guild ID, or map will be used.

<revive_flag> determines the action:

| flag  | Description                           |
|-------|---------------------------------------|
| **1** | Revive and heal all players (default) |
| **2** | Heal living players only              |
| **4** | Revive dead players only              |

<map name> can optionally be used to define a single map to execute the command on for types 1 (party) and 2 (guild).

Examples
--------

`// Only revive characters in invoking party on map morocc.`
`   `**`recovery`**` 1,getcharid(1),4,"morocc";`
`// Fully heal (don't revive) all members of invoking character's guild.`
`   `**`recovery`**` 2,getcharid(2),2;`
`// Revive and fully heal everyone in map prontera.`
`   `**`recovery`**` 3,"prontera";`
`// Only revive all dead characters on server.`
`   `**`recovery`**` 4,4;`

[Category:Script Command](/Category:Script_Command "wikilink")