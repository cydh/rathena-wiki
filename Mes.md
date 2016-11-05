---
title: Mes
permalink: /Mes/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [mes](/mes "wikilink") "<message>";
-   [mes](/mes "wikilink") "<Line 1>","<Line 2>","<Line 3>";
-   [mes](/mes "wikilink") "<message>"+<variable> or command +"<message>";

Description
-----------

The most basic scripting command.
Displays a window with **<message>** in it to the invoking character, if the window already exists, it will just display the given message.
Notice that mes does not create a *next* or *close* button, so you have to create one using the [next](/next "wikilink") or [close](/close "wikilink") command, otherwise the player will be stuck in your script.
Use the + operator to give out multiple messages combined with variables or some commands(for example [countitem](/countitem "wikilink"), [getitemname](/getitemname "wikilink") or [strcharinfo](/strcharinfo "wikilink"))in one mes.
Use "^<Red><Green><Blue> " in front of the message to give **<message>** a color.
<Red><Green><Blue> stand for three hexadecimal numbers, representing the color components of Red Green and Blue in the wanted colour, like a html-code(see examples).
Do not forget to set the color to black again, by putting "^000000" after your message, exept you want to color your whole text...
Be careful: <span style="color:#ff00ff>Magenta</span> (ff00ff) is considered as transparent in the client, using it in a Dialogue will result in a weird (or funny) effect.

Examples
--------

    mes "Hello World";
    //Will open up a text box with:

Hello World

    mes "Hello 1","Hello 2","Hello 3";
    // This will Generate 3 lines

Hello 1
Hello 2
Hello 3

    mes "Hello"+strcharinfo(0)+", how are you?";
    // Will upon up a textbox printing:

Hello Charname, how are you?

    mes "^FF0000 Hello World^000000";
    //Will open up a text box with

<span style="color:#FF0000">Hello World</span>

    mes "\'Hello!\'";
    // use \as prefix to include Symbols:
    // will print:

'Hello!'