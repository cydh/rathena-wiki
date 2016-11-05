---
title: Editing the wiki
permalink: /Editing_the_wiki/
---

Welcome to the rAthena wiki!
----------------------------

The rAthena wiki could always use some help. It is an ever changing repository of information related to rAthena, such as installation, configuration, scripting and even some client support. The wiki thanks you for stopping by and showing some interest in helping get the wiki full of the most useful information for rAthena.

### Where to Begin?

All users must login to the wiki using their forum account. Any member with more than 1 post on the forums can edit the wiki, but please keep in mind that the rAthena wiki is released under the [GNU Free Documentation License](/wikipedia:GNU_Free_Documentation_License "wikilink") Version 1.2. This means that the wiki and any works put on it can be edited at will. They may also be distributed, provided all history and copylefts remain intact. Please see read this page for more information.

Don't know where to start? Check the [Special:WantedPages](/Special:WantedPages "wikilink") page and create a page that is listed there!

Please do not create pages for custom content, such as custom projects not relating to rAthena in any way. A full list of content that should not be on the wiki is listed at [Editing the wiki](/Editing_the_wiki "wikilink").

Please see [Wiki Projects](/:Category:Wiki_Projects "wikilink") for any ongoing projects that you might be able to help with!

### License Requirements

The rAthena wiki is to be released under the [GNU Free Documentation License](/wikipedia:GNU_Free_Documentation_License "wikilink"). For those that do not know, this license allows anyone to edit your work on the wiki at will, provided that all pertinent history is remained intact and all copylefts are abided by. This work can also be redistributed, again, provided that all copylefts remain intact.

### Editing Requirements

You might be eager to start editing. The first question is....how do I start?

With the rAthena wiki, you can use IPB BBCodes to format your work, but there is a helpful toolbar at the top of the edit box to help you as well.

You can create a new page, but make sure that the page you are creating [doesn't exist yet](/Special:AllPages "wikilink") and preferably is already [being linked to](/Special:WantedPages "wikilink"). If it already exists, maybe you can head over and help edit in something that might be missing that someone forgot.

### General Rules for the rA wiki

These guidelines/rules should be followed on the rAthena wiki. If not followed, your account is at risk for being banned from the wiki **as well as** from the forums. You have been warned.

-   Deleting a page must come from a Community Administrator or a Documentation Manager. If you have a page that you request for deletion, please add the `{{deletion` `suggested}}` template. See [Template:Delete](/Template:Delete "wikilink") for details.
-   Editing wars are not to be tolerated. It creates unwanted and unneeded long history.
-   Pornography is a not to appear on the rA wiki.
-   Text must be appropriate in nature and not contain foul language.

### General tips for editing a wiki

These tips should be referenced when you need to edit/write an article.

-   As mentioned before, make sure that if a new page is being created, it [doesn't exist yet](/Special:AllPages "wikilink").
-   Use proper English with proper spelling and grammar. The rAthena wiki is in English and English only at this point.
-   Links should not appear in topic titles, such as the title of a section.
-   There should be no reason to link to a page more than once if it appears in the article multiple times. The first mention of a topic that has a page should be linked to.
-   Name your page appropriately and avoid special symbols. Don't make your page too long, but think of a name that will relate to the article (i.e: Don't name your article related to XRay 'client').
-   Use images when Windows is involved. It is too hard and sometimes troublesome to read an article with the text: Go here, click OK, go here, hover your mouse here, click here, type this, click here, drag it to here, etc.
-   Any section or article that relates to changing code should be in DIFF or PATCH format. This includes all of the proper syntax. If you do not know what a diff or patch file is, please refer to it's Wikipedia article [here](/wikipedia:Diff#Unified_format "wikilink"). 'find and replace' text is not acceptable.
-   Make use of Wikipedia's help articles, if you are unsure about [editing articles](/wikipedia:Wikipedia:How_to_edit_a_page "wikilink") or [the use of some wiki-code](/wikipedia:Help:Wiki_markup "wikilink"). Note, that most of the templates used on Wikipedia cannot be applied to the rAthena wiki, except [few ones](/:Category:Templates "wikilink").
-   Use the *Show preview* button before saving the page, especially when you are unsure, how your edit turns out. This helps avoiding follow-up "ooops"-edits.
-   Before you save an article, add reason for your edit or summary of your edit in the *Summary* line. You help others to recognize, what was changed and why in the [list of recent changes](/Special:RecentChanges "wikilink") and it distinguishes you from spam-bots, which do not add a reason. You do not need to add a summary for your user-page or on article's talk pages. If you cannot remember what you changed, use the *Show changes* button to review all changes done to the page as a diff.
-   Avoid excessive amount of formatting. Use either **bold** or *italics* but not ***both***. Refrain from using <u>underlining</u> as this usually gives the impression of a link. <s>Strike-through</s> should be used on talk pages only, if there is something in an article to invalidate, simply delete it.

### Script Command Pages

As a general rule of thumb, the following format should be used in order to keep the articles in a uniform fashion.

`==Syntax==`
`*'''scriptcommand'''(<argument1>, <"argument2">);`
``
`==Description==`
`This command does this and that, and arguments mean that and this.`
``
`==Examples==`
` [[/mes|mes]] "...";`
` [[/if|if]](scriptcommand(1, "abc"))`
` {`
`     mes "...";`
` }`
` [[/close|close]];`
``
`==See Also==`
`* [[/related_script_command_1|related script command 1]]`
`* [[/related_script_command_2|related script command 2]]`
``
`[[/Category:Script_Command|Category:Script Command]]`