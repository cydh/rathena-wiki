---
title: Show item SP heal
permalink: /Show_item_SP_heal/
---

Introduction
------------

Very simply, if you wish for SP to be displayed when using a healing item, simply follow this article.

Open /src/map/pc.c
------------------

*Scroll to or find the function pc_itemheal*

------------------------------------------------------------------------

**Find (*in pc_itemheal*):**

`   if (sd->sc.data[SC_CRITICALWOUND])`
`   {`
`       hp -= hp * sd->sc.data[SC_CRITICALWOUND]->val2 / 100;`
`       sp -= sp * sd->sc.data[SC_CRITICALWOUND]->val2 / 100;`
`   }`

**Below add:**

`   if( sp > 0 )`
`       clif_skill_nodamage(NULL, &sd->bl, MG_SRECOVERY, sp, 1);`

*Then recompile.*

Conclusion
----------

Now, when you use a healing item, it should display the amount of SP you recover.

[Category:Source Snippets](/Category:Source_Snippets "wikilink") [Category:Customization](/Category:Customization "wikilink")