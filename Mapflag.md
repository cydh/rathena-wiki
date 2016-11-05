---
title: Mapflag
permalink: /Mapflag/
---

A Map Flag describes restrictions, properties, and behaviors of a certain map. The map flags alter the behavior of the map regarding teleporting, storing location when disconnected, dead branch usage, penalties upon death, PVP behaviour, WoE behavior, ability to use skills or open up trade deals, current weather effects, and whether day/night will be in effect on this map.

Map flags can be found in the folder. However, some existing map flags do not have their own file in that folder therefore one might be required to create it and add it in using the same format as previous entries. All existing map flags can be found in , prefixed by *mf_*, which is not needed whenever you set it.

Do note that Map Flags are not restricted to the folder, for it can also be defined in any another script as long as that script is loaded into the map server and proper syntax is used.

Syntax and Setting
------------------

<code>

    <map name>%TAB%mapflag%TAB%<flag>%TAB%<extra>

</code>

**Map Name**: Replace it with the name of the map you wish to apply the map flag to. You do not have to include .gat at the end of the map name.
**mapflag**: Describes that it is a map flag.
**Flag**: Replace it with the map flag you wish to use such as novending, nocommands, restricted
**Extra**: Required only with some map flagg. Please check individual map flag articles for this part.

Map Flags in Scripts
--------------------

Map Flags are utilized by the following script commands. Please visit individual articles for descriptions.

-   [setmapflag](/setmapflag "wikilink")
-   [removemapflag](/removemapflag "wikilink")
-   [setmapflagnosave](/setmapflagnosave "wikilink")

Flags
-----

Below is a list of all the flags and their descriptions.

### allowks

-   allows Kill Stealing on that map (meaning @noks has no effect)

### autotrade

-   allows @autotrade command to be used on that map
-   this only takes effect if the **at_mapflag** is set to yes in

### battleground

-   defines a BG map

### bexp

-   changes the Base Exp Rate for that map
-   value is in percent: 100 means 1x the base_exp_rate. 200 means double the base_exp_rate
-   Example: 25% base exp boost in Prontera

`prontera   mapflag bexp    125`

### clouds

-   Enables Cloud weather effect

### clouds2

-   Another type of clouds

### fireworks

-   Enables Fireworks effects (sounds too)

### fog

-   Fog is not set in the mapflag but in data.grf\\fogparametertable.txt

### guildlock

-   Blocks changes to Guild (/guild, invite, leave, expel, add/delete Alliance/Opposition, @changegm and /breakguild)

### gvg

-   The **gvg** mapflags set the Guild vs. Guild mode on the specified map. All guilds will appear with their icon over the head and will be able to attack other guilds. WoE damage reduction calculations will be taken into consideration.

### gvg_castle

-   Defines a guild castle
-   On guild castle maps, GVG is only on when [WoE](/WoE "wikilink") is active

### gvg_dungeon

-   Defines a map if it is a Guild Dungeon
-   If you die twice you are warped out

### gvg_noparty

-   (if **gvg** ison) Ignores parties, allowing you to kill non-guild members in your party

### indoors

-   The **indoors** mapflag will set any map specified to the indoor mode, which prevents any enabled Weather Effects to display.

### jail

-   Jail file is actually a collection of mapflags specific to jail. In jail, the default mapflags are:

<code>

    //= pvp: Turns on PvP mode
    //= pvp_noparty: Can't attack player in same party
    //= nobranch: No Dead Branching allowed.
    //= nomemo: No Warp Portal Memory Point allowed.
    //= nopenalty: No Exp. penalty when player dies.
    //= nosave: No saving respawn point allowed. Use SavePoint to use the
    //=                players previous savepoint, or choose one manually.
    //= noteleport: No Teleporting allowed.  No f-wings or b-wings.

</code>

### jexp

-   Changes the Job Exp Rate for that map
-   Value is in percent: 100 means 1x the job_exp_rate. 200 means double the job_exp_rate

### leaves

-   Brown/red leaves falling

### loadevent

-   When a player loads on this map, [OnPCLoadMapEvent](/OnPCLoadMapEvent "wikilink") will be triggered

### monster_noteleport

-   Blocks monsters and monsters with RG_INTIMIDATE from teleporting

### nightenabled

-   Enables specified map to display [night mode](/night_mode "wikilink") effects; most outdoor maps have this mapflag set for obvious reasons.

### nobaseexp

-   Killed monsters will not give base experience (including MVP exp. bonus)

### nobranch

-   Following items can't be used:
    -   Dead Branch (ID 604)
    -   Red Pouch (ID 12024)
    -   Bloody Branch (ID 12103)
    -   Poring Box (ID 12109)

*Note: list of these items is [hardcoded](/wikipedia:Hard_coding "wikilink").*
*See also: [mob_warp](/mob_warp "wikilink").*

### nochat

-   Blocks creating Private/Public Chat Rooms (Alt+C)

### nocommand

-   Blocks all @commands
-   Optionally, you can specify the minimum GM level which can override and still use @commands

`prontera   ma`

### nodrop

-   Blocks dropping items in a certain map

### noexp

-   same as **nobasexp** and **nojobexp** combined

### noexppenalty

-   Players will not receive experience penalty upon their death
-   Pets' intimacy will not drop after owner's death
-   PR_REDEMPTIO skill will not deduct experience when used

*See also: [death_penalty_type](/death_penalty_type "wikilink")*

