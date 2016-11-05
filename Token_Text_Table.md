---
title: Token Text Table
permalink: /Token_Text_Table/
---

A text table format used for the [Ragnarok Online](/Ragnarok_Online "wikilink") client. It is used for organizing text data into columns and rows, mostly for id-description relations. It usually has the file extension **.txt** and can be found inside and outside the [GRF](/GRF "wikilink").

File Format
-----------

The files are plain text files, where rows and columns are separated by the token character [\#](/wikipedia:Hash_symbol "wikilink"). It can be edited with every text editor like Notepad. Make sure, that the file is not stored in [Unicode](/wikipedia:Unicode "wikilink") or [UTF-8](/wikipedia:UTF-8 "wikilink").

The amount of columns is fixed for each file, that uses this file format. Rows are either limited by available memory or by hard-coded limits, as seen below. Note that all of these limits can be lifted by hexing the client. Whether line breaks are allowed within a cell or not depends on each file as well. Multi-line cells support using \# character inside the text, as long it is followed by a **space character**. Contrary to that, all other \# characters must be followed by either a new line or a non-spacing character.

### Examples

1-column table (CardPostfixNameTable)

    4039#
    4041#
    4042#
    4046#
    4050#

1-column table multi-line (TipOfTheDay)

    /savechat : saves chat as text file.
    #
    You can select a type of mini-map using ctrl+[*],between transparency and opacity.
    #
    You can change the view of character with dragging a mouse while holding right button and pressing shift key.
       Double clicking right button on a mouse enables to return the view to default one.
    #

2-column table (IdNum2ItemDisplayNameTable)

    512#Apple#
    513#Banana#
    514#Grape#

2-column multi-line table (IdNum2ItemDescTable)

    1071#
    A test tube that contains some sort of unidentified fluid.
    ^ffffff_^000000
    Weight :^777777 3^000000
    #
    1072#
    It's a personal letter written by Mahnsoo, chief of the Merchant Guild.
    ^ffffff_^000000
    Weight :^777777 1^000000
    #
    1073#
    A delivery voucher with the serial number # 2485741
    ^ffffff_^000000
    Weight :^777777 1^000000
    #

### Comments

You may insert comments inside the file by putting **//** at the beginning of a line. The comment then spans to the end of that line. Trailing comments (not starting at beginning of a line) will not work. Example:

    row1#
    // Disabled because it does not work
    // row2#
    row3#

### Known Row Limits

| Table Name                 | Row Limit |
|----------------------------|-----------|
| BookItemNameTable          | 80000     |
| CardItemNameTable          | 80000     |
| CardPostfixNameTable       | 80000     |
| CardPrefixNameTable        | 80000     |
| IdNum2ItemDescTable        | 80000     |
| IdNum2ItemDisplayNameTable | 80000     |
| IdNum2ItemResNameTable     | 80000     |
| IndoorRswTable             | 4096      |
| ItemParamTable             | 80000     |
| ItemSlotTable              | 80000     |
| ItemSlotCountTable         | 80000     |
| LevelUseSkillSpAmount      | 16384     |
| MapNameTable               | 4096      |
| MapObjLightTable           | 4096      |
| MetalProcessItemList       | 80000     |
| Mp3NameTable               | 4096      |
| MsgStringTable             | 4096      |
| Num2CardIllustNameTable    | 80000     |
| Num2ItemDesctable          | 80000     |
| Num2ItemDisplayNameTable   | 20000     |
| Num2ItemResNameTable       | 80000     |
| QuestID2Display            | 80000     |
| SkillNameTable             | 4096      |
| SkillDescTable             | 16384     |
| SkillDescTable2            | 16384     |

[Category:File Formats](/Category:File_Formats "wikilink")