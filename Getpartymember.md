---
title: Getpartymember
permalink: /Getpartymember/
---

Syntax
------

-   [getpartymember](/getpartymember "wikilink") <party id>{,<type>};

Description
-----------

This command will find all members of a specified party and returns their names (or character id or account id depending on the value of "type") into an array of temporary global variables. There's actually quite a few commands like this which will fill a special variable with data upon execution and not do anything else.

Upon executing this,

| Type | Array                      | Description                                                                                                                        |
|------|----------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| 1    | **$@partymembername$\[\]** | is a global temporary string array which contains all the names of these party members (only set when type is 0 or not specified). |
| 2    | **$@partymembercid\[\]**   | is a global temporary number array which contains the character id of these party members (only set when type is 1).               |
| 3    | **$@partymemberaid\[\]**   | is a global temporary number array which contains the account id of these party members (only set when type is 2).                 |
| 4    | **$@partymembercount**     | is the number of party members that were found.                                                                                    |

The party members will (apparently) be found regardless of whether they are online or offline. Note that the names come in no particular order.

Be sure to use **$@partymembercount** to go through this array, and not '[getarraysize](/getarraysize "wikilink")', because it is not cleared between runs of '[getpartymember](/getpartymember "wikilink")'. If someone with 7 party members invokes this script, the array would have 7 elements. But if another person calls up the [NPC](/NPC "wikilink"), and he has a party of 5, the server will not clear the array for you, overwriting the values instead. So in addition to returning the 5 member names, the 6th and 7th elements from the last call remain, and you will get 5+2 members, of which the last 2 don't belong to the new guy's party. **$@partymembercount** will always contain the correct number, (5) unlike '[getarraysize](/getarraysize "wikilink")()' which will return 7 in this case.

Examples
--------

### Example 1

`// get the party member names`
[`getpartymember`](/getpartymember "wikilink")` `[`getcharid`](/getcharid "wikilink")`(1),0;`
`// It's a good idea to copy the global temporary $@partymember***** `
`// variables to your own scope variables because if you have pauses in this `
`// script (`[`sleep`](/sleep "wikilink")`, `[`sleep2`](/sleep2 "wikilink")`, `[`next`](/next "wikilink")`, `[`close2`](/close2 "wikilink")`, `[`input`](/input "wikilink")`, `[`menu`](/menu "wikilink")`, `[`select`](/select "wikilink")`, or `[`prompt`](/prompt "wikilink")`), `
`// another player could click this NPC, trigger '`[`getpartymember`](/getpartymember "wikilink")`', and `
`// overwrite the $@partymember***** `[`variables`](/Variables#Global_Variables "wikilink")`.`
[`set`](/set "wikilink")` .@count, $@partymembercount;`
[`copyarray`](/copyarray "wikilink")` .@name$[0], $@partymembername$[0], $@partymembercount;`
`// list the party member names`
[`for`](/for "wikilink")` (`[`set`](/set "wikilink")` .@i,0; .@i < .@count; `[`set`](/set "wikilink")` .@i, .@i+1) {`
`   `[`mes`](/mes "wikilink")` (.@i +1) + ". ^0000FF" + .@name$[.@i] + "^000000";`
`}`
[`close`](/close "wikilink")`;`

### Example 2

[`set`](/set "wikilink")` .register_num, 5; // How many party members are required?`
`// get the charID and accountID of character's party members`
[`getpartymember`](/getpartymember "wikilink")` `[`getcharid`](/getcharid "wikilink")`(1), 1;`
[`getpartymember`](/getpartymember "wikilink")` `[`getcharid`](/getcharid "wikilink")`(1), 2;`
[`if`](/if "wikilink")` ( $@partymembercount != .register_num ) {`
`   `[`mes`](/mes "wikilink")` "Please form a party of "+ .register_num +" to continue";`
`   `[`close`](/close "wikilink")`;`
`}`
`// loop through both and use '`[`isloggedin`](/isloggedin "wikilink")`' to count online party members`
[`for`](/for "wikilink")` ( `[`set`](/set "wikilink")` .@i, 0; .@i < $@partymembercount; `[`set`](/set "wikilink")` .@i, .@i +1 )`
`   `[`if`](/if "wikilink")` ( `[`isloggedin`](/isloggedin "wikilink")`( $@partymemberaid[.@i], $@partymembercid[.@i] ) )`
`       `[`set`](/set "wikilink")` .@count_online, .@count_online +1 ;`
`// We search `[`accountID`](/AID "wikilink")` & `[`charID`](/CID "wikilink")` because a single party can have multiple `
`// characters from the same account. Without searching through the charID, `
`// if a player has 2 characters from the same account inside the party but `
`// only 1 char online, it would count their online char twice.`
[`if`](/if "wikilink")` ( .@count_online != .register_num ) {`
`   `[`mes`](/mes "wikilink")` "All your party members must be online to continue";`
`   `[`close`](/close "wikilink")`;`
`}`
`// copy the array to prevent players cheating the system`
[`copyarray`](/copyarray "wikilink")` .@partymembercid, $@partymembercid, .register_num;`
[`mes`](/mes "wikilink")` "Are you ready ?";`
[`next`](/next "wikilink")`; // careful here`
[`select`](/select "wikilink")` "Yes";`
`// When a script hits a `[`next`](/next "wikilink")`, `[`menu`](/menu "wikilink")`, `[`sleep`](/sleep "wikilink")` or `[`input`](/input "wikilink")` that pauses the script, `
`// players can invite or /leave and make changes in their party. To prevent `
`// this, we call `[`getpartymember`](/getpartymember "wikilink")` again and compare with the original values.`
[`getpartymember`](/getpartymember "wikilink")` `[`getcharid`](/getcharid "wikilink")`(1), 1;`
[`if`](/if "wikilink")` ( $@partymembercount != .register_num ) {`
`   `[`mes`](/mes "wikilink")` "You've made changes to your party !";`
`   `[`close`](/close "wikilink")`;`
`}`
[`for`](/for "wikilink")` ( `[`set`](/set "wikilink")` .@i, 0; .@i < $@partymembercount; `[`set`](/set "wikilink")` .@i, .@i +1 ) {`
`   `[`if`](/if "wikilink")` ( .@partymembercid[.@i] != $@partymembercid[.@i] ) {`
`       `[`mes`](/mes "wikilink")` "You've made changes to your party !";`
`       `[`close`](/close "wikilink")`;`
`   }`
`}`
`// Finally, it's safe to start the event!`
[`warpparty`](/warpparty "wikilink")` "event_map", 0,0, `[`getcharid`](/getcharid "wikilink")`(1);`

[Category:Script Command](/Category:Script_Command "wikilink")