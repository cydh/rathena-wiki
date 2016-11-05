---
title: Waitingroom2bg
permalink: /Waitingroom2bg/
---

Syntax
------

-   **waitingroom2bg**("<mapname>",<x>,<y>,"<Logout Event>","<Die Event>"{,"<npcname>"});

Description
-----------

This command is part of the Battleground System and creates a BG team with the players inside of a '[waitingroom](/waitingroom "wikilink")'.

You can choose which NPC to check for a '[waitingroom](/waitingroom "wikilink")' by setting the **<npcname>** value. This command will then create the BG team with **"<mapname>"**,**<x>**,**<y>** as respawn point and the given events (**"<Logout Event>"** and **"<Die Event>"**) will be executed whenever a team member logs out or dies, and returns the ID of the newly created team.

Also this command will create an array of temporary global variables:

| Array                  | Description                                                                                |
|------------------------|--------------------------------------------------------------------------------------------|
| **$@arenamembers\[\]** | is a global temporary number array which contains the account id of these BG team members. |
| **$@arenamembersnum**  | is the number of party members that were found.                                            |

Note that the names come in no particular order.

Be sure to use **$@arenamembersnum** to go through this array, and not '[getarraysize](/getarraysize "wikilink")', because it is not cleared between runs of '[waitingroom2bg](/waitingroom2bg "wikilink")'. If a team is created with 7 members, the array would have 7 elements. But if another one is created with only 5 members, the server will not clear the array for you, overwriting the values instead. So in addition to returning the 5 member names, the 6th and 7th elements from the last call remain, and you will get 5+2 members, of which the last 2 don't belong to the new team. **$@arenamembersnum** will always contain the correct number, (5) unlike '[getarraysize](/getarraysize "wikilink")()' which will return 7 in this case.

Examples
--------

The **waitingroom**:

`bat_room,253,97,4  script  Registration::TK_Recruit1   418,{`
`   end;`
[`OnInit`](/OnInit "wikilink")`:`
`   `**`waitingroom`**` "The Keeper 10 Players",10,"TK_Master::OnJoin1",1;`
`   `[`end`](/end "wikilink")`;`
`}`

Create the teams:

`   // ...`
`   `[`set`](/set "wikilink")` .@Team1, getwaitingroomstate(0,"TK_Recruit1");`
`   set .@Team2, getwaitingroomstate(0,"TK_Recruit2");`
`   `[`if`](/if "wikilink")`( .@Team1 < 10 || .@Team2 < 10 ){`
`       `[`mapannounce`](/mapannounce "wikilink")` "bat_room","The Keeper -- Team 1: " + .@Team1 + "/10, Team 2: " + .@Team2 + "/10",1,0x006400;`
`       end;`
`   }`
`   set $@TK_Teamid1,waitingroom2bg("bat_b01",390,10,"TK_Master::OnLogoutEvent","TK_Master::OnDieEvent","TK_Recruit1");`
`   set $@TK_Teamid2,waitingroom2bg("bat_b01",10,290,"TK_Master::OnLogoutEvent","TK_Master::OnDieEvent","TK_Recruit2");`
`   bg_warp $@TK_Teamid1,"bat_b01",390,10;`
`   bg_warp $@TK_Teamid2,"bat_b01",10,290;`
`   // ...`

[Category:Script_Command](/Category:Script_Command "wikilink") [Category:Battlegrounds_Command](/Category:Battlegrounds_Command "wikilink")