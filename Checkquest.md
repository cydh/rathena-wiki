---
title: Checkquest
permalink: /Checkquest/
---

Syntax
------

-   **checkquest**(<ID>{,PLAYTIME|HUNTING})

Description
-----------

`If no additional argument supplied, return the state of the quest: `
`   -1 = Quest not started (not in quest log)`
`   0  = Quest has been given, but the state is "inactive"`
`   1  = Quest has been given, and the state is "active"`
`   2  = Quest completed`

If parameter "PLAYTIME" is supplied:

`   -1 = Quest not started (not in quest log)`
`   0  = the time limit has not yet been reached`
`   1  = the time limit has not been reached but the quest is marked as complete`
`   2  = the time limit has been reached`

If parameter "HUNTING" is supplied:

`   -1 = Quest not started (not in quest log)`
`   0  = you haven't killed all of the target monsters and the time limit has not been reached.`
`   1  = you haven't killed all of the target monsters but the time limit has been reached.`
`   2  = you've killed all of the target monsters`

Examples
--------

[`if`](/if "wikilink")` (`**`checkquest`**`(12059)== -1) `[`setquest`](/setquest "wikilink")` 12059;`

This checks the status of quest with ID 12059. If -1 is returned (-1 = Quest not started (not in quest log)) then the script will start the quest using [setquest](/setquest "wikilink").

[`set`](/set "wikilink")` .@etower_timer,`**`checkquest`**`(60200,PLAYTIME); // 1 week`
[`set`](/set "wikilink")` .@etower_timer2,`**`checkquest`**`(60201,PLAYTIME); // 4 hours`

This places the returned values of quest with ID 60200 and 60201 into 2 variables for later use in the NPC script.

[`if`](/if "wikilink")` (`**`checkquest`**`(3040)>=0) `[`erasequest`](/erasequest "wikilink")` 3040;`
[`if`](/if "wikilink")` (`**`checkquest`**`(3040) == -1) `[`setquest`](/setquest "wikilink")` 3040;`

This script checks the status of quest with ID 3040 and performs actions accordingly.
The first line uses [erasequest](/erasequest "wikilink") to erase the quest is the returned value is 0 (0 = Quest has been given, but the state is "inactive").
The second line will place the quest into the players quest log if the returned status is -1 (-1 = Quest not started (not in quest log)).

The following is a copy/paste from . The NPC dialogue has been cut short as it serves no purpose in this example.

