# Bugs on official servers
## Translation / Spelling / Grammar
### English (EU)
- NPC 65,1042 should be called "Goatherd" instead of "Shepherd".
- Vanguard request "[Harvest Festival] Collect taproots for tuwangi lunchboxes." should be correctly labeled "[Pond Faire] Collect taproots for tuwangi lunchboxes."
- [B80] Quest 18299 Task 1 tells you to go to Renish in Highwatch, but he's in Amadjuak Trading Post.
- [B80] Quest 50601 VillagerDialog text 6 spelling error "potion s" instead of "potions"
- [B80] Quest 50601 VillagerDialog text 14 spelling error "TGhere" instead of "There"
- [B80] Quest 50601 VillagerDialog text 14 grammar error "Once the effect is ends"
- [B80] Quest 50602 VillagerDialog text 3 grammar/spelling error "but we're also had some villagers go missing"
- [B80] Quest 50602 VillagerDialog text 3 spelling error "releated" instead of "related"
- [B80] Quest 50602 VillagerDialog text 5 spelling error "mosnters" instead of "monsters"
- [B80] Quest 61301 is called "Cottery's Delivery" despite the NPC being called "Cottrey"
- [B80] Quest 61308, task 3 shows "Use . <0/5>" because skill 0,9999,20006002 does not have an entry in StrSheet_UserSkill
- [B80] Quest 61302 VillagerDialog text 3 spelling error "sameples" instead of "samples"
- [B80] Quest 61303 VillagerDialog text 5 missing "." after "Well done"
- [B80] Quest 61305 VillagerDialog text 3 missing "." after "supposed to"
- [B80] Quest 61305 VillagerDialog text 6 "BR>" (missing "<" for html tag)
- [B80] Quest 51010 VillagerDialog text 3 spelling error "Timberwolfs" instead of "Timberwolves"
- [B80] Quest 51010 VillagerDialog text 3 spelling error "bering" instead of "bring"
- [B80] Quest 51010 VillagerDialog text 6 spelling error "How much time _to_ we have left?" instead of "How much time _do_ we have left?"
- [B80] Quest 50603 (Tria evacuation): After talking to the individual groups of NPCs and having them board the airship (in groups of 3, 3, 4, and 4 people, respectively), the airship incorrectly shows 4/15, 8/15, 12/15, and 15/15 (instead of 3/15, 6/15, 10/15, 14/15) passengers
- [B80] Quest 50603 VillagerDialog text 17 spelling error "an that" instead of "and that"
- [B80] Quest 50603 VillagerDialog text 23 "to make sure the the way is clear"
- [B80] Quest 50603 and others keep talking about "butterflies" but the mobs are moths :thinking:
- [B80] Quest 50603, when advancing to task 40 (StrSheet_Quest 50603078), spelling error "You here a strange sound." instead of "You hear a strange sound."
- [B80] Quest 50603 VillagerDialog text 31 "Bringing these people here was federation's idea"?
- [B80] Quest 61424 VillagerDialog text 4 spelling error "It's course" instead of "Its course"
- [B80] Quest 51020 VillagerDialog text 2 spelling error "y daughter" instead of "My daughter"
- [B80] Quest 51020 VillagerDialog text 3 spelling error "yes" instead of "Yes" at start of sentence
- [B80] Quest 51020 VillagerDialog text 4 spelling error "treat" instead of "Treat" at start of sentence. Also no punctuation before the ")"
- [B80] Quest 51020 VillagerDialog text 5 spelling error "tha" instead of "the", "Airship" instead of "airship", and grammar error "maybe there's be some news"
- [B80] Quest 61423 VillagerDialog text 8 grammar error "We running out of food..."
- [B80] Quest 6000 VillagerDialog text 3 (page 1) spelling error "you've came" instead of "you've come"
- [B80] Quest 6000 VillagerDialog text 3 (page 2) grammar error "The creatures secrete ... from its wing"
- [B80] Quest 6000 VillagerDialog text 3 (page 2) grammar error "When monsters inhale this powder, the nevous system [missing: is] disturbed"
- [B80] Quest 6000 VillagerDialog text 3 (page 2) spelling error "furous" instead of "furious"
- [B80] Quest 6000 VillagerDialog text 3 (page 3) grammar/spelling error "it's body" instead of "its body"
- [B80] Quest 6000 VillagerDialog text 9 spelling error "You've came" instead of "You've come"
- [B80] Quest 6000 VillagerDialog text 13 spelling error "our" instead of "Our"
- [B80] Quest 6000 VillagerDialog text 21 spelling error "Mos" instead of "Most"
- [B80] Quest 6000 VillagerDialog text 21 spelling error "they've" instead of "They've"
- [B80] Quest 6000 VillagerDialog text 22 spelling error "teh" instead of "the"
- [B80] Quest 6000 VillagerDialog text 22 spelling error "towm" instead of "town"
- [B80] Quest 6000 VillagerDialog text 25 spelling error "that's" instead of "That's"
- [B80] Quest 6000 VillagerDialog text 27 spelling error "mveryone" instead of "everyone"
- [B80] Quest 6000 VillagerDialog text 28 spelling error "Aura Sentine" instead of "Aura Sentinel"
- [B80] Quest 6001 VillagerDialog text 12 spelling error "idae" instead of "idea"
- [B80] NPC 238,3004 has a VillagerDialog saying just "Temp"
- [B80] NPC 38,109 VillagerDialog spelling error "every" instead of "ever"
- System message `SMT_FIELDNAMED_RANK` is missing first opening `<font color='#1DDB16'>` tag
- System message `SMT_CITYWAR_DEAD_MESSAGE` is missing closure of first `<font color = '#cccccc'>` tag
- System message `SMT_GUILD_WAR_WITHDRAW_GUILDMONEY` has additional closing `</font>` tag after the `<font color = '#5efdff'>{GuildName1}</font>` element
- System message `SMT_ACCOUNT_WAREHOUSE_BUY` text grammar error "to add more tabs your bank storage."
- Mystic's Mass Teleport skill tooltip says "Use to healp" instead of "Use to help"
- Nightlion mount is called "Frostlion" instead of "Nightlion" in its tooltip.

