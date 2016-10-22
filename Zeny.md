[Zeny](Zeny) is the in-game currency used in [Ragnarok Online](Ragnarok-Online), which can be used for buying and selling items from and to [NPC](NPC) shops and other players.

Limitation
----------

The technical limit is for both the client and server up to 2,147,483,647 Zeny, which is typically capped at 1,000,000,000. The cap can be changed inside **mmo.h** by adjusting the macro *MAX_ZENY* to a desired value below the technical limit. The source must be recompiled after this change. If a value is specified which surpasses the technical limit, the server will not compile.

Penalty
-------

Along with EXP death penalties, a Zeny penalty may be set in which reduced the amount of Zeny the player holds upon death:

    // When a player dies (to another player), how much zeny should we penalize them with?
    // NOTE: It is a percentage of their zeny, so 100 = 1%
    zeny_penalty: 0

[Mapflags](Mapflag) can be set on certain maps to disable the zeny penalty in.

Vending
-------

The amount of Zeny that can be set to an item when vending is soft-limited to 1,000,000,000 and can be overridden by the setting *vending_max_value* in and [hexing](hexing) the client to correct the client-side warnings.

If the seller obtains more Zeny through vending than *MAX_ZENY* the surplus Zeny is discarded. To avoid this, the setting *vending_over_max* in can be set to *no*, which causes the deal to fail if it would result in more Zeny than the seller is able to hold.

Scripting
---------

The name *Zeny* is recognized by the script engine as a [parameter constant](parameter-constant), which affects the amount of Zeny of the [currently attached](RID) player. It can be both read and written.

    set Zeny,Zeny+120;  // gives the player 120z
    mes "Your current balance is "+Zeny+"z.";
    set Zeny,0;  // takes all Zeny from the player
