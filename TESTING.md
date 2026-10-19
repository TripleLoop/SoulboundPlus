# 0.1.14 acceptance checks (graphical verification pending)

- [ ] Human dummy preview and real clash last 10 seconds by default. Five changing chest-led yanks finish in the first seven seconds. At seven seconds the hand begins the native soul-removal gesture; no struggle displacement/limb pulls overlap it. Final ejection still has one chest tug and removal sound.
- [ ] Set clash duration to 2, 5 and 15 seconds. Five pulls and a separate removal phase fit within the configured total; no extra cooldown or timing changes. Default retry remains 30 seconds, including owner return-key attempts.
- [ ] Possess a husk/zombie, voluntarily remove the soul and observe from the native camera. The hand reaches into the chest and extracts the soul, rather than staying arms-forward. No doubled wrist offset or sudden arm snap; a smooth chest tug/recoil follows. Test skeleton, Human/Monster/empty dummy and a normal player too.
- [ ] Enable a short mob/Monster timer. Native extraction prepares before expiry and transitions onto the released mob, with stable grabbing arms. Body/head facing remains consistent. Non-humanoid mobs receive a body pull rather than human arm motion.
- [ ] Possess zombie/husk, skeleton/stray, drowned, piglin, enderman and an illager: idle and walk arms follow player-style motion. Test crouching, sprinting, swimming and item use. Original model/size/texture stay intact; unpossessed mobs retain their normal stance. Illager crossed arms hide only during possession/extraction and return afterward.
- [ ] Start soul removal in first person, rear/front third person. Move the mouse and press F5 during extraction: no forced cinematic view or locked look; native movement lock still applies. Repeat on a borrowed mob, own body and a timed ejection. Menu/fountain/battle cameras remain intact.
- [ ] Try main/offhand weapons, Soulbound weapon slot, gloves and armor: held objects and armor follow final arm pose; no duplicate hands or equipment. Combat retains attacks/spells and disables timer-extraction poses until combat ends.
- [ ] Walk into own/borrowed body with multiple soul types: one native entry ring, correct color and sound, no new enemy clone. Check actual body movement near solid blocks.
- [ ] Start combat during either clash phase: eject challenger, stop the clash pose and apply cooldown. Completed possession still uses normal combat animation.

# 0.1.12 acceptance checks

- [ ] Menu → stats skill list shows three white handle bars and T-Action. Drag only from the handle; normal name clicks still open the skill tree. Long names leave room for handles.
- [ ] Move T-Action to the bottom, middle and top. Battle slots follow the menu order. Select moved skills and verify the named skill/action is cast, with normal costs/targets and unlock restrictions.
- [ ] Change current TP: affordable skills must not move ahead of the saved order. Gray/unaffordable skills remain correctly restricted. Test both normal and PvP skill menus (PvP may rename T-Action to Awaken).
- [ ] Drag across multiple pages by holding near list edges. Drop at both ends; resize the window; cancel with Escape/right click. A canceled drag must not save or reorder anything.
- [ ] Close/reopen the menu, reconnect and restart the client. Each profile/recruit retains its own order. Another player's list is unaffected.
- [ ] Unequip/re-equip a skill and learn another skill; no skill/progress is lost, relative ordering persists, and new skills append. Check normal live combat ordering. Card/deck modes keep native order and cast the expected card.
- [ ] Existing unoccupied Human, Monster and empty dummies are visible after updating. New spawns show their name/soul as appropriate. Approach each chest in soul mode: Human contests, Monster timers, empty immediate entry.
- [ ] Occupied dummies have exactly one visible controlled body. On exit the parked dummy becomes visible again. Dummies cannot be selected as battle enemies or added to nearby fights.
- [ ] Preview struggle/eject, edit levels/soul types/absorbed counts and clear dummies. Confirm the previous caps and cooldowns remain.

# 0.1.11 acceptance checks (not yet run in a graphical world)

