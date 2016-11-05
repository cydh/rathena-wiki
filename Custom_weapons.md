---
title: Custom weapons
permalink: /Custom_weapons/
---

The ID
------

Why the ID first? The ID controls what type of weapon sprite is displayed. Going outside the ID range will cause you to "punch" when attacking.

Open your and find the section with the weapon type you need. The allowable range is usually obvious.

| Item ID     | Item Type                |
|-------------|--------------------------|
| 1100-1149   | One-Handed Sword         |
| 1150-1199   | Two-Handed Sword         |
| 1200-1249   | Knife                    |
| 1250-1299   | Katar                    |
| 1300-1349   | One-Handed Axe           |
| 1350-1399   | Two-Handed Axe           |
| 1400-1449   | One-Handed Spear         |
| 1450-1499   | Two-Handed Spear         |
| 1500-1549   | Mace                     |
| 1550-1599   | Book                     |
| 1600-1649   | Rod                      |
| 1700-1749   | Bow                      |
| 1750-1799   | Arrow                    |
| 1800-1849   | Knuckle                  |
| 1900-1949   | Instrument               |
| 1950-1999   | Whip                     |
| 13000-13099 | Knife                    |
| 13100-13149 | Handgun                  |
| 13150-13199 | Other Gunslinger Weapons |
| 13300-13399 | Shuriken                 |
| 13400-13499 | One-Handed Sword         |

### Example

To make a custom bow, searching for "Bows" in item_db shows that bow IDs start at 1701 and end at 1749. Since there are no remaining IDs, commenting out an unused bow would work.

Otherwise, skip to the next set of bows, which start at 18101. Select an open ID in that range.

The Sprite
----------

The client requires a sprite for every job the weapon can be used by. Some programs can automatically organize the files:

-   [clydelion's Sprite Name Generator](http://rathena.org/board/files/file/2494-ra-sprite-name-gen/)
-   [Myzter's Sprite Name Generator](http://rathena.org/board/files/file/2386-ea-sprite-name-generator/)

Don't forget to give the weapon an icon in **/sprite/¾ÆÀÌÅÛ/**, as well as an inventory icon and collection image in **/texture/À¯ÀúÀÎÅÍÆäÀÌ½º/item/** and **/texture/À¯ÀúÀÎÅÍÆäÀÌ½º/collection/**.

Other Client Data
-----------------

Lastly, the client data tables need to be filled out:

-   **idnum2itemdesctable.txt**: Identified item description.
-   **idnum2itemdisplaynametable.txt**: Identified item display name.
-   **idnum2itemresnametable.txt**: Identified sprite name.
-   **itemslotcounttable.txt**: Number of weapon slots, if necessary (skip if 0).
-   **num2itemdesctable.txt**: Unidentified item description, if necessary.
-   **num2itemdisplaynametable.txt**: Unidentified item display name, if necessary.
-   **num2itemresnametable.txt**: Unidentified sprite name, if necessary.

*And... you are done!*

Additionally for the sprite to display you can place the custom weapon sprites in the following folder "data/sprite/ÀÎ°£Á·"

|                  |                                                |
|------------------|------------------------------------------------|
| ´ÑÀÚ             | Ninja weapon sprites                           |
| ¸¶¹ý»ç           | Mage weapon sprites                            |
| ¸ùÅ©             | Monk weapon sprites                            |
| ¿¬±Ý¼ú»ç         | Alchemist weapon sprites                       |
| ¿î¿µÀÚ           | GM Weapon sprites                              |
| ±â»ç             | Knight weapon sprites                          |
| ±Ã¼ö             | Archer weapon sprites                          |
| »óÀÎ             | Merchant weapon sprites                        |
| °Ç³Ê             | Gunslinger weapon sprites                      |
| °Ë»ç             | Swordsman weapon sprites                       |
| µµµÏ             | Thief weapon sprites                           |
| ·Î±×             | Rogue weapon sprites                           |
| ¼¼ÀÌÁö           | Sage weapon sprites                            |
| ¼ºÁ÷ÀÚ           | Acolyte weapon sprites                         |
| ½´ÆÛ³ëºñ½º       | Super novice weapon sprites                    |
| ½ÅÆäÄÚÅ©·ç¼¼ÀÌ´õ | Crusader weapon sprites (when mounted on peco) |
| ¾î¼¼½Å           | Assassin weapon sprites                        |
| ¹«Èñ             | Dancer weapon sprites                          |
| ¹Ùµå             | Bard weapon sprites                            |
| Á¦Ã¶°ø           | Blacksmith weapon sprites                      |
| À§Àúµå           | Wizard weapon sprites                          |
| Å©·ç¼¼ÀÌ´õ       | Crusader weapon sprites                        |
| ÆäÄÚÆäÄÚ_±â»ç   | Knight weapon sprites (when mounted on peco)   |
| ÃÊº¸ÀÚ           | Novice weapon sprites                          |
| ÇÁ¸®½ºÆ®         | Priest weapon sprites                          |
| ÇåÅÍ             | Hunter weapon sprites                          |

Troubleshooting
---------------

**Q: Weapon is an Unknown Item.**

A: An error in resnametable. The client is not reading any value, so it becomes unknown.

**Q: The weapon sprite shows fine when standing, turns to punches when attacking.**

A: The ID for the weapon isn't in the allowed range. Make sure the value is correct.

**Q: The weapon sprite doesn't show at all.**

A: Re-check file/folder names and placement.

[Category:Customization](/Category:Customization "wikilink")