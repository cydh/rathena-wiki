---
title: Soundeffect
permalink: /Soundeffect/
---

Syntax
------

-   **soundeffect** "<effect filename>",<type>;
-   **soundeffectall** "<effect filename>",<type>{,"<map name>"}{,<x0>,<y0>,<x1>,<y1>};

Description
-----------

These two commands will play a sound effect to either the invoking character only ('[soundeffect](/soundeffect "wikilink")') or multiple characters (**'soundeffectall**'). If the running code does not have a sprite ID (a 'floating' NPC) or is not running from an [NPC](/NPC "wikilink") object at all (an item script) the sound will be centered on the character who's [RID](/RID "wikilink") is attached to the script, if any. If it does have a sprite ID, it will be centered on that NPC.

Effect filename is the filename in a [GRF](/GRF "wikilink"). It must have the [.wav extension](/wikipedia:WAV "wikilink").

To be on the safe side, the clip should be in mono, with a 22050Hz sampling rate, and a bit rate of 192Kbps. Most other combinations usually bring up a Gravity Error, even though a few Gravity-official sound clips have a 44100Hz sampling rate, and a couple are even in stereo.

It's not quite certain what the 'type' actually does, it is sent to the client directly. It probably determines which directory to play the effect from. It's certain that giving 0 for the number will play sound files from '\\data\\wav\\', but where the other numbers will read from is unclear.

File names should have a maximum length of 23 characters including the .wav extension:

**`soundeffect`**` "1234567890123456789.wav", 0; // this will play the soundeffect `
**`soundeffect`**` "12345678901234567890.wav", 0; // throw gravity error  `

Example
-------

This NPC plays different sound effects for the player that talks to it, depending on what options the player picks within the script.

`prontera,185,153,2 script  159,{`
`   `[`mes`](/mes "wikilink")` "[Code Master]";`
`   `[`mes`](/mes "wikilink")` "Hey, you! What's today's secret code?";`
`   `[`next`](/next "wikilink")`;`
`   `[`switch`](/switch "wikilink")`(`[`select`](/select "wikilink")`("195.:675.:723.:438.:387.:I don't know.")) {`
`   `[`case`](/case "wikilink")` 1:`
`   case 2:`
`   case 4:`
`   case 5:`
`       mes "[Code Master]";`
`       `[`soundeffect`](/soundeffect "wikilink")` "buzzer.wav",0;`
`       mes "Nope, sorry! That's not the secret code! Try again next time!";`
`       `[`break`](/break "wikilink")`;`
`   case 3:`
`       mes "[Code Master]";`
`       `[`soundeffect`](/soundeffect "wikilink")` "bellding.wav",0;`
`       mes "That's it! That's today's secret code!";`
`       break;`
`   case 6:`
`       mes "[Code Master]";`
`       mes "You don't know? Then you need to look harder!";`
`       mes "The secret code is written on a wall nearby!";`
`       break;`
`   }`
`   `[`close`](/close "wikilink")`;`
`}`

Notes
-----

If a script plays a soundeffect play while another one is playing, the previous one doesn't stop; it'll keep playing! For most short sound effects, such as skill or monster sounds, this might not be a problem, but for songs like bragis_poem.wav, playing another sound over that might not sound good. The only way to stop any sound effects that are currently playing (on your client) is to change maps (ex: using the [warp](/warp "wikilink") script command) or walk through a warp portal to another map.

[Category:Script Command](/Category:Script_Command "wikilink")