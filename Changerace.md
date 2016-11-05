---
title: Changerace
permalink: /Changerace/
---

Introduction
------------

Very simply, this bonus will enable you to use `bonus` `bChangeRace,x;` where `x` `is` `a` `race` such as `RC_Demon`, `RC_Angel` etc.

Implementation
--------------

### Open /src/map/map.h

**Find:**

       SP_ADD_SKILL_BLOW, SP_SP_VANISH_RATE, SP_MAGIC_SP_GAIN_VALUE, SP_MAGIC_HP_GAIN_VALUE //2041-2044

**Replace with:**

       SP_ADD_SKILL_BLOW, SP_SP_VANISH_RATE, SP_MAGIC_SP_GAIN_VALUE, SP_MAGIC_HP_GAIN_VALUE, SP_SETRACE //2041-2045

### Open /src/map/pc.c

**Find:**

       case SP_LUK:
            if(sd->state.lr_flag != 2)
                sd->param_bonus[type-SP_STR]+=val;
            break;

**Below add:**

       case SP_SETRACE:
            if(val < 0 || val > RC_MAX-1) {
                ShowWarning("pc_bonus: invalid race defined for 'bChangeRace', set to %d.\n", val);
            } else if(sd->state.lr_flag != 2)
            {
                sd->status.race =
                sd->battle_status.race = val;
            }
            break;

### Open /db/const.txt

**Find:**

    bMagicHPGainValue<tab>2044

**Below add:**

    bChangeRace<tab>2045

### Conclusion

The script will be ready to go after a re-compile. Simply use `bonus` `bChangeRace,x;` and you'll be able to alter the race of a player (when wearing an item with the bonus in-tact).

[Category:Source Snippets](/Category:Source_Snippets "wikilink")