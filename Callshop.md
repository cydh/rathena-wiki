---
title: Callshop
permalink: /Callshop/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [callshop](/callshop "wikilink") "<name>",<option>;

Description
-----------

These are a series of commands used to create dynamic shops. The callshop function calls a invisible shop (view -1) as if the player clicked on it.

The shop which is called by callshop (as long as an npcshop\* command is executed from that NPC (see note 1)) will trigger the labels [OnBuyItem](/OnBuyItem "wikilink") and [OnSellItem](/OnSellItem "wikilink"). These labels can take over handling for relatively the buying of items from the shop and selling the items to a shop. Via these labels you can customize the way an item is bought or sold by a player.

In the [OnBuyItem](/OnBuyItem "wikilink"), two arrays are set (@bought_nameid and @bought_quantity), which hold information about the name id (item id) sold and the amount sold of it. Same goes for the [OnSellItem](/OnSellItem "wikilink") label, only the variables are named different (@sold_nameid and @sold_quantity). An example on a shop comes with rAthena, and can be found in the file.

This example shows how to use the labels and their set variables to create a dynamic shop.

Note 1: These labels will only be triggered if a npcshop\* command is executed, this is because these commands set a special data on the shop npc,named master_nd in the source. The [OnSellItem](/OnSellItem "wikilink") and [OnBuyItem](/OnBuyItem "wikilink") are triggered in the NPC whose master_nd is given in the shop. This was found out thanks to 'Hondacrx', noticing the [OnBuyItem](/OnBuyItem "wikilink") wasn't triggered unless [npcshopitem](/npcshopitem "wikilink") was used. After rechecking the source, I found what caused this.

Parameters
----------

### Option

| Option | Description                              |
|--------|------------------------------------------|
| 0      | The normal window (buy, sell and cancel) |
| 1      | The buy window                           |
| 2      | The sell window                          |

Examples
--------

    //This will call the shop named DaShop and opens the buy menu.
    callshop "DaShop",1;