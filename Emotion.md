---
title: Emotion
permalink: /Emotion/
---

Syntax
------

-   [emotion](/emotion "wikilink") <emotion number>{,<target>{,"<target name>"}};

Description
-----------

This command makes an object display an emotion sprite above their own as if they were doing that emotion. For a full list of emotion numbers, see '' under 'e_'. The not so obvious ones are 'e_what' (a question mark) and 'e_gasp' (the exclamation mark).

The optional target parameter specifies who will get the emotion on top of their head. Target value can be:

| Value | Description   |
|-------|---------------|
| 0     | NPC (default) |
| 1     | Player.       |

Target name parameter allows displaying emotion on top of other NPC/PC. If the specified name is not found, the command does nothing.

[Category:Script Command](/Category:Script_Command "wikilink")