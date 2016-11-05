---
title: Custom Books
permalink: /Custom_Books/
---

Introduction
============

Books are Miscellaneous type items in which you can store various kind of information, such as descriptions, stories and guides. You can read them by right-clicking on the item and left-clicking on the small book icon on the top-left corner of the item description.

**Please keep in mind** that in this tutorial I use 2013-08-04 client, which means I work with LUA files. If you use an older client that doesn't support LUA, please read this page for creating items: [Custom Items](/Custom_Items "wikilink").

[center](/File:Custombook1.png "wikilink")

Server-Side Modifications
=========================

You have to edit the following file on server-side:

1.  **trunk/db/re/item_db.txt**: The item's name and stats.

Item_db
--------

First, you must create your book. I strongly recommend creating a new item instead of altering an already existing one because players might acquire the original book in some ways. Also, you should find the row "// Misc "Etc" Books" and insert your book after the last one to keep everything in one place.

Let's create a book called "rAthena Book". Currently 11058 is the last ID but there are books up to 11060 so insert a row below that one and write:

`11061,Rathena_Book,rAthena Book,3,100,200,10,,,,,,,,,,,,,{},{},{}`

This will create an item with the following parameters:

**`11061`**`: ID`
**`Rathena_Book`**`: Database name`
**`rAthena` `Book`**`: Name that players see`
**`3`**`: The Type of the item is "Miscellaneous"`
**`100`**`: NPCs sell this book for 100z`
**`200`**`: Players can sell this book to NPCs for 200z`
**`10`**`: The Weight of this item is 10`
**`Empty`**`: The rest of the parameters remain empty`

Client-Side Modifications
=========================

You have to edit the following files on client-side:

1.  **client/System/itemInfo.lua**: This file determines the appearance and the description of the item.
2.  **grf/data/book/**: Here you add your own book's text.
3.  **grf/data/bookitemnametable.txt**: This file determines what items are books. If you skip this step, the Read icons won't appear.

Iteminfo.lua
------------

In your iteminfo.lua, find \[11058\]. This is the last book-type item after we inserted ours. Copy-paste the whole section, change \[11058\] to \[11061\] and fill it with your desired parameters. The first three lines are for items when they are unidentified; since we work with a Miscellaneous type item, they can be skipped. You should focus on the second three lines.

For the item's picture I recommend searching for an already existing item, find it in iteminfo.lua and copy-paste it's ResourceName. It doesn't matter if you have Korean letters in it or some gibberish text, your client can read both of them.

In the description, you can use colors such as in NPC scripts (see at [Basic_Scripting\#Message](/Basic_Scripting#Message "wikilink")). Each ("Sentence",) creates a new row.

`[11061] = {    // ID of the book: the first parameter in item_db.txt`
`       unidentifiedDisplayName = "",`
`       unidentifiedResourceName = "°í´ëľđľîÇŘĽ®ą®",`
`       unidentifiedDescriptionName = {`
`       },`
`       identifiedDisplayName = "rAthena Book", // Name of the book that appears in-game`
`       identifiedResourceName = "°í´ëľđľîÇŘĽ®ą®",  // Image of the book`
`       identifiedDescriptionName = {   // Description of the book`
`           "A book that is used for tutorial purposes.",`
`           "Weight: ^77777710^000000"`
`       },`
`       slotCount = 0,`
`       ClassNum = 0`
`   },`
`   `

At this point you have an item visible to players but it is still unreadable.

ID.txt
------

Now we can add the text of the book's. Let's see an example with short comments.

`%FAF0E6    // Background color; also the color of the text when Auto-Read is ON`
`^000088rAthena Tutorial Book^000000    // First Row`
`This book is just for testing purposes.    // Paragraphs.`
`If you hit two enters and keep writing, you will create a new ingame paragraph too.`
`You can color the text. Do not write too long lines, since some players might use Auto-Read.`

Bookitemnametable.txt
---------------------

We are at the last step - we have to add the "Read / Auto-Read" buttons to the item. In this txt look for the last line and add this:

`11061#`

After that patch up your client, reload your item_db and your book is ready to read!

[center](/File:Custombook2.png "wikilink")

[Category:Database](/Category:Database "wikilink") [Category:Data](/Category:Data "wikilink") [Category:Customization](/Category:Customization "wikilink")