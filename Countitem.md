---
title: Countitem
permalink: /Countitem/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [countitem](/countitem "wikilink")(<itemid>);
-   [countitem](/countitem "wikilink")("Itemname");

Description
-----------

Countitem will return the number of items of <itemid> the invoking player holds in his inventory.
Like in [getitem](/getitem "wikilink"), you can also write the name of the item ("Name"-column in ItemDB).

Example
-------

    mes "You have "+countitem(501)+"Apples!";
    close;

Will print out the number of Apples the char holds...

    if(countitem("Apple")>=5){
     mes "This will only print if you have 5 or more Apples!";
     close;
    }