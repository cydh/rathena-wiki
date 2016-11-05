---
title: Getmercinfo
permalink: /Getmercinfo/
---

Syntax
------

-   **getmercinfo**(<type>\[, <char id>\]);

Description
-----------

Retrieves information about mercenary of the [currently attached](/RID "wikilink") character. If char ID is given, the information of that character is retrieved instead. Type specifies what information to retrieve and can be one of the following:

| Value | Type                                           |
|-------|------------------------------------------------|
| 0     | Database ID                                    |
| 1     | Class                                          |
| 2     | Name                                           |
| 3     | Faith value for this mercenary's guild, if any |
| 4     | Calls value for this mercenary's guild, if any |
| 5     | Kill count                                     |
| 6     | Remaining life time in msec                    |
| 7     | Level                                          |

If the character does not have a mercenary, the command returns "" for name and 0 for all other types.

Examples
--------

[`if`](/if "wikilink")`(`**`getmercinfo`**`(0))`
`{`
`    `[`mes`](/mes "wikilink")` "Looks like you've got a "+`**`getmercinfo`**`(2)+" as mercenary.";`
`}`
[`else`](/else "wikilink")
`{`
`    mes "Still running around without a companion?";`
`}`
[`close`](/close "wikilink")`;`

See Also
--------

-   [gethominfo](/gethominfo "wikilink")
-   [getmonsterinfo](/getmonsterinfo "wikilink")
-   [getpetinfo](/getpetinfo "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")