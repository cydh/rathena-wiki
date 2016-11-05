---
title: Warpparty
permalink: /Warpparty/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [warpparty](/warpparty "wikilink") "<to_mapname>",<x>,<y>,<party_id>,{"<from_mapname>"};

Description
-----------

Warps a party to specified map and coordinate given the party ID, which you can get with [getcharid](/getcharid "wikilink")(1).
You can also request another party id, given a member's name with [getcharid](/getcharid "wikilink")(1,<player_name>).
You can use the following "map names" for special warping behavior:
**Random**: *All party members are randomly warped in their current map (as if they all used a fly wing).
* **SavePointAll**: *All party members are warped to their respective save point.
* **SavePoint**: *All party members are warped to the save point of the currently attached player (will fail if there's no playerattached).*
**Leader**: *All party members are warped to the leader's position. The leader must be online and in the current map-server for this to work.*
If you specify a from_mapname, warpparty will only affect those on that map

Example
-------

    mes "[Party Warper]";
    mes "Here you go!";
    close2;
    warpparty "prontera",150,100,getcharid(1);
    end;