- [ ] Possess an armored skeleton, release all movement keys and verify no drifting or hidden-body pushing. Walk, sprint, jump and stop normally, then leave/re-enter.
- [ ] Skeleton, zombie/baby zombie, spider and slime retain coherent walk poses and body size. World idles do not use combat poses. Try a modded non-biped too.
- [ ] Glove thumbs match the marked outer sides. Verify both hands from main hand, offhand and menu weapon slot, plus bows and child models.
- [ ] Ballet Shoes attach to both feet and follow combat kicks/walking. Notebook is closed/smaller; gun compact/3D; other weapons keep their original appearance with depth.
- [ ] Enable a 10-second mob timer: no countdown text, soul reveal at 5 seconds, colored glow at 9 seconds, native removal sound/chest pull on ejection at 10 seconds. Unlimited possession has no stages. Repeat during a fight: expiry waits until combat ends; manual reveal and teams still work normally afterward.
- [ ] Spawn a Human dummy at your level; preview struggle and eject while standing outside it. Repeat with large level gaps and animation-strength settings. Soul-mode entry runs a real simulated contest, retry cooldown works, winning allows walking/voluntary exit. A fight interrupts an active challenge. Clear drops any physical equipment once and removes your loaded dummies.
- [ ] Spawn Human LV 99 and try LV 100 (rejected). Change the nearest Human's soul with `dummy set soul bravery`; chest soul/name color update. Check all listed human soul types; monster/invalid types are rejected for Human dummies.
- [ ] Spawn Monster dummies with 0 and 7 souls; 8 is rejected. `dummy set souls 3` updates the nearest Monster. Entry ignores level; default possession lasts 30 seconds at 0 souls and 23 seconds at 7, regardless of the ordinary mob timer. Server duration/reduction/minimum settings still apply.
- [ ] Spawn an empty dummy: no chest soul, immediate entry, unlimited possession even with the ordinary mob timer enabled. Human possession is also untimed. Editing any occupied/contested dummy is rejected.
- [ ] Save/reload each dummy kind; level, soul type, absorbed souls, creator and name persist. Soul/body transitions never create inventory soul items.
- [ ] Two players still test ownership, return-key contests, owner/guest death and disconnect; the dummy cannot substitute for these checks.

# In-game acceptance checklist

Use a disposable world, two players, the exact pinned dependencies, and distinctive numbered items so duplication/loss is visible. These gameplay checks have **not** been run in this environment.

- [ ] Soulbound 2.0.21: enter a Replica battle while already possessing a body and while involved in a body struggle. Check that the normal combat lock and challenger-ejection rules apply; leaving a completed virtual encounter restores normal possession controls. Replica bosses have no possessable world body.

- [ ] Soulbound 2.0.19: ordinary hostile Darkner possession preserves its generated item, colors and proportions on both clients. Darkner bosses and the shopkeeper refuse possession. Exit restores the original Darkner, with no additional items/loot.
- [ ] Saved skill overrides survive the update. Unchanged skills follow 2.0.21 defaults; resetting an override restores the new native value. Check global scaling alongside per-skill overrides.
- [ ] Respect upstream's temporarily disabled 3D battle view; check glove/world/first-person rendering where models remain visible.

- [ ] Glove slot coverage: test main hand only, offhand only with an empty main hand, Soulbound weapon slot only with both physical hands empty, offhand/menu slot plus an unrelated held item, and gloves in multiple slots. Each case draws one pair in first/third person and battle clones; swapping all three slots away removes both gloves. Check local/remote players, left-handed controls and humanoid possession; a borrowed body's owner's soul weapon must not replace the possessor's own soul weapon.

- [ ] Tough Glove: hold one in the main hand, then off hand; both hands wear a single orange 3D pair. Test player models (wide/slim), left-handed setting, Human enemy, turn-based player/PvP clones, live combat and a possessed humanoid. Both padded gloves follow punches/spells/defending poses. First person shows both hands and one main-hand swing. Verify only one inventory item, original stats, empty/non-glove swap cleanup, offhand shield/item, armor overlap, invisibility, resource-pack textures, and no weapon on non-humanoid possessed mobs. Epic Fight must not be required.

- [ ] Body warning: while A is a free soul or possesses another body, damage A's parked original body. Only A sees “You feel as if something is happening to your body” at the selected tool name position, in A's soul color. Test different soul colors, empty hand, switching tools, survival/creative, repeated hits, death, disconnect and hidden HUD. The warning refreshes on each hit, fades after three seconds, and normal tool names resume. No warning for rejected damage to a hidden backing body or another player's parked body.

