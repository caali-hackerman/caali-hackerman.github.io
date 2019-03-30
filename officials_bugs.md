# Bugs on official servers
## Translation / Spelling / Grammar
### English (EU)
- NPC 65,1042 should be called "Goatherd" instead of "Shepherd".
- NPC 202,1029 should have dontTurn flag set (lumberjack starts chopping you with his axe when you talk to him...).
- Vanguard request "[Harvest Festival] Collect taproots for tuwangi lunchboxes." should be correctly labeled "[Pond Faire] Collect taproots for tuwangi lunchboxes."
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
- [B80] Quest 61305 VillagerDialog text 6 "BR>" (should be "<BR>" tag)
- [B80] Quest 51010 VillagerDialog text 3 spelling error "Timberwolfs" instead of "Timberwolves"
- [B80] Quest 51010 VillagerDialog text 3 spelling error "bering" instead of "bring"
- [B80] Quest 51010 VillagerDialog text 6 spelling error "How much time _to_ we have left?" instead of "How much time _do_ we have left?"
- [B80] NPC 29,1029 should have dontTurn flag set (corpse lying on the floor turns to you when examining it...).

## Spawns
- The Tholzak Emitter (46,7001) at 32763.529296875 -28165.0078125 -399.2496032714844 cannot be attacked (at least not with ranged skills, idk about melee) because it's inside a collision wall or something
- Some spawns for Castanic Recruit (15,4) have copy&pasted identical patrol routes, which are also very far away from their spawn locations. Looks weird.
- The Barrelhead Threshers (17,300552) near -15129.9970703125,58051.91015625,2585 are bugged (one of them stands on top of the catapult)
- The group of Heavens Fall Farmhand (17,300470) + Enthralled Workers (17,300580) around 7002 -27387.626953125 57267.68359375 2070.90966796875 seems to never respawn after being killed (requires server restart)
- Flying Cobala Ore node at about 7001 101373 -14228 2413
- Flying Plain Stone node at about 7002 -8093 60442 2879
- Flying Xermetal Ore node at about 7022 -25237 34975.53125 4408
- Flying Plain Stone node at about 7002 -39455 23026 1179
- Flying gathering node at 3 -1803.844970703125 8560.890625 5122.3291015625
- Flying gathering node at 3 -5089.22998046875 18386.572265625 5488.0654296875
- Flying gathering node at 3 -3805.832763671875 19238.0234375 5758.13623046875
- [B80] WorkObject 50610 (Ritual Jar in Velik's Distorted Dream) is spawned twice in the same place
- [B80] Flying WorkObject 200031 (Ralotate) at 7011 34389.4453125 -68171.8046875 3386.2763671875
