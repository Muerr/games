These are the relevant macros I use for my Beast Master Hunter. Some of these macros I created myself, most of them I modified from other peoples' on various WoW-related forums. If you want to see how a macro would work, [try them out](http://www.macroexplain.com/). Some macros are not BM specific and are usable on any class. There is no specific order here. Hopefully this is helpful to someone.

I don't take requests or build custom macros.

Cast binding shot at the current target's location if a modifier key is pressed, otherwise cast it with the targetting circle.

```
#showtooltip
/cast [mod][@target] Binding Shot
/cast [nomod] Binding Shot
END
```

My call pet macro. This will summon the specified pet number if the pet is not dead or cast Revive Pet if the pet is dead. If a modifier is held, it will dismiss the pet. Otherwise, it will cast Mend Pet. It will cast Wake Up to ensure the pet is not feigning death.

Pet 1 is my Fel Core Hound (Lust pet), Pet 2 is my Battle Rez pet (Quilen). I have others but those are the most important.

```
#showtooltip
/use [@pet,nodead] Call Pet 1; [@pet,dead][nopet]Revive Pet;[mod]Dismiss Pet;Mend Pet
/cast Wake Up
/script UIErrorsFrame:Clear()
```

If you haven't bound the extra action button in the keybinds menu, you can use a macro for it like this:

```
/click ExtraActionButton1
```

Handy, you can buy specific items from vendors. For example, this allows you to buy the ingredients for Fish Brul Special that can be purchased with Blood of Sargeras from the vendor in Dalaran.

```
/script BuyMerchantItem(7)
/script BuyMerchantItem(8)
/script BuyMerchantItem(12)
```

Turn on or turn off Growl and Thunderstomp based on whether you're in a group. If you're not using the Growler addon ;).

```
/petautocastoff [nomod][group] Growl
/petautocaston [nomod][nogroup] Growl
/petautocastoff [mod][group] Thunderstomp
/petautocastoff [mod][nogroup] Thunderstomp
```

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

I can never remember the command to show whether a quest ID is completed. Get the questid from wowhead or other wow database.

```
/script print(IsQuestFlaggedCompleted(33468))
```

Replace MAINTANK and OFFTANK with the main and off tank for your raid group to switch which one is your focus. This is useful for using assist, or casting Misdirection on the focus target.

```
/clearfocus
/focus [nomod] MAINTANK
/focus [mod] OFFTANK
```

I bind this to Control-C to cancel any attack and pet attack. Good for "oh shit, time to FD!" moments.

```
/stopcasting
/stopattack
/petfollow
/petpassive
```

Pop all on-use trinkets, no matter which slot they're in.
```
#showtooltip
/use 13
/use 14
```

Cast Bestial Wrath, and then Misdirection on my target, my focus, my target's target (e.g., whatever is tanking it), or my pet. Of couse, Misdirection isn't super effective for BM since most of our threat is generated by the pet, not the hunter themselves. But BW increases our damage from Cobra Shot and Murder of Crows, so at least we have that.

```
#showtooltip Bestial Wrath
/cast Bestial Wrath
/cast [help][@focus, help][@targettarget,help][@pet,exists] Misdirection
```

Cast all the buffs! Orcs are strong and have Blood Fury. Add your race's activated ability like Troll Berserking here if desired. But why wouldn't you be playing an orc for BM? :)

```
#showtooltip
/cast Aspect of the Wild
/cast Blood Fury
/cast Bestial Wrath
```

Interrupt! This can be used on mouseover if the current target isn't casting.

```
#showtooltip
/stopcasting
/stopcasting
/cast [@mouseover, exists] Counter Shot; Counter Shot
```

BM isn't super great at target switching for priority adds because pets have to travel. However, we can throw out some Cobra Shot to help a bit, and this allows that to happen on a mouseover without changing the main target. Careful about this though, if your mouse is over a friendly target it won't work. Maybe I should have a `harm` in here...

```
/cast [@mouseover, exists] Cobra Shot; Cobra Shot
```

Cast Dire Beast *before* casting Titan's Thunder. Hit it twice to get both up.

```
/castsequence Dire Beast, Titan's Thunder
```

OH SHIT FEIGN DEATH. Both you and your pet.
```
#showtooltip
/cast Feign Death
/cast Play Dead
```

Go to the Darkmoon Faire. Buy a Seafarer's Slidewhistle with the fish currency. Then use this macro for your disengage. Hilarity ensues in raids "What the fuck is that whistling?"

```
#showtooltip
/cast Disengage
/cast Seafarer's Slidewhistle
```

This one is pretty dope. It will cast Ancient Hysteria (lust) if the current pet is a Core Hound. It will cast Eternal Guardian (brez) if the current pet is a Quilen. The brez works on mouseover targets, or on your focus to get the main tank back up (see the focus macro earlier). Change the words as required if you use other pets for lust and brez.

```
#showtooltip [pet:Core Hound]Ancient Hysteria;[pet:Quilen]Eternal Guardian
/use [pet:Core Hound]Ancient Hysteria
/use [pet:Quilen,@mouseover,help][pet:Quilen,@focus,help]Eternal Guardian
```

LFR for the lulz. Just cast Kill Command and Cobra Shot over and over. You'll still do more DPS than half the raid, probably.

```
/startattack
/petattack
/castsequence reset=combat Kill Command, Cobra Shot
```

A bit more detailed LFR macro. This one tosses in Bestial Wrath for some buff goodness, and adds Dire Beast (or Dire Frenzy if you have that talented).

```
#showtooltip
/assist [@focus,exists][@pet,exists]
/startattack
/petattack
/cast Bestial Wrath
/castsequence reset=5 Cobra Shot, Dire Beast, Kill Command
```

Plain misdirection without the BW. Usable on Marksman. Not that you'd be playing MM.
```
#showtooltip Misdirection
/stopcasting
/cast [help][@focus, help][@targettarget,help][@pet,exists] Misdirection
```

Opener Macro. Use all on-use trinkets (mainly because my KJBW is in different slots based on which equipment set I used XD), then if Murder of Crows is talented cast that, put up Bestial Wrath and Titan's Thunder, send in the pet and autoattack.

This would be followed by Dire Frenzy, Aspect of the Wild (see the previous buffs macro), Kill Command, and the normal rotation.

```
/use 13
/use 14
/cast [talent:6/1] A Murder of Crows
/cast Bestial Wrath
/cast Titan's Thunder
/petattack
/startattack
```

Cast the row 5 talent that you have selected.

```
#showtooltip [talent:5/1] Binding Shot; [talent:5/2] Wyvern Sting; [talent:5/3] Intimidation
/cast [talent:5/3] Intimidation
/cast [talent:5/2] Wyvern Sting
/cast [talent:5/1] Binding Shot
```

Cast the row 6 talent that you have selected. Barrage is missing because as a BM YOU SHOULD NEVER USE BARRAGE.

```
#showtooltip [talent:6/1] A Murder of Crows; [talent:6/3]Volley
/cast [talent:6/1] A Murder of Crows
/cast [talent:6/3] Volley
```

Toss a freezing trap at your cursor without a modifier key, otherwise target the ground and place one. Strategically.

```
#showtooltip
/cast [nomod, @cursor] Freezing Trap
/cast [mod] Freezing Trap
```

That's it! Hope you found these useful!