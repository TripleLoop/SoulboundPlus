# SoulBound+ 0.1.12 compatibility

Minecraft 1.21.1 / original Soulbound Turn Battle 2.0.21. Optional mods are not bundled. The optional integration checks listed below were originally performed against addon 0.1.5 with Soulbound 2.0.16; they are historical evidence, not a fresh gameplay certification for 2.0.21. The integration code remains in place.

| Integration | Intended route | Validation performed |
|---|---|---|
| Sophisticated Backpacks Fabric 3.23.4.3.106 | Fabric | Loaded with the real Core/Trinkets dependencies; real backpack storage UUID and color component save/clear/restore passed. |
| Sophisticated Core Fabric 1.2.9.21.168 | Fabric | Real component codecs and wrapper used by the above check. |
| Trinkets 3.10.0 | Optional Fabric worn-backpack slots | Loaded alongside the real backpack/core mods; Inventory API transfer and full stack component preservation checked with inventory fixtures. No in-game wearable slot interaction was exercised. |
| Sophisticated Backpacks/Core NeoForge | NeoForge + Connector | Uses the same backpack item namespace and full Minecraft ItemStack components, without linking a loader-specific backpack API. Full NeoForge/Connector gameplay is not tested here. |
| Curios 1.21.1 API (1.21.1 branch / 9.x API) | NeoForge + Connector | Public API contracts reviewed against upstream; normal/cosmetic slots, render toggles, capacity checks and complete stack data tested with API-shaped fixtures. The real Curios/NeoForge runtime has not been exercised. |

The production addon has no hard Curios, Trinkets, backpack or core dependency. Optional accessory APIs are resolved only when installed. Soulbound menu gear is not transferred by this integration.

Body rules: a free soul can access its own body's backpack/accessory equipment. When someone possesses that body, its physical gear and access move to the occupant; the original soul cannot use a duplicate copy. Other bodies' original-owner equipment is never obtained from an owner who is currently wearing a third body's gear. Open handlers close on ownership changes. Drops from a free soul are placed at its original body.

Slot definitions and capacities remain controlled by Curios/Trinkets. Possession is rejected before changing inventories if any equipped item cannot fit the recipient's slot layout. New accessory items acquired while controlling an ordinary mob are dropped at that mob when it cannot wear them.

Important limits: this is an inventory/ownership integration, not an added third-party renderer for Soulbound's parked body entity. Backpack storage continues to be saved by Sophisticated Core. Full GUI interaction, upgrades that depend on world interaction/pickup rules, item drop rules supplied by other mods, attribute effects, death/respawn, and crash recovery across third-party saved data need the disposable-world checks in TESTING.md. A component roundtrip is not a full gameplay test of backpack contents.

## Public API references

- Fabric backpack port: https://github.com/Salandora/SophisticatedBackpacks/tree/1.21.x-fabric
- Curios 1.21.1 API: https://github.com/TheIllusiveC4/Curios/tree/1.21.1
- Curios item handlers: `getCuriosInventory`, `getCurios`, `getStacks`, `getCosmeticStacks`, `getStackInSlot`, `setStackInSlot`, `getRenders`, `getUpdatingInventories`.
- Trinkets: `getTrinketComponent`, `getInventory`, and Minecraft Inventory methods.
- No upstream code is bundled or copied into the addon.
