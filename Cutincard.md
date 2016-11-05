---
title: Cutincard
permalink: /Cutincard/
---

Syntax
------

-   **cutincard** <item id>;

Description
-----------

This command displays the card illustration, also known as card cutin, for given card item. Specifying an item, which does not have an illustration associated might cause the client to crash or display errors.

The card pictures are loaded by the client from **data\\texture\\유저인터페이스\\cardbmp** and **data\\texture\\유저인터페이스\\illust** from both the GRF archive and data folder. The item-illustration associations are read by the server from **data\\num2cardillustnametable.txt** inside the server's GRF. If the file is missing, cutincard will not work.

Since card cutins are cutins as well, they are removed by using the [cutin](/cutin "wikilink") command.

Examples
--------

`cutincard 4001;`

Displays card illustration for a Poring Card.

[Category:Script Command](/Category:Script_Command "wikilink") [Category:Obsolete Script Command](/Category:Obsolete_Script_Command "wikilink")