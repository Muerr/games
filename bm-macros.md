These are the relevant macros I use for my Beast Master Hunter. Some of these macros I created myself, most of them I modified from other peoples' on various WoW-related forums. If you want to see how a macro would work, [try them out](http://www.macroexplain.com/). Some macros are not BM specific and are usable on any class. Some combine different things between specs on hunters so I don't run out of "Muerr specific macro" space in the game macro panel UI. There is no specific order here. Hopefully this is helpful to someone.

## Binding Shot

Cast binding shot at the current target's location if a modifier key is pressed, otherwise cast it with the targetting circle.

```
#showtooltip
/cast [mod][@target] Binding Shot
/cast [nomod] Binding Shot
END
```

## Call Pet

My call pet macro. This will summon the specified pet number if the pet is not dead or cast Revive Pet if the pet is dead. If a modifier is held, it will dismiss the pet. Otherwise, it will cast Mend Pet. It will cast Wake Up to ensure the pet is not feigning death.

Pet 1 is my Fel Core Hound (Lust pet), Pet 2 is my Battle Rez pet (Quilen). I have others but those are the most important.

```
#showtooltip
/use [@pet,nodead] Call Pet 1; [@pet,dead][nopet]Revive Pet;[mod]Dismiss Pet;Mend Pet
/cast Wake Up
/script UIErrorsFrame:Clear()
```

## Buffs

Cast spec-specific buffs with one button. Hold down a modifier (I use `alt`) to cast your aspect if BM or SV, otherwise the main cooldown will be used (`nomod`).

```
#showtooltip
/cast [spec:1, mod] Aspect of the Wild; [spec:3, mod] Aspect of the Eagle
/cast [spec:1, nomod] Bestial Wrath; [spec:2, nomod] Trueshot; [spec:3, nomod] Coordinated Assault
```

## Interrupt

Interrupt! This can be used on mouseover if the current target isn't casting. Works for all three specs.

```
#showtooltip [spec:1][spec:2] Counter Shot; [spec:3]Muzzle
/stopcasting
/stopcasting
/cast [@mouseover,exists, harm][] Counter Shot
/cast [@mouseover,exists, harm][] Muzzle
```

## Core Ability

This puts the "core" ability for all three hunter specs on one button to save space in your macro UI.

```
#showtooltip
/petassist
/petattack
/use [spec:1][spec:3]Kill Command
/use [spec:2,@mouseover,harm,exists][spec:2]Aimed Shot
```

## Filler

Similar to "core" above, this is for your "filler" and works for all three hunter specs.

```
#showtooltip
/use [spec:1,@mouseover,harm,exists][spec:1]Cobra Shot
/use [spec:2,@mouseover,harm,exists][spec:2]Arcane Shot
/use [spec:3]Raptor Strike
```

## Focus Generators

For BM and MM, focus generator macro.

```
#showtooltip
/use [spec:1,@mouseover,harm,exists][spec:1]Barbed Shot
/use [spec:2,@mouseover,harm,exists][spec:2]Steady Shot
```

## Explosive Orbs

Use these to snipe orbs on Explosive affix for M+, and win the admiration of your party.

```
/cast [@mouseover, exists, harm][] Cobra Shot
```

```
/cast [@mouseover, exists, harm][] Dire Beast
``` 

```
/cast [@mouseover, exists, harm][] Barbed Shot
```

## Feign Death

OH SHIT FEIGN DEATH. Both you and your pet.

```
#showtooltip
/cast Feign Death
/cast Play Dead
```

## Pets are Healers

If you're using a Spirit Beast, you get Spirit Mend. You probably want to cast this on yourself, or maybe a mouse-over target.

```
#showtooltip
/cast [@mouseover,help][@player][] Spirit Mend
```

## MOST IMPORTANT MACRO

**Usable on all hunter specs**

Go to the Darkmoon Faire. Buy a Seafarer's Slidewhistle with the fish currency. Then use this macro for your disengage. Hilarity ensues in raids "What the fuck is that whistling?"

```
#showtooltip
/use [nomod] Disengage
/use [mod] Aspect of the Cheetah
/use Seafarer's Slidewhistle
```

As an added bonus, I baked Cheetah in this if you hit a modifier.

As an added bonus, use this with Vengeful Retreat on your Demon Hunter, Blink/Shimmer on your Mage, etc, etc.

## Exotic Abilities

This one is pretty dope. It will cast Ancient Hysteria (lust) if the current pet is a Core Hound. It will cast Eternal Guardian (brez) if the current pet is a Quilen. The brez works on mouseover targets, or on your focus to get the main tank back up (see the focus macro earlier). Change the words as required if you use other pets for lust and brez.

