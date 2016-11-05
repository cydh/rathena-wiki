---
title: OnWhisperGlobal
permalink: /OnWhisperGlobal/
---

Syntax
------

**OnWhisperGlobal:**

Explanation
-----------

This special label triggers when a player whispers the NPC, and will run with the player's RID attached. It can accept up to ten parameters, which will be stored into separate temporary character string variables @whispervar0$ to @whispervar9$.

See 'doc/whisper_sys.txt' for further documentation.

Examples
--------

This will broadcast the first word the message that you whispered to the NPC(whisper_announce)

`-  script  whisper_announce    -1,{`
[`OnWhisperGlobal`](/OnWhisperGlobal "wikilink")`:`
`   `[`if`](/if "wikilink")` (`[`getgroupid`](/getgroupid "wikilink")`() > 5)`
`       `[`announce`](/announce "wikilink")` @whispervar0$,0;`
`   `[`end`](/end "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")