### nogo

-   Blocks the command @go
-   any_warp_GM_min_level can override

### noicewall

-   Blocks the WZ_ICEWALL skill from being used by players, homunculi and mercenaries; client will not display any error message, player simply won't be able to cast the skill.

### nojobexp

-   Killed monsters will not give job experience

### noloot

-   Same as **nomobloot** and **nomvploot** combined

*Note: noloot mapflags work on monsters only. Looted items will always drop.*

### nomemo

-   Prevents players (below any_warp_GM_min_level) from using `/memo` to save a warp point
-   Disables usage of WE_CALLPARENT, WE_CALLPARTNER and WE_CALLBABY skills

### nomobloot

-   Killed monsters will not drop any items (including script-granted items and Ore Discovery) except looted items and MVP reward

### nomvploot

-   Killed monsters will not give any MVP rewards

### nopenalty

-   Same as **noexppenalty** and **nozenypenalty** combined

### nopvp

-   The **nopvp** mapflag prevents pvp from being turned on in the specified map.

### noreturn

-   Usage [warpparty](/warpparty "wikilink") and [warpguild](/warpguild "wikilink") script commands is restricted
-   Following items can't be used:
    -   Butterfly Wing (ID 602)
    -   Dungeon Teleport Scrolls (ID 14527, 14581)
    -   Yellow, Green, Red and Blue Butterfly Wings (ID 14582–14585)
    -   Siege Teleport Scroll (ID 14591)

*Note: list of these items is [hardcoded](/wikipedia:Hard_coding "wikilink").*

### nosave

-   **nosave** mapflag will prevent auto-saving in the map. If the character logs off in a map set with this mapflag, he/she will return to the map or point specified in the last field. *SavePoint* returns the character to their last Kafra or @save savepoint.

### noskill

-   The **noskill** mapflag disables all skills on the specified map. GM's are automatically exempt according to the setting in , *lowest_gm_level*.

### noteleport

-   [warp](/warp "wikilink"), [areawarp](/areawarp "wikilink"), [warpchar](/warpchar "wikilink"), [warpparty](/warpparty "wikilink"), [warpguild](/warpguild "wikilink") and [warpwaitingpc](/warpwaitingpc "wikilink") script commands will not work with *"Random"* destination
-   [warpwaitingpc](/warpwaitingpc "wikilink") will not work with *"SavePoint"* destination
-   [unitwarp](/unitwarp "wikilink") script command will not work with players
-   @jump will not work if GM level is below any_warp_GM_min_level
-   AL_TELEPORT skill can't be used by players (except for level 3, ie. Butterfly Wing)
-   TK_HIGHJUMP skill will not work (except for **battleground**, **gvg** and **gvg_castle** maps)
-   teleport part of RG_INTIMIDATE, NPC_EXPULSION, CG_TAROTCARD skills will not work
-   following items can't be used:
    -   Fly Wing (ID 601)
    -   Giant Fly Wing (ID 12212)

*Note: list of these items is [hardcoded](/wikipedia:Hard_coding "wikilink").*

### notrade

-   Blocks Trading

### novending

-   Blocks Vending

### nowarp

-   The **nowarp** mapflag will block the use of @go to any GM level lower than *lowest_gm_level*, set in , in the specified map. Characters who use @go will be met with the message ' *You are not authorized to warp from this map.* '.

### nowarpto

-   The **nowarpto** mapflag mainly has to do with your GM's. when set, the mapflag prevents @warp from being used to go to the specified map. The client will be met with the error message ' *You are not authorized to warp to this map.* '.

### nozenypenalty

-   Players will not receive [zeny penalty](/Zeny#Penalty "wikilink") upon their death

### partylock

-   Blocks changes to Party (/organize, /leave, /invite, @changeleader)

### pvp

-   The **pvp** mapflag will set pvp on in the specified map. By default, under pvp, parties will be allied to each other.

### pvp_nightmaredrop

-   The **nightmare** mapflag sets any specified map to have a specified drop on death. The syntax of the actual mapflag is as follows:

<code>

    map_name<TAB>mapflag pvp_nightmaredrop<TAB>id,type,percent

</code>

-   For the *id* field, possible settings are the **item ID** you would like dropped, or **random** to pick a random item from the player.

<!-- -->

-   In the *type* field, the possibles are: **inventory** for dropping an item directly from inventory, **equip** for stripping the equipment off the character, or **all** for stripping the item off the character regardless of where it is. The percent, obviously, is a number times 100%.

### pvp_nocalcrank

-   Disables the default PvP Ranking(Usually found at bottom-left of the Client) in a certain map.

### pvp_noguild

-   (if PvP is on) Ignores guilds, allowing you to kill players in your guild

### pvp_noparty

-   (if PvP is on) Ignores parties, allowing you to kill players in your party

### restricted.txt

-   The **restricted** mapflag is used in conjunction with item_noequip.txt and skill_nocast_db.txt, both located in the /db/ folder.

### sakura

-   Enables Sakura weather effect(white leaves falling).

### snow

-   Enables Snow weather effect.

### town

-   Defines a map as a "town"
-   Currently, this is only used to check which maps Mail Inbox can be opened on.

The format for this file is:

<code>

    map_name<TAB>mapflag restricted<TAB>zone_number

</code>

The zone number is set in and

[Category:Scripting](/Category:Scripting "wikilink")