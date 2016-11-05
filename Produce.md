---
title: Produce
permalink: /Produce/
---

Syntax
------

-   [produce](/produce "wikilink") <item level>;

Description
-----------

This command will open a crafting window on the client connected to the invoking character. The 'item level' is a number which determines what kind of a crafting window will pop-up. You can see the full list of such item levels in which determines what can actually be produced. The window will not be empty only if the invoking character can actually produce the items of that type and has the appropriate raw materials in their inventory.

Valid item levels are:

| Value | Item Type                                                       |
|-------|-----------------------------------------------------------------|
| 1     | Level 1 Weapons                                                 |
| 2     | Level 2 Weapons                                                 |
| 3     | Level 3 Weapons                                                 |
| 21    | Blacksmith's Stones and Metals                                  |
| 22    | Alchemist's Potions, Holy Water, Assassin Cross's Deadly Poison |
| 23    | Elemental Converters                                            |

Examples
--------

**`produce`**` 1; //This will bring up a window similar to "Arrow Crafting", it will only show content `
`if you carry the required items to make a level 1 weapon.`

**`produce`**` 2; //This will bring up a window similar to "Arrow Crafting", it will only show content `
`if you carry the required items to make a level 2 weapon.`

**`produce`**` 3; //This will bring up a window similar to "Arrow Crafting", it will only show content `
`if you carry the required items to make a level 3 weapon`

[Category:Script Command](/Category:Script_Command "wikilink")