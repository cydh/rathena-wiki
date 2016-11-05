---
title: Getmapguildusers
permalink: /Getmapguildusers/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   **getmapguildusers**("<Map_name>",<guild_id>);

Description
-----------

This function will return the number of users of the guild_id currently located on the specified map.

Example 1
---------

`// This will return the number of users of the guild_id 1 that are in payon.`
[`mes`](/mes "wikilink")` "You have "+`**`getmapguildusers`**`("payon",1)+" guild members in Payon.";`