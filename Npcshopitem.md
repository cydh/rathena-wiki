---
title: Npcshopitem
permalink: /Npcshopitem/
---

Syntax
------

-   [npcshopitem](/npcshopitem "wikilink") "<name>",<item id>,<price>{,<item id>,<price>{,<item id>,<price>{,...}}}

Description
-----------

This command lets you override the contents of an existing NPC shop or cashshop. The current sell list will be wiped, and only the items specified with the price specified will be for sale.

The function returns 1 if shop was updated successfully, or 0 if not found.

Note that you cannot use -1 to specify default selling price!

Examples
--------

The code below will replace the price of Red Potion to 5000z and Orange Potion to 6000z when [WoE](/WoE "wikilink") starts.

    prontera,100,200,4 shop    SampleShop  46,501:-1,502:-1

    -   script  NPCShopItem -1,{

    OnAgitStart:
        npcshopitem "SampleShop",501,5000,502,6000;
        end;
    }

[Category:Script Command](/Category:Script_Command "wikilink")