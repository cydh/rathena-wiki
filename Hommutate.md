---
title: Hommutate
permalink: /Hommutate/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   **hommutate** {<ID>};

Description
-----------

This command will try to mutate the invoking player's Homunculus into a Homunculus S. The Strange Embryo (ID 6415) is deleted upon success.

The command will fail if the invoking player does not have an evolved Homunculus at level 99 or above, if it is not in the embryo state (from the 'morphembryo' command), or if the invoking player does not possess a Strange Embryo. The /swt emotion is shown upon failure.

If the optional parameter <ID> is set, the invoking player's Homunculus will change into the specified Homunculus ID. Otherwise, a random Homunculus S will be chosen. See 'db/homunculus_db.txt' for a full list of IDs.

Returns 1 upon success and 0 for all failures.

Example
-------

Here is a sample script which might be a help to you:

[`set`](/set "wikilink")` .@h, `[`select`](/select "wikilink")`("Eira:Bayeri:Sera:Dieter:Elanor");`
[`if`](/if "wikilink")` (.@h) {`
`     `[`mes`](/mes "wikilink")` "I will mutate now your .@h";`
`     `[`next`](/next "wikilink")`;`
`     `**`hommutate`**` 6047+.@i;`
`}`
`     `[`else`](/else "wikilink")` `**`hommutate`**`;`
`     `[`close`](/close "wikilink")`;`