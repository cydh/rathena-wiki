---
title: Instance create
permalink: /Instance_create/
---

Syntax
------

-   [instance_create](/instance_create "wikilink")("<instance name>");

Description
-----------

Creates an instance for the party of the attached player. The instance name, along with all other instance data, is read from . Upon success, the command generates a unique instance ID, duplicates all listed maps and NPCs, sets the alive time, and triggers the "OnInstanceInit" label in all NPCs inside the instance.

The command returns the instance ID upon success, and these values upon failure:

| Value | Description                                 |
|-------|---------------------------------------------|
| -1    | Invalid type.                               |
| -2    | Party not found.                            |
| -3    | Instance already exists.                    |
| -4    | No free instances (MAX_INSTANCE exceeded). |

See Also
--------

-   [Instancing](/Instancing "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")