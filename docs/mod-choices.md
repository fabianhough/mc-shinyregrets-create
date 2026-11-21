# Mod Choices

Why each mod is in the pack. Minecraft 1.21.1, NeoForge 21.1.267. Last updated 2026-11-21.

## Principles
- **Pure NeoForge.** No Sinytra Connector or Fabric API layers (Continuity was rejected for this reason). Mods that bundle Forgified Fabric API modules internally (Sodium) are fine.
- **Why NeoForge 1.21.1.** Create's active development branch is `mc1.21.1/dev`; its 1.20.1 branch has been quiet since Nov 2025, and Create Aeronautics is NeoForge 1.21.1 only. Fabric 1.20.1 was evaluated and rejected: Create Fabric is a community port that trails (6.0.8.1 vs 6.0.10), and several add-ons have no Fabric build.
- **Vanilla++.** Vanilla plus performance, visual and UI mods and cohesive vanilla-style additions, with Create as the central content mod.
- **Community-proven and polished.** Prefer mods with a long track record that work cleanly together.
- **No magic system.** Ars Nouveau and Ars Creo were dropped (decided 2026-11-20).
- **Aeronautics is a separate integration effort**, not part of this pack's current build.
- **Modrinth only, stable releases only.** See the Rules in the [README](../README.md). Exceptions are listed under [Exceptions](#exceptions).
- **One pack for everyone.** The pack bundles everything (including shaders) so players who aren't familiar with mods get a complete setup from a single Modrinth install. The same `.mrpack` is used for the server.

Exact versions are pinned in each mod's metadata file under `mods/` and `shaderpacks/` (`*.pw.toml`), not in this doc.

**Side** is packwiz's marking from Modrinth's environment data: `client` means client-only (a server install skips it); `both` means client and server. It's recorded for reference; the pack is built as a single client-and-server monolith.

---

## Chosen mods (38)

### Performance and rendering
| Mod | Side | Why |
|---|---|---|
| [Sodium](https://modrinth.com/mod/sodium) | client | Core rendering engine. Chunk loading is noticeably smoother when flying fast. Create lists Sodium ≥ 0.6.9 as its optional floor. |
| [Sodium Extra](https://modrinth.com/mod/sodium-extra) | client | Rendering options, including a built-in FPS counter. |
| [Iris](https://modrinth.com/mod/iris) | client | Shader support. About 120 FPS average with a shader active. |
| [Lithium](https://modrinth.com/mod/lithium) | both | Game logic and tick performance. Create lists ≥ 0.14.7 as its optional floor. |
| [FerriteCore](https://modrinth.com/mod/ferrite-core) | both | Memory usage. |
| [ModernFix](https://modrinth.com/mod/modernfix) | both | Load time and memory. |
| [ImmediatelyFast](https://modrinth.com/mod/immediatelyfast) | client | GUI and text rendering. |
| [EntityCulling](https://modrinth.com/mod/entityculling) | client | Entity rendering. **Under retest:** earlier it dropped FPS from about 120 to about 100 (about 80 looking at a sheep) with shaders on. |
| [Colorwheel](https://modrinth.com/mod/colorwheel) | client | Bridges Create's Flywheel renderer and Iris shaders. Works with Complementary and Bliss. Do not combine with Iris Flywheel Compat (Colorwheel declares it incompatible on Modrinth). |
| [Colorwheel Patcher](https://modrinth.com/mod/colorwheel-patcher) | client | Shader-pack patches for Colorwheel. |

### Shader packs (bundled)
| Shader pack | Side | Why |
|---|---|---|
| [Complementary Reimagined](https://modrinth.com/shader/complementary-reimagined) | both | Bundled so players don't have to find shaders themselves. |
| [Complementary Unbound](https://modrinth.com/shader/complementary-unbound) | both | Same. |
| [Bliss](https://modrinth.com/shader/bliss-shader) | both | Same. Works with Create via Colorwheel and Colorwheel Patcher. |

Shaders are bundled but chosen per player in Iris's shader menu. Modrinth publishes no environment data for shader packs, so packwiz marks them `both`; harmless on a server.

### Maps, recipes and information
| Mod | Side | Why |
|---|---|---|
| [Xaero's Minimap](https://modrinth.com/mod/xaeros-minimap) | both | Minimap. |
| [Xaero's World Map](https://modrinth.com/mod/xaeros-world-map) | both | World map. Create requires ≥ 1.40.2 for its built-in train-map overlay. |
| [JEI](https://modrinth.com/mod/jei) | both | The sole recipe viewer. Create ships a JEI plugin. EMI was tried and turned off (see Rejected and turned off). |
| [Jade](https://modrinth.com/mod/jade) | both | Block and entity info on look-at. |
| [AppleSkin](https://modrinth.com/mod/appleskin) | both | Hunger and saturation display. |
| [Controlling](https://modrinth.com/mod/controlling) | client | Keybind search. |
| [Mouse Tweaks](https://modrinth.com/mod/mouse-tweaks) | client | Inventory handling (drag, scroll and click transfers). |

### Gameplay and quality of life (vanilla++)
| Mod | Side | Why |
|---|---|---|
| [Carry On](https://modrinth.com/mod/carry-on) | both | Enabler for moving animals and relocating mob spawners. |
| [Nature's Compass](https://modrinth.com/mod/natures-compass) | both | Biome finder. Removes the frustration of hunting for a specific biome; fun over friction. |
| [Sophisticated Backpacks](https://modrinth.com/mod/sophisticated-backpacks) | both | Backpacks that scale well, a clean answer to inventory pressure. |
| [Sophisticated Storage](https://modrinth.com/mod/sophisticated-storage) | both | Storage with upgrades. Briefly cut because backpacks already cover a lot, then kept for players who want the customization. |
| [GraveStone Mod](https://modrinth.com/mod/gravestone-mod) | both | Death and graves. Chosen over Epitaphs: it integrates well with Xaero's and is less obnoxious than Epitaphs was on the ATM10 Aeronautics server. |
| [Gravestone x Curios API Compat](https://modrinth.com/mod/gravestone-x-curios-api-compat) | both | Grave handling for Curios slots, so worn backpacks come back. |
| [Curios API](https://modrinth.com/mod/curios) | both | Accessory slots. Crucial to the setup: GraveStone's Curios compat depends on it. Promoted from a dependency to a chosen mod. |
| [Lootr](https://modrinth.com/mod/lootr) | both | Per-player loot chests, so every player gets their own loot from each chest. |
| [Farmer's Delight](https://modrinth.com/mod/farmers-delight) | both | Food and cooking. The first content mod in the pack, in keeping with the vanilla feel. |
| [Easy Villagers](https://modrinth.com/mod/easy-villagers) | both | Villagers as items. |

### Create: core and integrations
| Mod | Side | Why |
|---|---|---|
| [Create](https://modrinth.com/mod/create) | both | The central content mod. |
| [Sophisticated Backpacks Create Integration](https://modrinth.com/mod/sophisticated-backpacks-create-integration) | both | Sophisticated and Create interoperate. |
| [Sophisticated Storage Create Integration](https://modrinth.com/mod/sophisticated-storage-create-integration) | both | Same, for Sophisticated Storage. |
| [Create: Enchantment Industry](https://modrinth.com/mod/create-enchantment-industry) | both | Create-path enchanting and XP. Pinned to the 2.4.x stable line; 2.5.x has been beta-only since Sept 2026. |
| [Create Slice & Dice](https://modrinth.com/mod/slice-and-dice) | both | Automates Farmer's Delight with Create. |
| [Create Cobblestone](https://modrinth.com/mod/create-cobblestone) | both | Cobblestone generation. |

### Create: decor and building
| Mod | Side | Why |
|---|---|---|
| [Create: Design n' Decor](https://modrinth.com/mod/create-design-n-decor) | both | Industrial decor blocks. The main decor mod: it covers what Create Deco and Vibrant Vaults add (including shipping-container vaults) and more. |
| [Copycats+](https://modrinth.com/mod/copycats) | both | Shaped copycat blocks (still testing). |
| [Create Deco](https://modrinth.com/mod/create-deco) | both | Added by choice. Earlier saw an x-ray glitch when breaking a middle block of a shipping container. Overlaps Design n' Decor. |
| [Create Encased](https://modrinth.com/mod/create-encased) | both | Added by choice (extra Create casings and components). |
| [Create: Vibrant Vaults](https://modrinth.com/mod/create-vibrant-vaults) | both | Added by choice. Overlaps Design n' Decor's shipping-container vaults. |

---

## Dependencies (installed automatically, not chosen)

Traced from Modrinth's dependency data (what packwiz uses) and cross-checked against each jar's `neoforge.mods.toml`.

| Library | Side | Required by |
|---|---|---|
| [Sophisticated Core](https://modrinth.com/mod/sophisticated-core) | both | Sophisticated Backpacks, Sophisticated Storage, and both Create integrations |
| [Create: Dragons Plus](https://modrinth.com/mod/create-dragons-plus) | both | Create: Enchantment Industry |
| [Kotlin for Forge](https://modrinth.com/mod/kotlin-for-forge) | both | Create Slice & Dice |
| [Architectury API](https://modrinth.com/mod/architectury-api) | both | Create Cobblestone (listed on Modrinth; the jar itself doesn't declare it) |
| [BaguetteLib](https://modrinth.com/mod/baguettelib) | both | Gravestone x Curios API Compat |
| [Searchables](https://modrinth.com/mod/searchables) | client | Controlling |
| [MezzConfig](https://modrinth.com/mod/mezzconfig) | both | JEI (beta-only; see [Exceptions](#exceptions)) |

Bundled inside other jars (no separate file):
- **Flywheel, Ponder, Registrate:** inside Create.
- **Forgified Fabric API modules:** inside Sodium.
- **MezzConfig 0.6.6:** inside JEI, in addition to the standalone MezzConfig above. NeoForge loads the newest copy present.
- **XaeroLib:** inside both Xaero's Minimap and Xaero's World Map.

### Dependency tree

Required dependencies only. A mod's children require it.

```
Create  (bundles Flywheel, Ponder, Registrate)
├── Create: Dragons Plus
│   └── Create: Enchantment Industry      (also requires Create)
├── Create Slice & Dice                   (also requires Kotlin for Forge)
├── Create Cobblestone                    (also requires Architectury API)
├── Create: Design n' Decor
├── Copycats+
├── Create Deco
├── Create Encased
├── Create: Vibrant Vaults
├── Sophisticated Backpacks Create Integration   (also requires Sophisticated Backpacks)
└── Sophisticated Storage Create Integration     (also requires Sophisticated Storage)

Sophisticated Core
├── Sophisticated Backpacks
└── Sophisticated Storage

Sodium
├── Sodium Extra
└── Iris
    └── Colorwheel

Curios API ─┐
GraveStone ─┼── Gravestone x Curios API Compat
BaguetteLib ┘

Searchables ── Controlling
MezzConfig ─── JEI
```

Everything else (Lithium, FerriteCore, ModernFix, ImmediatelyFast, EntityCulling, Colorwheel Patcher, Xaero's, Jade, AppleSkin, Mouse Tweaks, Carry On, Nature's Compass, GraveStone, Lootr, Farmer's Delight, Easy Villagers) stands alone.

---

## Exceptions

Departures from the pack rules, decided case by case.

| Mod | Rule | Why accepted |
|---|---|---|
| MezzConfig 0.7.1 (beta) | Stable only | Required by JEI and has never had a stable release on Modrinth. |

Not an exception, but worth knowing: Iris's version number reads `1.8.14-beta.1`, yet its author published it on Modrinth as a release.

---

## Under consideration
| Mod | Notes |
|---|---|
| Inventory Essentials | Inventory sorting (middle-click) and moving all stacks of one type. Overlaps Mouse Tweaks on shift-drag. Just Create SMP 2 runs both. Check that middle-click sorting doesn't clash with creative-mode stack copying. |
| Create Stuff 'N Additions | Optional add-on; the preferred choice over Create Jetpack if a jetpack goes in. |
| Create: Numismatics | Optional add-on (currency and shops). |
| Open Parties and Claims | Claims are optional; unsure they are needed. Just Create SMP 2 uses FTB Chunks instead. Xaero's maps list it as an optional integration. |
| Waystones | Optional; pending the travel design. |
| Steam 'n' Rails | No official NeoForge 1.21.1 release. Only an unofficial NeoForge port exists (alpha); Just Create SMP 2 runs a NeoForge listing of it. |
| Reese's Sodium Options | Not discussed yet. Sodium Extra lists it as an optional pairing (a nicer video settings screen). |

### Candidates for categories not yet filled
Each has a NeoForge 1.21.1 build, either checked on its own page or present in ATM10's modlist. None are decided.
- **Terrain and biomes:** Tectonic, Terralith, Regions Unexplored, Oh The Biomes We've Gone.
- **Structures and dungeons:** YUNG's suite (Better Dungeons, Better Mineshafts, Desert Temples, Strongholds, Nether Fortresses, End Island), When Dungeons Arise, Dungeon Crawl, Integrated Dungeons and Structures, Dungeons and Taverns, Repurposed Structures, Towns and Towers, Villages & Pillages, Deeper and Darker.
- **Weapons and gear (no magic):** Better Combat, Simply Swords, Artifacts, Relics.
- **Mobs and bosses:** L_Ender's Cataclysm; Alex's Mobs (unofficial 1.21.1 port only).
- **Ideas from Just Create SMP 2:** FTB Chunks, Vanilla Backport and Copper Age Backport for vanilla catch-up, KubeJS and LootJS for scripting (needed for found-versus-made gear), Simple Voice Chat.

---

## Rejected and turned off
| Mod | Reason |
|---|---|
| Continuity | The NeoForge build depends on Sinytra Connector and Fabric API, which breaks the pure-NeoForge rule. |
| Embeddium, Oculus | Stale, no 1.21.1 build. |
| EMI | Turned off. It added little over JEI, its UI scales a bit too large, and its recipe tree handles Create poorly (for example the dough to slime ball path). |
| Ars Nouveau, Ars Creo | No magic system in this pack. |
