---
title: Removing skill level requirements
permalink: /Removing_skill_level_requirements/
---

If you want to remove the skill level requirements from a skill, so that you don't need to level other skills up to get into it, then here's what you need to do:

Navigate to and open it up. In there, is the database file for the skill tree, a.k.a. what skills you need to get this skill, what skill you need to get the next, and so on.

The format is as follows:

`//JobNo,Skill-ID,MaxLV,Prerequisite Skill-ID-1,Prerequisite Skill-ID-1-Lv,PrereqSkill-ID-2,`
`PrereqSkill-ID-2-Lv,PrereqSkill-ID-3,PrereqSkill-ID-3-Lv,PrereqSkill-ID-4,PrereqSkill-ID-4-Lv,`
`PrereqSkill-ID-5,PrereqSkill-ID-5-Lv//CLASS_SKILLNAME#Skill Name#`

And then the file is broken down into each class' skill trees.

Let's say we wanted to remove the requirements from the Skill 'Safety Wall' for the Mage.

`2,12,10,11,7,13,5,0,0,0,0,0,0//MG_SAFETYWALL`

Comparing the legend versus the entry for safety wall, we need a few more skills and a certain level of those skills to get safety wall.

If you wanted to remove the other skills from being needed to learn safety wall, simply change those columns to zero. Make sure you restart your server afterwards.

`2,12,10,0,0,0,0,0,0,0,0,0,0//MG_SAFETYWALL`

There! No more requirements to learn Safety Wall! It can be learned as soon as you change into a Mage.

[Category:Database](/Category:Database "wikilink")