- [ ] Empty body: leave A, enter A with B; B retains B's level/spells/menu armor and uses A's skin/physical armor/inventory.
- [ ] Owner return: A's return key triggers the struggle against B, including when B entered an unattended body.
- [ ] Equal-level contest: repeat with a fixed pair; only the original owner has the configured advantage.
- [ ] Threshold: test gap 9, 10, 11, then change threshold to 15; weaker soul always loses at/above threshold.
- [ ] Cooldown: losing soul, displaced owner, teleport-return key, proximity entry, voluntary exit, and Monster expiry cannot bypass the timer.
- [ ] One challenger: a third soul cannot enter a body with an active struggle.
- [ ] Combat interruption: have the incumbent start a mob fight and a PvP fight during a struggle; only the entering soul is ejected.
- [ ] Completed possession: normal fight uses the possessor's own skills and the borrowed body appearance.
- [ ] Combat lock: possession, return contests, and voluntary exit are blocked while fighting.
- [ ] Monster: possession succeeds regardless of level; increasing absorbed souls shortens duration, respecting minimum.
- [ ] Mob timer: off gives no expiry; enabling it uses exactly base Monster time × configured multiplier.
- [ ] Eligibility: zombie, skeleton, spider, and a modded hostile can be entered. Passive mobs, Wither, Ender Dragon, modded bosses, and rare Boss-marked mobs are rejected.
- [ ] Rendering: human skin, skeleton weapon attacks, quadruped hidden weapon, spell effects, twitch, and directional chest pull look correct to both clients.
- [ ] Inventory: swap slots, selected hotbar slot, equipment, pick up items, transfer items to containers, and drop items while possessed; verify exact counts after exiting.
- [ ] Owner soul death with a guest: guest is ejected; owner body dies; guest's own body survives.
- [ ] Possessor death inside a player: borrowed body stays empty, its inventory remains, and possessor's original body dies.
- [ ] Possessor death inside a mob: mob survives with half its HP at entry and regains AI.
- [ ] Empty body hazard: lava/fall/void destroys original body and kills its soul, even while the soul is in a borrowed body.
- [ ] With keepInventory=false, repeat every death case with soul and original body far apart and in different dimensions; verify items drop once only at the original body's current position.
- [ ] With keepInventory=true, repeat all death cases; verify retained items and no world drops.
- [ ] Test both gamerule values in Soulbound's Dark Worlds as well.
- [ ] Disconnect/reconnect each role: challenger, incumbent, possessor, original owner.
- [ ] Clean restart during human/mob possession restores inventories and AI.
- [ ] Forced process termination in a test world during possession restores inventories and mob AI without duplicate live inventory. Check save-order edge cases carefully.
- [ ] Non-operator cannot change settings; operator changes sync to other operators and persist after restart.

## 0.1.2 clone regression

- [ ] Possess a zombie in full diamond armor: only the controlled model appears, with no second armor set walking beside it.
- [ ] Possess a creeper: no separate creeper or targetable hitbox follows the player.
- [ ] Attacking where the background body is parked cannot start a battle against that body.
- [ ] Start a fight beside other hostiles: the possessed mob's parked entity is never added as an extra enemy.
- [ ] Other mobs cannot target or push the parked entity; they can still fight the controlling player normally.
- [ ] Exit normally or expire the timer: the released mob is visible, targetable, has AI again, and can be fought normally.
- [ ] Retest soul-death HP-halving and disconnect restoration.

## 0.1.3 skill balance regression

`./gradlew runSkillSmoke` loads the integration test mod through Fabric and exercises the actual transformed skill classes. It must print `SOULBOUNDPLUS SKILL SMOKE PASSED` before the normal EULA gate. Do not install the smoke-test JAR in a normal game.

