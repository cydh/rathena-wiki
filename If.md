---
title: If
permalink: /If/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [if](/if "wikilink") (<condition>) <statement>;
-   [if](/if "wikilink") (<condition>) { <statements> };

Description
-----------

This is the basic conditional statement command, and just about the only one available in this scripting language.

The condition can be any expression. All expressions resulting in a non-zero value will be considered True, including negative values. All expressions resulting in a zero are false.

If the expression results in True, the statement will be executed. If it isn't true, nothing happens and we move on to the next line of the script.

`   if (1)  mes "This will always print.";`
`   if (0)  mes "And this will never print.";`
`   if (5)  mes "This will also always print.";`
`   if (-1) mes "Funny as it is, this will also print just fine.";`

For more information on conditional operators see the operators section above. Anything that is returned by a function can be used in a condition check without bothering to store it in a specific variable:

`   if (strcharinfo(0) == "Daniel Jackson") mes "It is true, you are Daniel!";`

With the Advanced scripting engine, we got nested if's. That is:

    if (<condition>)
        dothis;
    else
        dothat;

If the condition doesn't meet, it'll do the action following the else. We can also group several actions depending on a condition, the following way:

    if (<condition) {
        dothis1;
        dothis2;
        dothis3;
    } else {
        dothat1;
        dothat2;
        dothat3;
        dothat4;
    }

Remember that if you plan to do several actions upon the condition being false, and you forget to use the curlies (the { } ), the second action will be executed regardless the output of the condition, unless of course, you stop the execution of the script if the condition is true (that is, in the first grouping using a return; , and end; or a close; )

Also, you can have multiple conditions nested or chained, and don't worry about limits as to how many nested if you can have, there is no spoon ;)

    if (<condition 1>)
        dothis;
    else if (<condition 2>){
        dotheother;
        do that;
        end;
    } else
        do this;

Examples
--------

        set .@var1,1;
        input .@var2;
        if(.@var1 == .@var2)
           close;
        mes "Sorry that is wrong";
        close;

        input .@var2;
        if(.@var2 != 1) mes "Sorry that is wrong";
        close;

Notice examples 1 and 2 have the same effect.

        mes "[Quest Person]";
        if(countitem(512) >= 1) {
           mes "Oh an apple, I didn't want it, I just wanted to see one";
           close;
        }
        // The number 512 was found from item_db, it is the item number for the Apple.
        mes "Can you please bring me an apple?";
        close;

        mes "[Multi Checker]";
        if(queststarted == 1 && countitem(512) >= 5) {
           // This will only be done if the quest has been started AND you have 5 apples with you
           mes "[Multi Checker]";
           mes "Well done you have started the quest of got me 5 apples";
           mes "Thank you";
           set queststarted,0;
           delitem 512,5;
           close;
        }
        mes "Please get me 5 apples";
        set queststarted,1;
        close;

        set .@var1,.@var1+1;
        mes "[Forgetful Man]";
        if (.@var == 1) mes "This is the first time you have talked to me.";
        if (.@var == 2) mes "This is the second time you have talked to me.";
        if (.@var == 3) mes "This is the third time you have talked to me.";
        if (.@var == 4) {
           mes "This is the forth time you have talked to me, but I think I am getting amnesia, I have forgotten about you.";
           set .@var,0;
        }
        close;

If you plan to something like this, better look at the '[switch](/switch "wikilink")' command.

        mes "[Person Checker]";
        if($name$ != null && $name$ == strcharinfo(0)) {
           mes "[Person Checker]";
           mes "You are the person that " +$name2$+ " just mentioned";
           mes "nice to meet you";
        } else if($name$ != null){
           mes "[Person Checker]";
           mes "You are not the person that " +$name2$+ " mentioned";
        } else {
           mes "Please tell me someones name";
           next;
           input $name$;
           set $name2$,strcharinfo(0);
           mes "[Person Checker]";
           mes "Thank you";
        }
        set $name$,null;
        set $name2$,null;
        close;

See '[strcharinfo](/strcharinfo "wikilink")' for explanation of what this function does.