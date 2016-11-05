---
title: Escape sql
permalink: /Escape_sql/
---

Syntax
------

-   [escape_sql](/escape_sql "wikilink")(<value>)

Description
-----------

Converts the value to a string and escapes special characters so that it is safe to use in query_sql().

Returns the escaped form of the given value.

Examples
--------

`set .@str$, "John's Laptop";`
`set .@esc_str$, escape_sql(.@str$);    // Escaped string: John\'s Laptop`

[Category:Script Command](/Category:Script_Command "wikilink")