- [ ] As host/operator, menu key → Settings → Server → Skill Balance → Edit opens the searchable editor.
- [ ] Search by display name, enum ID, and family; resize the window; page through every family.
- [ ] Change a damage skill's TP cost and fixed base range, then use it in turn-based and live combat. Native stat/global/accessory scaling still applies.
- [ ] Change shield reduction/duration and a heal's base values. Verify shield values may have minimum greater than maximum because these are independent parameters.
- [ ] No enable/disable control exists. A legacy saved zero flag does not disable the skill in either combat mode.
- [ ] Legacy disabled settings become usable immediately after updating; learned skills and prerequisite progress remain intact.
- [ ] Adjust Snowgrave TP cost; check reservation, execution and TP display. Its other native requirements still apply.
- [ ] Join with a second client; both see the server values. Disconnect and join a different server; previous server overrides must be cleared.
- [ ] Restart the server and check overrides persist. Reset restores the original skill, including Snowgrave's dynamic TP cost.
- [ ] A non-operator cannot edit; revoke operator access with the editor open and verify subsequent updates are rejected.
- [ ] Test malformed/out-of-range input and saving on a read-only config directory; no unpersisted update should become active.


## 0.1.4 mob vision regression

`./gradlew runVisionSmoke -x downloadAssets` loads the client environment and verifies actual Camera/GameRenderer transformations and vanilla shader resources, then exits before opening a window. It is not a visual gameplay test. Do not install either smoke-test JAR in a normal game.

- [ ] Possess a creeper: first person is green; spider/cave spider: multi-eye; enderman: inverted.
- [ ] Zombie/skeleton and a modded hostile: normal colors with the default model's eye height.
- [ ] First-person hands/items are hidden only during mob vision; normal hand rendering returns in first-person live combat.
- [ ] F5 through both third-person views and back: effects and height offset disappear/reappear without sticking.
- [ ] Start/end turn-based combat while possessing each shader mob: standard battle view; effect returns only after combat.
- [ ] Test live combat with first-person lock-on enabled: locking on, opening the live menu or an action lock disables mob vision.
- [ ] Exit, owner death/ejection, possessor death, timer expiry, disconnect/reconnect, dimension change and resource reload: no lingering vision.
- [ ] Human/Monster player possession and ordinary soul mode: no mob filter or eye-height override.
- [ ] Another mod's active post-processing is preserved; retry after it ends. Test shader packs separately.
- [ ] Check low ceilings and enderman eye height; player collision dimensions are unchanged.


## 0.1.5 backpack/accessory gameplay acceptance

`./gradlew -PbodyGearIntegration runBodyGearSmoke` uses optional test JARs placed in `integration-mods` (not distributed in the addon). The fixture tests cover public Curios API contracts; they do not run Curios on NeoForge. With the Fabric test mods installed, the test additionally creates a real Sophisticated backpack and verifies storage UUID/color component roundtrips. It stops at the normal EULA gate; no world is started.

- [ ] Fill a real backpack with numbered items and upgrades; record UUID, colors, nested bags, filters, liquids and energy. Leave your body, open it using its native key, make changes, and return. Check exact counts/IDs.
- [ ] Repeat with Fabric chest/offhand inventory backpacks and a Trinkets-worn backpack; repeat with native NeoForge Backpacks/Core/Curios through Connector.
- [ ] Equip Curios normal and cosmetic items and set render toggles. Soul mode retains access. A possessor receives those items and native effects; the displaced owner has no second usable copy.
- [ ] Original owner possessing a third body: taking their unattended original body must use that original body's stored gear, not the third body's gear.
- [ ] Keep a backpack/Curios screen and cursor stack open when possession resolves or the owner reclaims the body; old screen IDs must stop accepting clicks.
- [ ] Extract items, shift-click, swap/drop a backpack, and equip a new accessory while the original body is occupied. No item may be erased or copied; deposited/dropped items must be at that body.
- [ ] Try mismatched slot types and insufficient capacity: deny possession and leave both inventories unchanged.
- [ ] Repeat owner/possessor/mob death with both keepInventory values. Check backpack contents and accessories drop/retain exactly once, at the original body when dropped.
- [ ] Test Curios attribute removal/equip effects after transfers and after respawn. Menu-equipped Soulbound gear must remain with its soul.
- [ ] Test disconnect, clean stop, and disposable-world unclean restart while using body-bound backpacks. Recovery across independently saved third-party backpack storage still requires testing.
- [ ] Parked empty-body accessory rendering is not added by this integration. Test possessed-player rendering with the installed mods separately.
