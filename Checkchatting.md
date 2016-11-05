---
title: Checkchatting
permalink: /Checkchatting/
---

Syntax
------

-   [checkchatting](/checkchatting "wikilink")({"<player name>"});
-   [checkvending](/checkvending "wikilink")({"<player name>"});

Description
-----------

Checks if the player is vending or in a chatroom. Name is optional, and defaults to the attached player if omitted.

| Value | Description                             |
|-------|-----------------------------------------|
| 0     | The player is not chatting/vending.     |
| 1     | The player is chatting/vending.         |
| 2     | The player is vending using @autotrade. |

Return value returns respectively as what your function is. (e.g.: if the value of checkchatting() = 1 but checkvending() = 0, then he is currently chatting, not vending)

Examples
--------

`//This will check if Aaron is vending, and if so, put a message in front`
`//of the attached player saying Aaron is vending.`
[`if`](/if "wikilink")` (`[`checkvending`](/checkvending "wikilink")`("Aaron"))`
`   `[`mes`](/mes "wikilink")` "Aaron is currently vending!";`
`//This will check if the attached player in a chat room or not.`
[`if`](/if "wikilink")` (`[`checkchatting`](/checkchatting "wikilink")`())`
`   `[`mes`](/mes "wikilink")` "You are currently chatting!";`

[Category:Script Command](/Category:Script_Command "wikilink")