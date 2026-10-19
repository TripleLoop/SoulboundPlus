# Previous release notes (historical)

These describe earlier builds. Use README.md for current controls and behavior.

## 0.1.13: directional chest pulls and native entry effects

Introduced five synchronized visual/physical chest-led pulls across a 10-second occupied-body contest, native extraction poses and soul-colored entry rings. Retry cooldown defaults changed to 30 seconds, with one-time migration of old defaults. In 0.1.14, those five pulls are rescheduled into the first phase so they no longer overlap the final extraction gesture; use the current README for timing.

## 0.1.10: Soulbound 2.0.20 compatibility

Updated the exact dependency to 2.0.20 and rebuilt against the supplied JAR. The new Replica bosses are virtual encounters, not possessable world entities. Their battle start uses the existing `tryStartVirtual` integration, so the addon's combat/possession rules continue to apply through that entry point. No upstream content is copied into the addon. Existing configuration files, saved skill overrides and features are retained.

## 0.1.9: Soulbound 2.0.19 compatibility

Updated the pinned dependency and integration checks for 2.0.19. Ordinary hostile Darkners can be possessed under the existing mob rules; their generated item and appearance seed are synced to the borrowed-body model. Darkner bosses and the non-combat shopkeeper are explicitly excluded. Existing possession, inventories, soul gear, balance overrides, warnings, paired gloves, mob vision and recovery rules remain in place.

The upstream update changes native skill defaults and scaling. Untouched skills use the new defaults automatically; saved explicit skill overrides remain as configured. Use **Reset** in Skill Balance if you want an overridden skill to return to its new native values. Existing configuration filenames and addon ID are unchanged.

Soulbound 2.0.17–2.0.19 temporarily disables its own 3D battle view. This addon respects that setting; it does not re-enable the upstream view. Paired glove visuals remain available wherever humanoid models/hands are rendered. See UPSTREAM-CHANGES.md for the comparison and testing limits.

## 0.1.8: offhand and Soulbound weapon-slot gloves

Paired glove rendering now directly checks the main hand, offhand and Soulbound weapon slot, including player battle proxies using that soul's synced gear. Any of those slots can supply one Tough Glove to draw both hands; multiple occupied glove slots still produce only one visual pair. First-person rendering supports an empty main hand with an offhand/menu-slot glove and retains unrelated held items. Inventory and gameplay remain unchanged.

## 0.1.7: paired 3D Tough Gloves

The Human Bravery **Tough Glove** renders as an original pair of orange padded 3D gloves, with raised knuckles, thumb padding, dark cuffs and lighter wrist straps. One held glove dresses both animated hands on biped models, including Soulbound's humanoid battle clones and humanoid borrowed bodies. First-person glove use shows both arms, with the attacking main arm retaining the vanilla swing. The models follow the existing arm poses; combat animations, stats, inventory, damage and equipment rules are unchanged, and no second item is created. Non-humanoid borrowed mobs still hide weapons under the existing rules. Inventory/dropped-item icons retain Soulbound's original artwork. Epic Fight is a visual inspiration only and is not required; no Epic Fight assets or code are bundled.

Other Human weapon redesigns remain proposed designs, not part of this build: cyan-handled chunky Toy Knife; blue Ballet Shoes with ribbons; purple thick-paged Torn Notebook; deep black Burnt Pan with a rim and wooden handle; blocky yellow-detailed Empty Gun; and a steel Real Knife with a red-brown grip.

## 0.1.6: body damage warning

When your parked original body takes damage, an owner-only warning reads **You feel as if something is happening to your body** in your current soul's color. It temporarily replaces the selected tool's name above the hotbar, even with an empty hand, for three seconds after the latest hit and fades at the end. Item names return afterwards. This uses the normal hotbar HUD visibility and does not add a full possession HUD. Disconnect and death clear the notice.

## 0.1.5: body-bound backpack and accessory access

Sophisticated Backpacks/Core items can be used in soul mode through the backpack mod's normal controls, including its open-backpack key. This works by temporarily exposing the original body's backpack item to its free soul; its storage UUID and components are preserved. The item remains logically owned by that body. Contents and upgrades continue to use Sophisticated's original storage rather than a new backpack copy.

Curios equipment, cosmetic items and render flags now follow the body during possession. The optional Fabric Trinkets integration also handles worn Fabric backpacks. A free soul can use its own body's equipment. When that body is possessed, its owner loses that access and the possessor receives the body's gear. The possessor's own backpack/accessories stay with their original body, and access returns when possession ends. Soulbound menu equipment remains attached to the soul as before.

Open inventory/backpack/accessory screens close when gear changes bodies. Items dropped by a free soul are relocated to its original body. Ordinary items withdrawn from a backpack into the soul's main inventory are deposited back at the body under the existing soul inventory rules; the body-bound backpacks remain accessible. Gear acquired while controlling a mob is left with that mob on exit; accessories that the mob cannot wear are dropped there.

The recovery journal includes accessory data and backpack access handles. For a linked-body death, keepInventory=true stashes accessories for restoration after respawn; false drops them at the original body's location. Curios' normal death pass sees cleared slots, preventing a second accessory drop. Normal deaths outside the possession/body-link system keep their existing mod behavior.

