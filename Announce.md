---
title: Announce
permalink: /Announce/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [announce](/announce "wikilink") "Message",<flag>{,<color>};

Description
-----------

This command will broadcast a message to all or most players, similar to @kami/@kamib GM commands. The region the broadcast is heard in and the color the message will come up as will be determined by the flags.

Using this command for private messages to players is probably not that good an idea, but it can be used instead in NPCs to "preview" an announce.

Parameters
----------

### Flag

The flag values are coded as constants in db/const.txt to make them easier to use:

| Flag       | Value | Description                                                                                                                                                     |
|------------|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| bc_all    | 0     | Broadcast message is sent server-wide.                                                                                                                          |
| bc_map    | 1     | Message is sent to everyone in the same map.                                                                                                                    |
| bc_area   | 2     | Message is sent to players in the vicinity of the source.                                                                                                       |
| bc_self   | 3     | Message is sent only to current player.                                                                                                                         |
| bc_npc    | 8     | Broadcast source is the npc, not the player attached to the script (useful when a player is not attached or the message should be sent to those nearby the npc) |
| bc_yellow | 0     | The default is to send broadcasts in yellow color.                                                                                                              |
| bc_blue   | 16    | Alternate broadcast is displayed in blue color.                                                                                                                 |

### Color

The optional parameter, color, allows usage of broadcasts in any custom color. The color parameter is a single number which can be in hexadecimal notation. For example:

    //This will display a global announce in yellow. The color format is in RGB (0xRRGGBB).
    announce "This will be shown to everyone at all in yellow.",bc_all,0xFFFF00;

Examples
--------

    announce "This will be shown to everyone at all in yellow.",0;

    //This will be a private message to the player using the NPC that made the announcement
    announce "This is my message just for you",bc_blue|bc_self;

    //This will be shown on everyone's screen that is in sight of the NPC.
    announce "This is my message just for you people here",bc_area;