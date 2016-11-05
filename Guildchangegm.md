---
title: Guildchangegm
permalink: /Guildchangegm/
---

Syntax
------

-   **guildchangegm**(<guild id>,<new master's name>)

Description
-----------

This function will change the Guild Master of a guild. The ID is the Guild's ID, and the new Guild Master's name must be passed.

Returns 1 on success, 0 otherwise.

Examples
--------

Lets say, that my char's name is -Caleb-, and i'm the Guild Master of "Wikithena" with Guild ID: 1324. I'm going to transfer ownership of the guild to a guy called Akkarin. This is what we can do:

[`mes`](/mes "wikilink")` "Hey "+`[`strcharinfo`](/strcharinfo "wikilink")`(0)+"!";`
[`set`](/set "wikilink")` @GID,`[`getcharid`](/getcharid "wikilink")`(2); '''//Get the ID of the Guild you're in, if any`
`   `[`if`](/if "wikilink")`(@GID==0) `[`goto`](/goto "wikilink")` L_NoGuild;`
`   `[`if`](/if "wikilink")`(`[`strcharinfo`](/strcharinfo "wikilink")`(0)==`[`getguildmaster`](/getguildmaster "wikilink")`(@GID)) `[`goto`](/goto "wikilink")` L_GuildMaster;`
`   `[`mes`](/mes "wikilink")` "You need to be the Guild Master of the Guild you want to transfer ownership of.";`
`   close;`
`L_GuildMaster:`
`   `[`mes`](/mes "wikilink")` "So you wanna change ownership huh?! This can be arranged :)";`
`   `[`next`](/next "wikilink")`;`
`   mes "All I need you to do is type in the name of the character you want to be the new Guild Master.";`
`   `[`input`](/input "wikilink")` @newgm$; `**`//Here` `you` `would` `type` `the` `name` `Akkarin`**
`   if(`[`getcharid`](/getcharid "wikilink")`(0,@newgm$) == 0) goto L_NotExist; `**`//Check` `to` `see` `if` `"Akkarin"` `actually` `exisits`**
`   mes "Ah, so you want "+@newgm+" to be the new Guild Master of "+`[`GetGuildName`](/GetGuildName "wikilink")`(@GID)+"?"; `**`//Fetch` `the` `name` `of` `the` `guild` `using` `the` `Guild` `ID` `and` `getguildname().`**
`   next;`
`   `[`switch`](/switch "wikilink")` (`[`select`](/select "wikilink")`(" - Yes, do it!: - I'll need to think about it..")) {`
`   `[`case`](/case "wikilink")` 1:`
`       if(`**`guildchangegm`**`(@GID,@newgm$)) == 1){ '''//If command returned a success value (1)`
`           mes "Awesome, you're no longer in-charge!";`
`       } else {`
`           mes "Something went wrong, and i don't know why D:!";`
`       }`
`       `[`close`](/close "wikilink")`;`
`   `[`case`](/case "wikilink")` 2:`
`       mes "Come back when you've made up your mind!";`
`       `[`close`](/close "wikilink")`;`
`   }`
`L_NoGuild:`
`   mes "You need to be in a guild first o.O";`
`   close;`
`L_NotExist:`
`   mes "That character doesn't exist. Make sure you've typed their name correctly!";`
`   close;`

[Category:Script_Command](/Category:Script_Command "wikilink")