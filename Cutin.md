---
title: Cutin
permalink: /Cutin/
---

Syntax
------

-   **cutin** &lt;"file name"&gt;, <position>;

Description
-----------

This command will display a picture, usually an [NPC](/NPC "wikilink") illustration, also called cutin, for the [currently attached](/RID#Usage "wikilink") client. The *position* parameter determines the placement of the illustration and takes following values:

| Value | Description                                                    |
|-------|----------------------------------------------------------------|
| 0     | Bottom-Left Corner                                             |
| 1     | Bottom-Middle                                                  |
| 2     | Bottom-Right Corner                                            |
| 3     | Middle of screen in a movable window with an empty title bar.  |
| 4     | Middle of screen without the window header, but still movable. |

The picture is read from **data\\texture\\유저인터페이스\\illust**, from both the [GRF](/GRF "wikilink") archive and data folder, and is required to be a bitmap. The file extension **.bmp** can be omitted. Magenta color () is considered transparent. There is no limit placed on the size of the illustrations by the client, although loading of large pictures (about 700x700 and larger) causes the client to freeze shortly (lag). Typically the size is about 320x480. New illustrations can be added by just putting the new file into the location above.

The client is able to display only one **cutin** at the same time and each new one will cause the old one to disappear. To delete the currently displayed illustration without displaying a new one, an empty file name and position 255 must be used.

Examples
--------

`cutin "kafra_7",2;`

Displays the Comodo Kafra illustration in lower right corner.

[`mes`](/mes "wikilink")` "See you.";`
[`close2`](/close2 "wikilink")`;`
`cutin "",255;`
[`end`](/end "wikilink")`;`

Typical way to end a script, which displayed an illustration during a dialog with a player.

[Category:Script Command](/Category:Script_Command "wikilink")