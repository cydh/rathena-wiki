---
title: Addrid
permalink: /Addrid/
---

Syntax
------

-   **addrid**(<type>{,<flag>{,<parameters>}});

Description
-----------

This command will attach other RIDs to the current script without detaching the invoking RID. It returns 1 if successful and 0 upon failure.

To be more exact, this command will run the succeeding code for each player attached by it. For example, if 10 players were added by this command, the code after it will be ran an additional 10 times, each time with another RID attached.

<type> determines what RIDs are attached:

| Value      | Description                                                                                                   |
|------------|---------------------------------------------------------------------------------------------------------------|
| 0          | All players in the server.                                                                                    |
| 1          | All players in the map of the invoking player, or the invoking NPC if no player is attached.                  |
| 2          | Party members of a specified party ID. *Parameters: <party id>*                                               |
| 3          | Guild members of a specified guild ID. *Parameters: <guild id>*                                               |
| 4          | All players in a specified area of the map of the invoking player (or NPC). *Parameters: <x0>,<y0>,<x1>,<y1>* |
| Account ID | The specified account ID.                                                                                     |

<flag> can prevent certain players from being attached:

| Value | Description                                                    |
|-------|----------------------------------------------------------------|
| 0     | Players are always attached. (default)                         |
| 1     | Players currently running another script will not be attached. |

[Category:Script Command](/Category:Script_Command "wikilink")