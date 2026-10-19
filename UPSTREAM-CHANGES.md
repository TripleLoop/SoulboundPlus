# Soulbound 2.0.20 to 2.0.21 comparison

Compared the supplied original JARs by entry bytes, class signatures and decompiled/bytecode method bodies. Nine classes changed: ReplicaBosses and four of its nested types, TurnBattleClientMod, VoidMenuScreen and two of its nested types.

The client change opens ReplicaHubScreen with no parent screen. Menu changes affect navigation, sibling switching and item rendering. Replica registration/end handling changed. SoulWalk, SoulBodyEntity, BattleManager, ServerSettings, SettingsScreen, SoulGlowRenderer, skill classes, CloneAnimator, equipment APIs and original Human weapon sprites are byte-identical. No upstream possession, per-skill editor or other replacement for this addon's features was found in these changes.

SoulBound+ 0.1.11 is rebuilt against 2.0.21 and requires that version. The menu superclass still provides the click/constructor API used by the new Edit button; the existing virtual-battle hooks remain present. This build also includes the requested movement/rendering corrections, dummy, models and timer cues. No upstream JAR is modified or bundled. Gameplay of Replica/possession interactions still requires acceptance testing.

---

# Soulbound 2.0.19 to 2.0.20 comparison

Compared the supplied 2.0.19 and 2.0.20 JARs, including class signatures and the new Replica battle start implementation.

The added code and resources implement Replica bosses, their hub, patterns and sprites. Existing battle, Dark World and UI code also changed. No new counterpart to SoulBound+'s possession, body-bound equipment, per-skill editor, warning or paired gloves was found.

The new ReplicaBosses.startFight method calls BattleManager.tryStartVirtual, which the addon already hooks. Replica boss definitions are virtual battle data, not MobEntity subclasses, so they do not introduce a new possessable boss type. All existing addon-targeted BattleManager method signatures remain present; the added methods are lastStandThreshold and markEnemyTurnStart. Core SoulWalk, SoulBodyEntity, inventory/accessory integration interfaces, skill classes, ServerSettings, SettingsScreen, CloneAnimator, and original glove assets are unchanged from 2.0.19.

SoulBound+ 0.1.10 pins the new dependency and refreshes the tested build. No unrelated behavior changes or upstream JAR modifications are included. Existing configs and explicit skill overrides remain in place.

Full Replica/possession interaction still needs in-game acceptance testing. Automated results are recorded in VALIDATION.txt.

---

# Soulbound 2.0.16 to 2.0.19 comparison

Compared the supplied original JARs and the author's Modrinth version API changelogs for 2.0.17, 2.0.18 and 2.0.19. The supplied 2.0.19 JAR matches the published file's SHA-512.

No replacement for SoulBound+'s possession/contests, body-bound backpack/accessory transfers, per-skill balancing editor, original-body damage warning, paired 3D Tough Gloves or possessed-mob camera was found. Native global skill multipliers already existed before this update; they are distinct from the addon's per-skill editor.

Evidence: SoulWalk, SoulBodyEntity, CloneAnimator, HumanEnemies and Net121 class bytes are identical between the two supplied versions, as are the Tough Glove model and texture. The native server settings changed enemy level controls to distance scaling; they did not add the addon's per-skill editor. Added classes cover Darkners/bosses, shopkeepers/shops, area levels, boss dialogue and Dark World support.

The main new content is experimental generated Darkners and fountain-guarding bosses, Dark Dollars, travelling shops and distance-based area levels. Combat changes include first-strike damage, skill/armor/defense adjustments, server-side live-combat hit detection and several battle/UI fixes. Releases 2.0.18 and 2.0.19 repair Darkner-boss softlocks; 2.0.19 also fixes a Darkner animation. The author temporarily disabled native 3D battle view.

## Addon changes

- Targets exactly Soulbound 2.0.19 on Minecraft 1.21.1 Fabric; no upstream JAR is modified or bundled.
- Blocks Darkner bosses, which are deliberately skipped by upstream's ordinary elite roll and could otherwise bypass the older boss check.
- Blocks the invulnerable non-combat shopkeeper, whose custom class does not inherit Minecraft's PassiveEntity.
- Preserves an ordinary possessed Darkner's generated visual item and seed on clients. This is render-only metadata and does not grant a new item or native Darkner skills.
- Retains saved server skill overrides; untouched and reset skills use current upstream defaults and scaling.
- Keeps upstream's disabled 3D battle view disabled.

## Sources

- https://api.modrinth.com/v2/version/7weLXRWW (2.0.17)
- https://api.modrinth.com/v2/version/azVSpaMO (2.0.18)
- https://api.modrinth.com/v2/version/WuDbZLlA (2.0.19)
- Supplied turnbattle-2.0.16.jar and turnbattle-2.0.19.jar class/resource comparison.

Build and runtime-loading checks are recorded in VALIDATION.txt. Full gameplay, graphical appearance and NeoForge/Connector validation still require the checks in TESTING.md.
