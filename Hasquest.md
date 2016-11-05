---
title: Hasquest
permalink: /Hasquest/
---

Syntax
------

-   **hasquest**(<Quest ID>);

Description
-----------

This command is part of the Questlog System and checks if the invoking character has the Quest with the selected ID or not.

Return Values
-------------

| Value | Description                           |
|-------|---------------------------------------|
| 0     | The character doesn't have the quest. |
| 1     | The character has the quest.          |

Examples
--------

[`if`](/if "wikilink")`(`**`hasquest`**`(50000))`
`   `[`mes`](/mes "wikilink")` "Yeah! You have the Quest with ID 50000";`
[`else`](/else "wikilink")
`   mes "You don't have the quest with ID 50000!";`

[Category:Script_Command](/Category:Script_Command "wikilink")