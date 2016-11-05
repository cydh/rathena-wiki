---
title: Getwaitingroomstate
permalink: /Getwaitingroomstate/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   **getwaitingroomstate**(<information type>{,"<NPC object name>"})

Description
-----------

This function will return information about the waiting room state for the attached waiting room or for a waiting room attached to the specified NPC if any.

The valid information types are:

| Value | Description                                                                                                           |
|-------|-----------------------------------------------------------------------------------------------------------------------|
| 0     | Number of users currently chatting.                                                                                   |
| 1     | Maximum number of users allowed.                                                                                      |
| 2     | Will return 1 if the waiting room has a trigger set, 0 otherwise.                                                     |
| 3     | Will return 1 if the waiting room is currently disabled, 0 otherwise.                                                 |
| 4     | The Title of the waiting room (string)                                                                                |
| 5     | Password of the waiting room, if any. Pointless, since there is no way to set a password on a waiting room right now. |
| 16    | Event name of the waiting room (string)                                                                               |
| 32    | Whether or not the waiting room is full.                                                                              |
| 33    | Whether the amount of users in the waiting room is higher than the trigger number.                                    |

Example
-------

Here is a sample script which might be a help to you:

` `[`if`](/if "wikilink")`(!`**`getwaitingroomstate`**`(32,"Heero Yuy"))`
`     `[`mes`](/mes "wikilink")` "The room is currently full."`
`     `[`close`](/close "wikilink")`;`
` }`