## Spawns
- In Allemantheia Consul's Hall (zone 2) one of the guards at the entrance (519,1007) is below the map (z = 58, should be z = 186).
- The Tholzak Emitter (46,7001) at 32763.529296875 -28165.0078125 -399.2496032714844 cannot be attacked (at least not with ranged skills, idk about melee) because it's inside a collision wall or something
- Some spawns for Castanic Recruit (15,4) have copy&pasted identical patrol routes, which are also very far away from their spawn locations. Looks weird.
- The Barrelhead Threshers (17,300552) near -15129.9970703125,58051.91015625,2585 are bugged (one of them stands on top of the catapult)
- The group of Heavens Fall Farmhand (17,300470) + Enthralled Workers (17,300580) around 7002 -27387.626953125 57267.68359375 2070.90966796875 seems to never respawn after being killed (requires server restart)
- Duplicate spawns of 2 groups of Lokian Sniper (25,2041) & Lokian Blood Reaper (25,2042) at identical coordinates 7003 -83433.3515625,-39486.55859375,2694 and 7003 -83323.171875,-39493.359375,2696
- Kelobe (25,5021) and Lysinia (25,5023) spawn/idle inside of a barricade (near 7003 -84598.8515625,-35351.96484375,2694)
- The 3 Incubators in Granarkus are all spawned in the same location (8001 39927.44921875 66449.84375 2812.475830078125) instead of being spread out
- Flying Cobala Ore node at about 7001 101373 -14228 2413
- Flying Cobala Ore node at about 7001 88120 -3323 865
- Flying Plain Stone node at about 7002 -8093 60442 2879
- Flying Xermetal Ore node at about 7022 -25237 34975.53125 4408
- Flying Plain Stone node at about 7002 -39455 23026 1179
- Flying Wild Veridia node at about 7001 82304 -23844 1424
- Flying gathering node at 3 -1803.844970703125 8560.890625 5122.3291015625
- Flying gathering node at 3 -5089.22998046875 18386.572265625 5488.0654296875
- Flying gathering node at 3 -3805.832763671875 19238.0234375 5758.13623046875
- [B80] WorkObject 50610 (Ritual Jar in Velik's Distorted Dream) is spawned twice in the same place
- [B80] Flying WorkObject 200031 (Ralotate) at 7011 34389.4453125 -68171.8046875 3386.2763671875
- [B80] Workobject 200010 (Monster Traces) at 7011 56526 3585 5530 is below the ground

## NPCs
- NPC 202,1029 should have dontTurn flag set (lumberjack starts chopping you with his axe when you talk to him...).
- [B80] NPC 29,1029 should have dontTurn flag set (corpse lying on the floor turns towards you when examining it...).
- [B80] NPC 27,1019 should have dontTurn flag set (siege cannon immediately turns towards you when examining it...).
- NPC 63,40009618 should have dontTurn flag set (hidden egg from easter egg turns towards you when examining it)
- NPC 72,40009607 should have dontTurn flag set (hidden egg from easter egg turns towards you when examining it)
- NPC 84,40009607 should have dontTurn flag set (hidden egg from easter egg turns towards you when examining it)
- NPC 183,40009601 should have dontTurn flag set (hidden egg from easter egg turns towards you when examining it)
- NPC 183,40009617 should have dontTurn flag set (hidden egg from easter egg turns towards you when examining it)
- NPC 68,9005 should have dontTurn flag set (hidden egg from easter egg turns towards you when examining it)
- NPC 61,9005 should have dontTurn flag set (hidden egg from easter egg turns towards you when examining it)
- NPC 411,5003 should have dontTurn flag set (working blacksmith turns towards you when talking to him)
- NPC 411,5004 should have dontTurn flag set (working blacksmith turns towards you when talking to him)
- NPC 411,5005 should have dontTurn flag set (working blacksmith turns towards you when talking to him)
- NPC 411,5006 should have dontTurn flag set (working blacksmith turns towards you when talking to him)
- NPC 411,5015 should have dontTurn flag set (working blacksmith turns towards you when talking to him)

## Quests
### EU
- Reward for completing 16 daily vanguard quests still includes [Item 444] "(Old) Bravery Potion" (1 hour cooldown)
