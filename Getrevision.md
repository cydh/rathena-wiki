---
title: Getrevision
permalink: /Getrevision/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   **get_revision**()

Description
-----------

This command will return the SVN revision number that the server is currently running on.

Example
-------

Here is a sample script which might be a help to you:

`if ( get_revision() >= 15000 )`
`mes "Welcome to rAthena !";`