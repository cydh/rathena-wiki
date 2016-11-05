---
title: A brief look at RagExe
permalink: /A_brief_look_at_RagExe/
---

*Game Framework Class* (GFC) is Gravity's own name for the game engine or application architecture used in Ragnarok Online. With the Ragnarok beta release in 2001, Gravity announced the finalization of GFC 2.0. But what exactly is GFC, and where did it come from? Most game developers use commercial proprietary engines for their games, while GFC is an in-house product by Gravity's RND-1 development division. In truth, it's misleading to call it a game engine, as GFC in its current form has been used in exactly one game and is tightly coupled to it. In all likelyhood the name GFC and the notion of a game engine are just buzzwords Gravity used in an attempt at impressing investors in their early days. However, my client is strictly based on Gravity's RagExe implementation, and I guess it can therefore be said to be a clone of GFC. Here's a brief look at its history.

Gravity Corp. was a relatively small developer before Ragnarok Online became an international success. Certainly no one outside of South Korea knew of them. In fact, right up until Ragnarok become ready for alpha testing they were still just Team Gravity. In 1999 they partnered up with Sonnori Entertainment in a joint venture to develop an action RPG. *Arcturus: The Curse and Loss of Divinity* was released with success in 2000. At this point Gravity obtained the rights to publish a game based on the popular Korean comic *Ragnarök*. They decided to reuse source code from Arcturus. While Arcturus and Ragnarok don't have much in common in terms of game play, resemblances can be noticed in aspects such as artistic style and music.

[<File:Acturus.png>](/File:Acturus.png "wikilink")

Making Arcturus into the Ragnarok we know today required a severe overhaul of the code base. However, in many architectural decisions were left intact. What was retained became the base of GFC.

Ragnarok, like Arcturus, is a 2.5D game. While Gravity at one point experimented with 3D actors in Ragnarok, the main focus has always been on sprite-based characters in a 3D world. Most of the file formats from Arcturus could therefore be reused directly in Ragnarok. This is one of the reasons why some of Gravity's file formats have strange features. For instance the world resource format (RSW) contains strings pointing to scripts files, a feature not used in Ragnarok. Some formats, like RSX (think RSM for actors) were retained and is still in the code base, but never used. A few formats from Arcturus you may know include:

-   SPR - indexed color bitmap format
-   ACT - actor animation
-   RSM - hierarchical 3D models with basic animation support
-   GND - tile based ground mesh
-   GAT - tile based property map
-   RSW - map format (defines a scene with objects)

They also made new formats, like the worthless IMF format that no one understand what is supposed to do... (Just kidding, IMF is used when combining ACT files for player characters, but it turns out it wasn't really necessary or useful. The client uses IMF offsets when drawing the player on the character select, which is probably why headgear sometimes looks a little wonky there. It also uses it for drawing order for player character sprites in-game.)

While based on DirectX 7.0, from a modern perspective GFC can be said to be software rendered. If you've ever wondered why Ragnarok uses so much CPU, that is why! Direct3D is only used as a glorified triangle rasterizer with blending and depth buffering. GFC has a fairly large entity-based actor system where every actor is responsible for rendering themselves every frame. There are a few principal object types: ground (GND), models (e.g. RSM) and game objects (actors, effects, etc). Rendering done by registering a *render pass* from with the renderer - basically a list of screen projected vertices and a texture. The renderer sorts the render passes by depth, opacity and other attributes, and draws everything at the end of each game cycle. This all makes for a pretty horrible design. Easy to work with, but unnecessarily taxing on the system. The only reason it worked in the first place is the low amount of polygons on the screen. (Typically below 10,000 triangles at any time.)

Game objects communicate by passing messages around to each other. In Ragnarok, there is also a global state (the session) and the current game mode, which is responsible for tasks like processing input, creating actors, handling network messages and signalling actors.

[<File:Acturus-GameObjectHierarchy.png>](/File:Acturus-GameObjectHierarchy.png "wikilink")

The diagram above shows part of the base object hierarchy in Arcturus, which is pretty tall and convoluted. In Arcturus, each enemy needed its own class specialization. In comparison the diagram below shows the object hierarchy at the time of the Ragnarok alpha release. While simplified, the principal structure is the same. I have colored a few classes that provide similar functionality in the two games.

[<File:Ragnarok-GameObjectHierarchy-Alpha.png>](/File:Ragnarok-GameObjectHierarchy-Alpha.png "wikilink")

CRenderObject is any type of object that is draw on the screen, while CGameActor is any object that can be interacted with. CPc is the object type for characters controlled by a player. CNpc covers static NPCs and monsters. In Arcturus you could interact with certain 3D models (e.g. doors, chests), so C3dActor was a part of the game object hierarchy. In Ragnarok, all 3D models are just decoration and not part of the game play and aren't considered game objects. (The exceptions to the rule are Granny actors and traps, the latter of which are actually RSM models drawn by a Skill object.)

From the Ragnarok alpha to commercial release the renderer was improved a bit, and the 2D actor system become more flexible. A few libraries from RAD Game Tools was integrated to provide sound, video playback and a more practical 3D format (namely GR2, thought it's only been used for a few models). Aside from that, not much has changed.

Source
------

[curiosity's post](https://rathena.org/board/topic/104827-wip-native-ragnarok-client/#entry298242)