```
#showtooltip [pet:Core Hound]Ancient Hysteria;[pet:Quilen]Eternal Guardian
/use [pet:Core Hound]Ancient Hysteria
/use [pet:Quilen,@mouseover,help][pet:Quilen,@focus,help]Eternal Guardian
```

## Misdirection

Set the tank as your focus. Or the healer, or whoever you want to troll... ;)

```
#showtooltip Misdirection
/stopcasting
/cast [help][@focus, help][@targettarget,help][@pet,exists] Misdirection
```

## Murder of Crows OR Dire Beast

If talented, this handles casting Dire Beast (with `mod:alt`) or Murder of Crows (`nomod`).

```
#showtooltip
/targetenemy [dead][noexists]
/use [spec:1,talent:4/3,mod:alt,@mouseover, harm, exists][spec:1,talent:4/3,nomod]A Murder of Crows
/use [spec:1,talent:1/3,nomod,@mouseover, harm, exists][spec:1,talent:1/3,mod:alt]Dire Beast
/cast Auto Shot
```

## Level 30 Talent - SV and BM

Both SV and BM have activated abilities for their level 30 talent, so put those on one macro. Bonus: Chimaera Shot is a `@mouseover`, so you can use this on Explosive Orb weeks - and cleave to another mob nearby!

```
#showtooltip
/use [@mouseover,harm,spec:1,talent:2/3][spec:1,talent:2/3]Chimaera Shot
/use [spec:2, talent:2/3]Explosive Shot
/cast Auto Shot
```

# Freezing Trap

Toss a freezing trap at your cursor without a modifier key, otherwise target the ground and place one. Strategically. You wish you had this macro when doing Aggramar on Heroic+ eh? Or, you wish hunters in PUGs did...

```
#showtooltip
/cast [nomod, @cursor] Freezing Trap
/cast [mod] Freezing Trap
```

# Tar Trap

Same as Freezing Trap, but this one makes everything sticky.

```
#showtooltip
/cast [nomod, @cursor] Tar Trap
/cast [mod] Tar Trap
```

## Turtle

Cancels Aspect of the Turtle if it's up, otherwise, Turtle!

```
#showtooltip
/cancelaura Aspect of the Turtle
/use Aspect of the Turtle
```

# Other Useful Macros

## Extra Action Button
If you haven't bound the extra action button in the keybinds menu, you can use a macro for it like this:

```
/click ExtraActionButton1
```

## Buying  Items from Vendors

Handy, you can buy specific items from vendors. For example, this allows you to buy the ingredients for Fish Brul Special that can be purchased with Blood of Sargeras from the vendor in Dalaran.

```
/script BuyMerchantItem(7)
/script BuyMerchantItem(8)
/script BuyMerchantItem(12)
```

## Awesome Mount Macro

This badass macro will mount up based on a few conditions. To explain:

* If we're in the water (swimming), or if Ctl-Alt are held, mount the Azure Water Strider for water walking
* If Alt is held, mount the Transmog / Vendor
* If Ctl is held, mount the Sky Golem to farm herbs (because I'm not a druid ;) )
* If we're in a place where flying isn't allowed, mount Steelbound Devourer, because it matches the Fel Core Hound pet :)
* Otherwise, mount a favorite mount which will automatically pick a flying mount if flying is available
* Finally, dismount if we're mounted

```
/use [swimming][mod:alt,mod:ctrl]Azure Water Strider
/use [mod:alt]Grand Expedition Yak
/use [mod:ctrl]Sky Golem
/use [mod:shift]Arcanist's Manasaber
/use [noflyable]Steelbound Devourer
/run C_MountJournal.SummonByID(0)
/dismount [mounted]
```

## Quest Completion Command

I can never remember the command to show whether a quest ID is completed. Get the questid from wowhead or other wow database.

```
/script print(IsQuestFlaggedCompleted(33468))
```

## Tank Focus Swapping

Replace MAINTANK and OFFTANK with the main and off tank for your raid group to switch which one is your focus. This is useful for using assist, or casting Misdirection on the focus target.

```
/clearfocus
/focus [nomod] MAINTANK
/focus [mod] OFFTANK
```

## ABORT

I bind this to Control-C to cancel any attack and pet attack. Good for 

> Raid Lead: "STOP DPS!"

```
/stopcasting
/stopattack
/petfollow
/petpassive
```

## Rings and Trinkets

Pop all on-use rings and trinkets, no matter which slot they're in. This may not work in BfA with GCD changes.

```
#showtooltip
/use 11
/use 12
/use 13
/use 14
```
