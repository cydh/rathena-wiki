---
title: Mmo.h
permalink: /Mmo.h/
---

This source file holds global declarations and hard-coded settings, that are used by the login, char and map server. If you modify anything, you have to recompile all three servers, otherwise you may run into errors.

### PACKETVER

Specifies the packet version to use for server-client communication. It must be set to date, your client has been released at, e. g. 20090922 for 2009-09-22aRagexeRE. Note: If you have a client, that is newer, than the latest packet version in the comment, some things might not work properly, if the client packets have changed since then.

### ENABLE_SC_SAVING

If you disable this define, all status changes get discarded upon logout.

### HOTKEY_SAVING

When enabled, the server stores client hotkeys. While older clients save them locally in the registry, newer clients require this define to be enabled.

### MAX_MAP_PER_SERVER

Sets how many maps a single map server may manage. This also includes instanced maps.

### MAX_INVENTORY

Sets maximum amount of item slots in the character item inventory. If you set this above 127, some scripts, that enumerate characters' inventory will break.

### MAX_CHARS

Max number of characters per account. Note, that changing this setting alone is not enough if the client is not hexed to support more characters as well.

### GLOBAL_REG_NUM

Max number of permanent [char variables](/Variables#Player_Variables "wikilink").

### ACCOUNT_REG_NUM

Max number of permanent [account variables](/Variables#Account_Variables "wikilink").

### ACCOUNT_REG_NUM2

Max number of permanent [global account variables](/Variables#Global_Account_Variables "wikilink").

### MAX_REG_NUM

Should hold the max of GLOBAL/ACCOUNT/ACCOUNT2 (needed for some arrays that hold all three)

### DEFAULT_WALK_SPEED

Default walk speed of players in milliseconds.

### MIN_WALK_SPEED

Minimum walk speed of players in milliseconds.

### MAX_WALK_SPEED

Maximum walk speed of players in milliseconds.

### MAX_STORAGE

Max number of storage slots a player can have. (up to ~850 tested)

### MAX_GUILD_STORAGE

Max number of [storage](/storage "wikilink") slots a guild.

### MAX_PARTY

Maximum members a [party](/party "wikilink") can hold.

### MAX_GUILD

Maximum members a [guild](/guild "wikilink") can hold. 6 additional members will be added per 1 level of Guild Extension skill.

### MAX_GUILDPOSITION

Maximum guild positions that can be assigned to members.

### MAX_GUILDEXPULSION

Maximum length of expulsion reason to be displayed.

### MAX_GUILDALLIANCE

Maximum length of guild alliance names to be displayed.

### MAX_GUILDSKILL

Maximum number of skills that a Guild can have.

### MAX_GUILDLEVEL

Maximum level that a Guild can reach.

### MAX_GUARDIANS

Maximum guardians that can be summoned in a castle. If this value is increased, need to add more fields on MySQL \`guild_castle\` table ..

### MAX_QUEST_DB

Maximum number of quest(Questlog System) that the server will load.

### MAX_QUEST_OBJECTIVES

Maximum quest objectives for a quest.

### WEDDING_RING_M

Item ID of the wedding ring for male.

### WEDDING_RING_F

Item ID of the wedding ring for female.

### NAME_LENGTH

Maximum length of a character/title/guild/map/etc. name.

### ITEM_NAME_LENGTH

Maximum of length of an item name, which tend to have much longer names.

### PINCODE_LENGTH

Maximum length of pincodes.

### MAX_FRIENDS

Maximum number of friends that a player can have on his list.

### MAX_MEMOPOINTS

Maximum memo points that the warp portal skill can save.

### MAX_FAME_LIST

Number of players to be listed in the fame list arrays.

### START_ACCOUNT_NUM

Starting ID for player accounts.

### END_ACCOUNT_NUM

Ending ID for player accounts.

### START_CHAR_NUM

Starting ID for characters.

### MAX_GUILDMES1

Maximum character length of guild message title.

### MAX_GUILDMES2

Maximum character length of guild message body.

[Category:Configuration](/Category:Configuration "wikilink")