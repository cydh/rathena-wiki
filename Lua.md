---
title: Lua
permalink: /Lua/
---

Lua Background Information
==========================

What is Lua?
------------

Lua is a powerful, fast, lightweight, embeddable scripting language.

Lua combines simple procedural syntax with powerful data description constructs based on associative arrays and extensible semantics. Lua is dynamically typed, runs by interpreting bytecode for a register-based virtual machine, and has automatic memory management with incremental garbage collection, making it ideal for configuration, scripting, and rapid prototyping.

Where does Lua come from?
-------------------------

Lua is designed, implemented, and maintained by a team at PUC-Rio, the Pontifical Catholic University of Rio de Janeiro in Brazil. Lua was born and raised in Tecgraf, the Computer Graphics Technology Group of PUC-Rio, and is now housed at Lablua. Both Tecgraf and Lablua are laboratories of the Department of Computer Science of PUC-Rio.

What does Lua stand for?
------------------------

"Lua" (pronounced LOO-ah) means "Moon" in Portuguese. As such, it is neither an acronym nor an abbreviation, but a noun. More specifically, "Lua" is a name, the name of the Earth's moon and the name of the language. Like most names, it should be written in lower case with an initial capital, that is, "Lua". Please do not write it as "LUA", which is both ugly and confusing, because then it becomes an acronym with different meanings for different people. So, please, write "Lua" right!

Lua and RO
==========

What's it used for?
-------------------

### The client itself

First application of Lua appeared in the client as a means of customizing the Homunculus and Mercenary AI. Later, Gravity started to move out a lot of hard-coded data and functionality inside the client into Lua scripts, causing X-ray clients to become obsolete.

### The Ragnarok Online Patcher

Recently, the patch and skin information of the official patcher is Lua-based as well, stored in nine files spanning five folders.

[Lua](/wikipedia:Lua_(programming_language) "wikilink") is a free scripting language, which can be both embedded or stand-alone.

How do we use it?
-----------------

### Client-side gibberish

If you're using Lua files from Gravity, chances are your files are encoded. When you open up a .lua file, you'll notice 2 things.

#### ASCII

Lots and lots of ASCII characters depending on what kind of editor you use:
Notepad
[<File:Accname.lub-notepad.png>](/File:Accname.lub-notepad.png "wikilink")
[Notepad++](http://notepad-plus-plus.org/)
[<File:Accname.lub-notepadpp.png>](/File:Accname.lub-notepadpp.png "wikilink")

#### English

You'll notice some English words that you may find familiar, be it headgear names, job classes, NPC sprites etc. You can manipulate this data to directly affect the client. The most popular reasons for editing the Lua files is to create [Custom Items](/Custom_Items#View_IDs.2C_Having_A_Custom_Item_Without_Xray "wikilink")

### Client-side un-gibberish

The Translation Project team have been keeping their SVN repository up to date with the latest Lua files. They're in plain English, and readable. This makes editing them a whole lot easier!

[Lua_Project](http://subversion.assembla.com/svn/ClientSide/Lua_Project/)

Misc.
-----

A number of development branches have arisen which intended to replace the Athena Scripting Language with Lua, but as of today none have been completed.

External Links
--------------

-   [Official Lua Scripting Language Homepage](http://www.lua.org/)
-   [Lua_Project](http://subversion.assembla.com/svn/ClientSide/Lua_Project/)

[:Category:Customization](/:Category:Customization "wikilink")