---
title: Gethominfo
permalink: /Gethominfo/
---

Syntax
------

-   **gethominfo**(<type>);

Description
-----------

Retrieves information about homunculus of the [currently attached](/RID "wikilink") character. Type specifies what information to retrieve and can be one of the following:

| Value | Description                                                 |
|-------|-------------------------------------------------------------|
| 0     | Database ID                                                 |
| 1     | Class                                                       |
| 2     | Name                                                        |
| 3     | Friendly level (intimacy score), 100000 is full loyalty     |
| 4     | Hungry level, 100 is completely full                        |
| 5     | Rename flag. 0 means this homunculus has not been named yet |
| 6     | Level                                                       |

If the character does not have a homunculus, the command returns "null" for name and 0 for all other types.

Examples
--------

[`if`](/if "wikilink")`(gethominfo(0))`
`{`
`    `[`mes`](/mes "wikilink")` "That's some sweet "+gethominfo(2)+" you have there.";`
`}`

See Also
--------

-   [getmercinfo](/getmercinfo "wikilink")
-   [getmonsterinfo](/getmonsterinfo "wikilink")
-   [getpetinfo](/getpetinfo "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")