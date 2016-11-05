---
title: Query sql
permalink: /Query_sql/
---

Syntax
------

-   **query_sql**("your MySQL query"{, <array variable>{, <array variable>{, ...}}});
-   **[query_logsql](/query_logsql "wikilink")**("your MySQL query"{, <array variable>{, <array variable>{, ...}}});

Description
-----------

Executes an SQL query. A '[select](/select "wikilink")' query can fill [array](/array "wikilink") variables with up to 128 rows of values, and will [return](/return "wikilink") the number of rows (i.e. array size).

Note that [query_sql](/query_sql "wikilink") runs on the main database while [query_logsql](/query_logsql "wikilink") runs on the log database.

Examples
--------

[`set`](/set "wikilink")` .@nb, `**`query_sql`**`` ("SELECT name, fame FROM `char` ORDER BY fame DESC LIMIT 5", .@name$, .@fame); ``
[`mes`](/mes "wikilink")` "Hall Of Fame: TOP5";`
[`for`](/for "wikilink")`(`[`set`](/set "wikilink")` .@i,1; .@i <= .@nb; set .@i,.@i+1)`
[`mes`](/mes "wikilink")` .@i+". "+.@name$[0]+" ("+.@fame[0]+")"; // Will return a person with the biggest fame value.`

[Category:Script_Command](/Category:Script_Command "wikilink")