`gef_fild05,80,149,3    script  Myu#08_hat  877,{`
`   `[`mes`](/mes "wikilink")` "[Myu]";`
`   `[`mes`](/mes "wikilink")` "Meow...";`
`   `[`emotion`](/emotion "wikilink")` 23;`
`   `[`next`](/next "wikilink")`;`
`   `[`if`](/if "wikilink")`(hatcat2008 == 0) {`
`       `[`mes`](/mes "wikilink")` "[Myu]";`
`       `[`mes`](/mes "wikilink")` "Oh? Aren't you an adventurer?";`
`       `[`mes`](/mes "wikilink")` "What brings you here? Ho, you are not here to harm Wild Roses, are you?";`
`       `[`mes`](/mes "wikilink")` "(Meow!)";`
`       `[`next`](/next "wikilink")`;`
`////////////////// Script Shortened //////////////////`
`       `[`mes`](/mes "wikilink")` "[Myu]";`
`       `[`mes`](/mes "wikilink")` "If you manage to do that, I will give you something precious which I really adore.";`
`       `[`next`](/next "wikilink")`;`
`       `[`switch`](/switch "wikilink")`(`[`select`](/select "wikilink")`("That sounds troublesome..:What should I do?")){`
`       `[`case`](/case "wikilink")` 1:`
`////////////////// Script Shortened //////////////////`
`       `[`case`](/case "wikilink")` 2:`
`           `[`mes`](/mes "wikilink")` "[Myu]";`
`           `[`mes`](/mes "wikilink")` "Of course take care of those Kobold Archers Meow!";`
`////////////////// Script Shortened //////////////////`
`           `[`next`](/next "wikilink")`;`
`           `[`switch`](/switch "wikilink")`(`[`select`](/select "wikilink")`("Isn't that too much?:That's easy")){`
`           `[`case`](/case "wikilink")` 1:`
`               `[`mes`](/mes "wikilink")` "[Myu]";`
`               `[`mes`](/mes "wikilink")` "..But they won't give up if we dont really teach them a lesson.";`
`               `[`mes`](/mes "wikilink")` "Well If you think it's too much for you, so be it.";`
`               `[`close`](/close "wikilink")`;`
`           `[`case`](/case "wikilink")` 2:`
`               `[`mes`](/mes "wikilink")` "[Myu]";`
`               `[`mes`](/mes "wikilink")` "But you have to keep one thing in mind and it is";`
`               `[`mes`](/mes "wikilink")` "obiously, NEVER EVER do any harm to Wild Roses.";`
`               `[`next`](/next "wikilink")`;`
`               `[`mes`](/mes "wikilink")` "[Myu]";`
`               `[`mes`](/mes "wikilink")` "If you do, it's all over for you.";`
`               `[`mes`](/mes "wikilink")` "So you better be careful.. ";`
`               `[`mes`](/mes "wikilink")` "Meow Meow Meow..";`
`               `[`set`](/set "wikilink")` hatcat2008,1;`
`               `[`setquest`](/setquest "wikilink")` 7054; `**`//Puts` `the` `quest` `7054` `into` `the` `players` `quest` `log`**
`               `[`setquest`](/setquest "wikilink")` 7055; `**`//Puts` `the` `quest` `7054` `into` `the` `players` `quest` `log`**
`               `[`close`](/close "wikilink")`;`
`           }`
`       }`
`   } `[`else`](/else "wikilink")` `[`if`](/if "wikilink")`(hatcat2008 == 1) {`
`       `[`if`](/if "wikilink")`(`**`checkquest`**`(7055,HUNTING) == 2) { `**`//Checks` `to` `see` `if` `you` `killed` `a` `Wild` `Rose`**
`           `[`mes`](/mes "wikilink")` "[Myu]";`
`           `[`mes`](/mes "wikilink")` "Did you think I didn't know what you have done?";`
`           `[`mes`](/mes "wikilink")` "Huh?";`
`           `[`next`](/next "wikilink")`;`
`////////////////// Script Shortened //////////////////`
`           `[`mes`](/mes "wikilink")` "(Meow..)";`
`           `[`set`](/set "wikilink")` hatcat2008,0;`
`           `[`erasequest`](/erasequest "wikilink")` 7054; `**`//Removes` `the` `quest` `7054` `from` `the` `players` `quest` `log`**
`           `[`erasequest`](/erasequest "wikilink")` 7055; `**`//Removes` `the` `quest` `7054` `from` `the` `players` `quest` `log`**
`           `[`close`](/close "wikilink")`;`
`       } `[`else`](/else "wikilink")` `[`if`](/if "wikilink")`(`**`checkquest`**`(7054,HUNTING) == 2) { `**`//Checks` `to` `see` `if` `you` `killed` `1000` `Kobold` `Archers`**
`////////////////// Script Shortened //////////////////`
`           `[`mes`](/mes "wikilink")` "Now, just take it and leave. Wild Roses feel uncomfortable with an adventurer around them.";`
`           `[`set`](/set "wikilink")` hatcat2008,2;`
`           `[`getitem`](/getitem "wikilink")` 5446,1;`
`           `[`erasequest`](/erasequest "wikilink")` 7054; `**`//Removes` `the` `quest` `7054` `from` `the` `players` `quest` `log`**
`           `[`erasequest`](/erasequest "wikilink")` 7055; `**`//Removes` `the` `quest` `7055` `from` `the` `players` `quest` `log`**
`           `[`close`](/close "wikilink")`;`
`       }`
`       `[`mes`](/mes "wikilink")` "[Myu]";`
`       `[`mes`](/mes "wikilink")` "You get it now, huh?";`
`       `[`mes`](/mes "wikilink")` "ONE THOUSAND TIMES! -chuckles-";`
`       `[`mes`](/mes "wikilink")` "(Meow Meow Meow~)";`
`       `[`next`](/next "wikilink")`;`
`       `[`mes`](/mes "wikilink")` "["+`[`strcharinfo`](/strcharinfo "wikilink")`(0)+"]";`
`       `[`mes`](/mes "wikilink")` "(What a weirdo.. Anyways..what's with that meow meow sound?)";`
`       `[`mes`](/mes "wikilink")` "Just keep your promises.";`
`       `[`mes`](/mes "wikilink")` "after the work is done...Ok?";`
`       `[`next`](/next "wikilink")`;`
`       `[`mes`](/mes "wikilink")` "[Myu]";`
`       `[`mes`](/mes "wikilink")` "Of course! Don't worry about that~";`
`       `[`close`](/close "wikilink")`;`
`   } `[`else`](/else "wikilink")` `[`if`](/if "wikilink")`(hatcat2008 == 2) {`
`////////////////// Script Shortened //////////////////`
`       `[`mes`](/mes "wikilink")` "our situation hasn't changed at all. Would you mind helping us once more?";`
`       `[`next`](/next "wikilink")`;`
`       `[`mes`](/mes "wikilink")` "Myu slides her neck mocking like she's slitting her throat.";`
`       `[`mes`](/mes "wikilink")` "Her mouth looks like it's saying.";`
`       `[`mes`](/mes "wikilink")` " 'O.N.E. T.H.O.U.S.A.N.D.' ";`
`       `[`next`](/next "wikilink")`;`
`       `[`switch`](/switch "wikilink")`(`[`select`](/select "wikilink")`("NO!:Sure.")) {`
`       `[`case`](/case "wikilink")` 1:`
`////////////////// Script Shortened //////////////////`
`       `[`case`](/case "wikilink")` 2:`
`           `[`mes`](/mes "wikilink")` "[Myu]";`
`           `[`mes`](/mes "wikilink")` "You know the drill right?";`
`           `[`mes`](/mes "wikilink")` "Never ever touch the Wild Roses, Only hunt down the Kobold Archers.";`
`           `[`mes`](/mes "wikilink")` "Give them 1,000 times despair!";`
`           `[`set`](/set "wikilink")` hatcat2008,1;`
`           `[`setquest`](/setquest "wikilink")` 7054; `**`//Puts` `the` `quest` `7054` `into` `the` `players` `quest` `log`**
`           `[`setquest`](/setquest "wikilink")` 7055; `**`//Puts` `the` `quest` `7055` `into` `the` `players` `quest` `log`**
`           `[`close`](/close "wikilink")`;`
`       }`
`   }`
`   `[`mes`](/mes "wikilink")` "[Myu]";`
`   `[`mes`](/mes "wikilink")` "Meow..";`
`   `[`mes`](/mes "wikilink")` "This Sunshine...makes me sleepy..";`
`   `[`close`](/close "wikilink")`;`
`}`

Related commands: [setquest](/setquest "wikilink"), [erasequest](/erasequest "wikilink"), [changequest](/changequest "wikilink"), [completequest](/completequest "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")