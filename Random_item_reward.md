---
title: Random item reward
permalink: /Random_item_reward/
---

Description
-----------

Rewards the player with a random item from a list.

Examples
--------

### Method 1: Item Group

By using item group, item chance to be gained can be decided. First, must decide ID for item group, edit the [const.txt](https://github.com/rathena/rathena/blob/master/db/const.txt) file. Example,

`IG_TestRandomItem  392`

Maximum Item Group ID is 399 as defined in [\#define MAX_ITEMGROUP 400](https://github.com/rathena/rathena/blob/master/src/map/itemdb.h#L26) Then put the item list on [item_group_db.txt](https://github.com/rathena/rathena/blob/master/db/import/item_group_db.txt) with format

`//GroupID,ItemID,Rate{,Amount,Random,isAnnounced,Duration,isNamed,isBound}`
`IG_TestRandomItem,607,10`
`IG_TestRandomItem,608,5`
`IG_TestRandomItem,678,7`

Then use script command [getrandgroupitem](/getrandgroupitem "wikilink")

`getrandgroupitem IG_TestRandomItem,1;`

If the item list is added when server is running, just use [@reloaditemdb](/@reloaditemdb "wikilink"). More info can be found on [Item Group Documentation](https://github.com/rathena/rathena/blob/master/doc/item_group.txt)

### Method 2: F_Rand Function

This function is one of many useful functions in [Global_Functions.txt](https://github.com/rathena/rathena/blob/master/npc/other/Global_Functions.txt) file.

`//////////////////////////////////////////////////////////////////////////////////`
`// Returns a random argument.`
`// -- callfunc "F_Rand",arg0,arg1,...`
`// Example:`
`//    // You can use it to pick a random number from a list:`
`//    set @itemIDfromList, callfunc("F_Rand",1129,1222,1163,1357,1360,1522,1811,1410);`
`//////////////////////////////////////////////////////////////////////////////////`
`function   script  F_Rand  {`
`   return getarg(rand(getargcount()));`
`}`

*How to use?* Just use like at the example, call the F_Rand function then follow the item ID, the rate for each item to shows up is 1/n. Example usage can we see in item_db.txt,

`12136,Women's_Bundle,Women's Bundle,2,0,,100,,,,,0xFFFFFFFF,63,2,,,,,,{`
`getitem callfunc("F_Rand",558,529,2668,7518),1; },{},{}`

### Method 3: Using Array

    // begin of the script
    setarray .@RandItem[0],501,502,503,504,505;
    set .@RandItemCount,getarraysize(.@RandItem);
    getitem(.@Randitem[rand(.@RandItemCount)],1);
    // end of the script

-   **.@RandItem\[\]** is an array that stores the available item rewards.
    -   .@RandItem\[0\] =&gt; *501*
    -   .@RandItem\[1\] =&gt; *502*
    -   .@RandItem\[2\] =&gt; *503*
    -   .@RandItem\[3\] =&gt; *504*
    -   .@RandItem\[4\] =&gt; *505*
-   **.@RandItemCount** stores length of *.@RandItem\[\]* array
-   **rand(<number>)** results a random number from *0* until *<number> -1*. See [Rand](/Rand "wikilink")
-   **getitem(<item_id>,<amount>)** gives to player an item with id *<item_id>*. See [Getitem](/Getitem "wikilink") or maybe you can use [Getitem2](/Getitem2 "wikilink") too.

[Category:Scripting Tips and Tricks](/Category:Scripting_Tips_and_Tricks "wikilink")