Optional integrations do not become mandatory dependencies. On Fabric, install the Fabric Sophisticated Backpacks/Core ports and their required dependencies. For the Minecraft 1.21.1 Forge-family route, use the native **NeoForge** backpack/core and Curios mods on **NeoForge with Sinytra Connector and Forgified Fabric API**, loading this Fabric addon and the original Soulbound through Connector. This is not a native Forge/NeoForge build, and full Connector gameplay has not been tested here. Do not install both platform variants of the same backpack/core mod in one instance.

Curios/Trinkets slot definitions remain server controlled. If another body's equipped items cannot fit your available slot types/capacity, possession is refused before transferring anything. The integration does not add third-party backpack/accessory render layers to Soulbound's parked empty-body entity; it covers ownership, access, transfers, data and recovery. Rendering on a possessed player continues through the installed equipment mods.

See COMPATIBILITY.md for tested versions and exact validation limits.

## 0.1.4: first-person mob vision

While possessing a mob, first person uses the mob model's standing eye height and hides the player's first-person hands/items, like spectator mob view. Creepers use vanilla green spectator vision, spiders/cave spiders use vanilla multi-eye vision, and endermen use inverted colors. Other eligible mobs have normal colors at their model's eye height, matching vanilla spectator behavior. No new vision filters are invented for modded mobs; compatible subclasses use the same vanilla effects.

The mob view turns off in both third-person perspectives, turn-based battles, live-combat lock-on/menus/action locks, and Soulbound cinematic cameras. It returns automatically when those conditions end and you are still possessing the mob in first person. Leaving the body, death, or disconnect clears it. Your game mode, controls, abilities, and actual camera entity stay unchanged. This is a visual camera offset; it does not change player collision size or attack reach, and uses the existing default mob model rather than syncing individual age/variant/scale data.

The effect uses Minecraft's native spectator post-processing, respects resource-pack replacements, and does not replace another active post-processing effect. Shader-pack compatibility and visuals still need in-game verification.

## 0.1.3: server skill balancing

Open Soulbound's menu (usually **M**) → **Settings** → **Server** → **Skill Balance — Open Editor**. Click the toggle-style editor entry to open it. Search by skill name, family or internal enum ID; select a skill, edit its values and click **Apply**. **Reset** restores that skill's original behavior. Changes are immediate, saved on the server, and synced to connected clients. Only operators or the single-player host can apply changes. Install this version on both server and clients and remove the older addon JAR.

Every native active `BattleSkill` in Soulbound 2.0.16 is included: PSI, Lightner, Human Mage, Monster, Soul Mage, Ori, and the Vessel Action implementations. Per skill you can set **enabled**, **TP cost**, **required level**, **base minimum**, **base maximum**, and **extra**. Disabling is enforced at skill resolution in both turn-based and live combat, including already-equipped skills. Disabling during a cast can cancel its pending effect; already-paid costs are not refunded.

These are Soulbound's native parameters, so their meaning depends on skill type. Damage/heal/TP skills normally use a base roll range; shields use reduction percentage and duration; buffs use duration and strength; extra can mean hits, freeze turns, burn/sleep chance or mercy gain. The editor labels shield/buff parameters separately. Some specialized skills ignore certain parameters or apply hardcoded rules; this addon does not rewrite those rules, passive/stat-tree nodes, ACT commands, skill-learning point costs, or native animation timing. Native global multipliers, stat scaling, immunities, minimum durations, accessory discounts and special requirements still apply. `999` can be a full-heal sentinel, not literal healing. A maximum below the minimum produces the native minimum value for rolls, and is normal for shield/buff parameters.

Untouched skills retain their original behavior. Applying an override stores all six displayed values for that skill explicitly. For Snowgrave this makes its TP cost a fixed configured cost; **Reset** restores its original double-max-TP calculation. Descriptions written into Soulbound may still mention the original values for special skills; the editor shows the server values.

Overrides are stored in `config/soulbound-plus-skills.json`. Each skill ID maps to `[enabled, tpCost, requiredLevel, minimum, maximum, extra]`; enabled is 0 or 1. Allowed ranges: TP 0–10000, LV 1–10000, base parameters 0–100000, extra 0–10000. Existing possession settings remain in `config/soulbound-possession.json`. For offline modpack editing, stop the server before editing the file and restart afterwards. The included skill catalogue lists the native IDs, types and defaults.

## 0.1.2 fix

Fixed the duplicate-looking mob during possession: the parked original mob is now hidden entirely, including armor and nameplates. Its hitbox, targeting, collision and damage are suppressed while occupied. Soulbound cannot start a battle against it or recruit it as an extra enemy in a nearby fight. The controlled player remains visible and fights normally. The original mob returns to normal when possession ends.

## 0.1.1 fix

Fixed immediate return to your own body after the soul-removal animation. The nearby possession scan now excludes your own empty body; normal proximity re-entry requires moving away and coming back. The existing return key still works and respects possession contests/cooldowns.

