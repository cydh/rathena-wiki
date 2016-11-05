---
title: Favorite tab
permalink: /Favorite_tab/
---

The new Favorite Item Tab addition allows players to move items into the new tab which then gets saved. It acts like any other tab in your inventory, but it's meant for you to keep items you find to be "personal", "productive" or even your "favorite" in there. This new addition to rAthena has been introduced in [r16518](http://trac.rathena.org/changeset/16518/rathena).

How do I get it?
----------------

Along with the new addition in [r16518](http://trac.rathena.org/changeset/16518/rathena), you can download the SQL file here: that will update your SQL table so that your server won't give you any errors.

What client supports this?
--------------------------

Clients that are dated 2011-11-22aRagexeRE client and above will support this new Favorite Tab.

Msgstringtable
--------------

In order for you to get the actual tab working, you would need to get an updated [msgstringtable.txt](http://pastebin.com/MxVxnCtH). If you wish to change what's written in your tabs, find these lines:

-   Line: 1466 = Usable Items
-   Line: 1472 = Etc. Items
-   Line: 2051 = Equipment
-   and Line: 2052 = Personal/Favourite Tab

What you Must Know
------------------

Without this Favorite Tab added to your SQL, you will encounter a SQL Error which would be indicating a missing column. The error that will be appearing would be:

`[SQL]: DB error - Unknown column 'favorite' in 'field list'`
`` [Debug]: at c:\rathena\src\char\char.c:1225 - SELECT `id`, `nameid`, `amount`, ` ``
`` equip`, `identify`, `refine`, `attribute`, `expire_time`, `favorite`, `card0`, ` ``
`` card1`, `card2`, `card3` FROM `inventory` WHERE `char_id`=? LIMIT 100 ``

and

`[SQL]: DB error - Statement not prepared `

This SQL error will cause players to have their items "disappeared" every time they relog. Fixing this is easy as to just updating your database with this code:

`` ALTER TABLE `inventory`  ADD COLUMN `favorite` TINYINT(3) UNSIGNED NOT NULL DEFAULT '0' AFTER `expire_time`; ``

Further Updates
---------------

Further updates to the Favorite Tab functionality has been introduced in:

-   [r16543](http://trac.rathena.org/changeset/16543/rathena)
