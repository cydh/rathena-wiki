---
title: Group Permissions
permalink: /Group_Permissions/
---

What are Group Permissions
--------------------------

Ever since rAthena , a new system has replaced the old GM IDs with a new Grouping system. With this new Grouping System, each group has its own unique ID and Name, lists of available commands and other permissions, and a list of other groups it inherits from. More information can be found in your .

With this in mind, there is a file called permissions.txt that can be found in your . It lays out all of the permissions that groups can get. You can add such permissions in your .

Adding Permissions
------------------

For this guide, I'll be using the group "players". This group is located in :

`{`
`   id: 0 /* group 0 is the default group for every new account */`
`   name: "Player"`
`   level: 0`
`   inherit: ( /*empty list*/ )`
`   commands: {`
`       /* no commands by default */`
`   }`
`   permissions: {`
`       /* without this basic permissions regular players could not `
`       trade or party */`
`       can_trade: true`
`       can_party: true`
`   }`
`},`

As you can see, the **permissions:** section is what holds all the permissions that group can do. Now, lets say I want my players to be allowed to join protected (password) chats. What I would do is right after **can_party: true**, I will add **join_chat: true**. Doing so will result in it looking like this:

`   permissions: {`
`       /* without this basic permissions regular players could not `
`       trade or party */`
`       can_trade: true`
`       can_party: true`
`       join_chat: true`
`   }`

True or False?
--------------

Now you may ask, "**Why do I need to put true? Why can't it be false?**" or something similar. Well, to put it this way, setting it to **true** allows that group to be able to do such a permission or "privilege". By setting it to **false**, that group will not be able to do that such permission.

What are my Permissions?
------------------------

As mentioned before, head on over to . That is where all the permissions for your groups can be found.

`These are possible permissions of player groups, configured in conf/groups.conf.`
`can_trade : Ability to trade or otherwise distribute items (drop, storage, vending etc)`
`can_party : Ability to join parties.`
`all_skill : Ability to use all skills.`
`all_equipment : Ability to equip anything (can cause client errors).`
`skill_unconditional : Ability to use skills without meeting the required conditions (SP, items, etc...).`
`join_chat : Ability to join a password protected chatrooms.`
`kick_chat : Protection from being kicked from a chat.`
`hide_session : Hides player session from being displayed by @commands.`
`who_display_aid : Ability to see GMs and Account/Char IDs in the @who command.`
`hack_info : Ability to receive all informations about any player that try to hack, spoof a name, etc.`
`any_warp : Ability to bypass nowarp, nowarpto, noteleport and nomemo mapflags.`
`          This option is mainly used in commands which modify a character's`
`          map/coordinates (like @memo, @mapmove, @go, @jump, etc...).`
`view_hpmeter : Ability to see HP bar of every player.`
`view_equipment : Ability to view players equipment regardless of their setting.`
`use_check : Ability to use client command /check (display character status).`
`use_changemaptype : Ability to use client command /changemaptype.`
`all_commands: Ability to use ALL atcommands/charcommands.`
`receive_requests: Ability to receive @requests.`
`show_bossmobs: Ability to see boss mobs with @showmobs.`
`disable_pvm: Ability to disable Player v.s. Monster.`
`disable_pvp: Ability to disable Player v.s. Player.`