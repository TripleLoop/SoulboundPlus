# SoulBound+ 0.1.14

A separate Fabric addon for Minecraft 1.21.1 and **Soulbound Turn Battle 2.0.21**.

## Install

Use Java 21, Fabric Loader 0.16.5+, Fabric API, the original `turnbattle-2.0.21.jar`, and `soulbound-plus-0.1.14.jar`. Replace the older addon. Install matching versions on the server and every client. The upstream mod and optional mods are not bundled.

## 0.1.14: possession animations and free camera

Occupied human bodies still clash for **10 seconds by default**, including overwhelming level gaps. The five chest-led directional yanks now fit into the first phase. The final 30% of the clash, capped at three seconds, is reserved for the native soul-removal gesture: struggle limb motion and physical displacement have finished before the hand reaches for the losing soul. With a 10-second clash, this means a seven-second struggle phase followed by a three-second extraction. Changing the duration scales both phases without extending the total timer.

Humanoid mob extraction is applied after the complete mob-specific animation, so zombies/husks cannot overwrite it with their arms-forward pose. The borrowed model receives the native pose once; wrist offsets do not double. The final chest tug has a continuous, smaller recoil, and the grabbing arms stay stable during it. Released mobs inherit the controller's body/head facing. Non-humanoid mobs retain their body pull without human arm poses.

Possessed humanoid bodies use vanilla player-style idle/walk/sneak/swim and item-use motion instead of the mob stance. Detection follows humanoid bones, including standard bipeds such as zombies, husks, skeletons, strays, drowned, piglins and endermen, plus independent-arm humanoids such as illagers. The mob's original model, proportions and textures remain. Crossed arms are hidden while the separate possessed arms move; normal mob animation/visibility returns after release. Combat and native soul gestures layer over this player-style base.

Soul-removal no longer forces the native cinematic camera or blocks mouse look. Keep your chosen first/third-person perspective, switch views normally and look around. This relaxes look input only; the native extraction movement lock remains. Menu/fountain cinematics and battle cameras keep their own behavior. Possession itself never changes the camera entity or forces a perspective.

Walking back into your own body and entering a borrowed body retain the native soul-colored ring and graze sound. Default retry cooldown remains **30 seconds**, including return-key challenges. Server menu duration/cooldown/pull-strength settings remain configurable.

Existing unversioned config values matching the old 3-second struggle and 15-second cooldown migrate once to 10 and 30. Other customized values are preserved. The old separate overpower duration remains removed; level gaps still determine odds. Install matching addon versions on clients and server.

## Retained from 0.1.12: personal skill order and visible dummies

In the main Soulbound stats menu (usually M), grab the three white lines at the right of a skill row. Drag up/down, then release at the yellow insertion marker. Hold near the top or bottom to scroll a long list. Escape or a right click cancels. Clicking the skill name still opens its native skill tree.

