---
title: Guardian
permalink: /Guardian/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   **guardian** "<map name>",<x>,<y>,"<name to show>",<mob id>{,"<event label>"{,<guardian index>}};

Description
-----------

This command is *roughly* equivalent to '[monster](/Monster "wikilink")', but is meant to be used with castle guardian monsters and will only work with them. It will set the guardian characteristics up according to the castle's investment values and set the things up that only castle guardians need.

**Since trunk :** Returns the id of the mob or 0 if an error occurred. When 'guardian index' isn't supplied it produces a temporary guardian.

Temporary guardians are not saved with the castle and can't be accessed by '[guardianinfo](/Guardianinfo "wikilink")'.