T-Action is now in this list and can be moved like any skill. Top-to-bottom menu order becomes the normal battle skill order (across the battle's existing slots). Changing TP does not reshuffle it; unaffordable skills keep their position and native cost restrictions. Skill identities, unlocks, equipment and cast messages are unchanged. Live combat uses the same relative order for its supported skills; this does not add a new live-combat T-Action. Card/deck modes keep their native indexed order.

Ordering is a personal client preference saved in `config/soulbound-plus-skill-order.json`, by player profile and selected character/recruit. It survives reconnects and restarts, needs no operator permission, and does not change another player's order. Temporarily unavailable/unequipped skills keep their saved positions; newly learned entries are appended after saved entries. The first unsaved order has T-Action first, followed by skill names alphabetically.

Fixed test dummies being classified as hidden backing entities even when unoccupied. Unoccupied Human, Monster and empty dummies now pass the renderer and soul-entry visibility gates; only their parked backing body is hidden while occupied. Combat exclusion remains separate, so visible dummies cannot start battles. All prior dummy commands and caps remain. Approach a dummy's chest in soul mode to possess it.

## Features retained from 0.1.11

- Blocks pushing between a controller and the hidden backing body; clears leftover movement when entering a borrowed body.
- Copies mob walking phase as well as speed. Native world poses stay active outside combat; combat keeps the soul's attack/spell animation. Preserves supported baby/size/variant metadata and Darkner appearance.
- Removes skill disabling. Settings → Server → Skill Balance now has an **Edit** button. Previously disabled skills become usable; numeric overrides and learned progress remain.
- Adds operator-only Human, Monster and empty test dummies, command editing, struggle/chest-pull previews and voluntary exit. Human levels cap at 99; Monster absorbed souls cap at 7.
- Simplifies orange gloves into blocky padding and moves thumbs to the marked outer sides. Main hand, offhand and Soulbound weapon slot each render both gloves.
- Ballet Shoes follow both feet. Torn Notebook is a smaller closed purple book. Empty Gun is smaller with a solid barrel, cylinder and grip. Knives, pan and climbing claws gain block depth while retaining the upstream palette.
- Removes the remaining-time text. Timed possession reveals the soul at **50% elapsed**, adds a soul-colored outline at **90% elapsed**, then plays Soulbound's soul-removal sound on ejection. Unlimited possession has no warning stages. Combat still delays expiry until the fight ends.
- Rebuilt and checked against the supplied Soulbound 2.0.21 JAR.

## Solo test dummy

Requires host/operator permission (level 2). Commands:

```
/soulboundplus dummy spawn human 50 bravery
/soulboundplus dummy spawn monster 7
/soulboundplus dummy spawn empty
/soulboundplus dummy set level 99
/soulboundplus dummy set soul justice
/soulboundplus dummy set souls 3
/soulboundplus dummy preview struggle
/soulboundplus dummy preview eject
/soulboundplus dummy clear
```

Human dummies have a soul and LV 1–99. Omitting their arguments uses your level (capped at 99) and soul type, falling back to Determination for a Monster player. Choices are determination, perseverance, integrity, patience, justice, bravery, kindness and ori. They show the selected soul on the chest and use the configured human-owner contest odds. Winning permits unlimited possession; losing ejects your soul and applies the retry cooldown.

Monster dummies have a Monster soul and 0–7 absorbed souls (default 0). Entry ignores level and uses the normal Monster-player time formula, including the server's base time, per-soul reduction and minimum. They are timed even if the ordinary mob timer is disabled. Empty dummies have no soul and allow immediate, unlimited entry.

Spawn places the dummy two blocks ahead. Leave your body and move into its chest to possess it; use normal soul removal to leave. The `set level` and `set soul` commands edit your nearest Human dummy; `set souls` edits your nearest Monster dummy, within 16 blocks. Finish a struggle and leave before editing. Arguments outside the caps are rejected. Levels and absorbed souls are also clamped when loaded from saved data.

Preview commands target your nearest unoccupied dummy within 16 blocks and show the animations without leaving your body. Clear removes your loaded dummies and drops their stored physical equipment once. Unloaded dummies must be revisited to clear them. Dummies do not attack, drop free gear, spawn naturally or participate as enemies in battles. They simulate test occupants; they do not replace multiplayer ownership/death testing.

## Possession

Leave your body with Soulbound's existing controls. Enter another body's chest the same way you enter your own. Empty human bodies allow immediate entry; occupied human bodies trigger a struggle. Original owners also contest occupied bodies when using the return-to-body key.

Your soul keeps its level, skills and Soulbound-menu equipment. Physical inventory, armor, backpacks and accessory slots belong to the body. You can use them while controlling that body; ownership does not transfer.

Use soul removal to exit voluntarily. New possession and voluntary exit are blocked during combat. Starting a fight during a struggle ejects the entering challenger. Completed possession continues with the borrowed appearance and your soul's combat abilities.

Non-passive battle mobs can be possessed; bosses, Boss-marked/elite mobs and shopkeepers cannot. Humanoid mobs show weapons; other models hide weapons while retaining their stats. Mob vision uses native spectator filters in first person, and switches off in third person, combat and cinematics. Player collision dimensions and reach remain unchanged.

## Contests, cooldowns and durations

Default threshold is 10 levels: at or beyond it, the weaker soul loses. Equal levels give the invader 45% and original owner 55%; odds scale toward 0%/100% at the threshold. Original ownership keeps its advantage even after another soul takes the body. Two unrelated invaders use a neutral 50/50 baseline. One challenger is allowed per body.

Default struggle is 10 seconds for every occupied-body contest. Both participants receive a 30-second per-body retry cooldown, including teleport-return attempts. Struggle duration, cooldown, directional pull strength and chest-pull strength are configurable.

Monster-player possession lasts 30 seconds minus 1 second per absorbed soul, with a 2-second minimum. Ordinary mob possession is unlimited by default. Its optional timer defaults to twice the Monster base duration. Server settings configure these values.

If a soul dies, its original body dies. A guest is ejected if the borrowed body's owner dies. If the guest dies, the borrowed body survives; a borrowed mob is left with half its entry health. With keepInventory enabled, the original owner's items are retained. Otherwise items drop once at the original body's location. Disconnect and shutdown unwind possession; recovery data is retained for crash recovery.

Damage to your parked original body shows **You feel as if something is happening to your body** above the hotbar in your soul's color. This warning remains separate from the removed possession countdown.

## Server skill editor

Menu key (usually M) → Settings → Server → Skill Balance → **Edit**. Search by name/family/ID, select a skill, change values and press Apply. Changes save and synchronize immediately; rejoining is unnecessary. Reset restores native defaults. Host/operators can edit; other clients cannot change server values.

The editor covers 233 active skill entries: PSI, Lightner, Human Mage, Monster, Soul Mage, Ori and Vessel Actions. Editable values are TP cost, required level, base minimum, base maximum and extra. Shield/buff labels explain their alternate meanings. Skill unlock dependencies remain native. No skill can be disabled through this editor.

Parameters retain their native meaning and scaling. Some specialized skills ignore a field or use hardcoded rules. Shields use reduction/duration; buffs use duration/strength; extra may mean hits, turns, chance or mercy. A 999 healing value can mean full heal. The editor does not edit passive/stat nodes, ACT commands, skill-learning points or native animation timing. Configuring Snowgrave's TP cost makes it fixed; Reset restores its dynamic cost.

Possession settings use `config/soulbound-possession.json`. Skill overrides use `config/soulbound-plus-skills.json`. The six-number stored format is retained for migration: `[reserved, tpCost, requiredLevel, minimum, maximum, extra]`. The former enable flag is ignored and normalized to 1 when loaded/saved; it is not a setting. Ranges: TP 0–10000, LV 1–10000, base 0–100000, extra 0–10000. Stop the server before editing files manually.

## Optional backpack/accessory integration

Sophisticated Backpacks/Core can expose the original body's backpack through normal controls while its soul is out. Storage UUID/components are preserved; the item stays body-bound. Possessing another body uses that body's physical backpack/accessory gear. Soulbound menu equipment stays soul-bound. Forge/NeoForge Curios compatibility is optional via Connector and its public API; see COMPATIBILITY.md for the tested limits.

## Validation and remaining checks

See VALIDATION.txt for automated results, TESTING.md for in-game checks and UPSTREAM-CHANGES.md for the JAR comparison. Automated client checks stop before window creation. No graphical or two-player gameplay session has been run here. Visual fitting on unusual/modded models, real movement/input, inventory/death/reconnect transitions and multiplayer contest results still require testing in a disposable world. Existing historical optional-mod checks do not certify Connector gameplay on this version.

## Build

Use Java 21. Copy the original upstream JAR to `libs/turnbattle-2.0.21.jar`, then run `./gradlew build`. Run `runSkillSmoke`, `runVisionSmoke -x downloadAssets` and `runBodyGearSmoke` separately from the production build; smoke test JARs must never be installed in a normal instance. Source contains the model generator in tools/; it reads the upstream sprites without redistributing them.
