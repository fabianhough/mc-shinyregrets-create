# Mod Choices

Why each mod is in the pack. Minecraft 1.21.1, NeoForge 21.1.267. Last updated 2026-11-21.

## Principles
- **Pure NeoForge.** No Sinytra Connector or Fabric API layers (Continuity was rejected for this reason). Mods that bundle Forgified Fabric API modules internally (Sodium) are fine.
- **Why NeoForge 1.21.1.** Create's active development branch is `mc1.21.1/dev`; its 1.20.1 branch has been quiet since Nov 2025, and Create Aeronautics is NeoForge 1.21.1 only. Fabric 1.20.1 was evaluated and rejected: Create Fabric is a community port that trails (6.0.8.1 vs 6.0.10), and several add-ons have no Fabric build.
- **Vanilla++.** Vanilla plus performance, visual and UI mods and cohesive vanilla-style additions, with Create as the central content mod. "Cohesive" means balanced and in keeping with vanilla, not power-creep: Better Combat and Simply Swords fit; something like Apotheosis, which makes gear and progression overpowered, does not.
- **Community-proven and polished.** Prefer mods with a long track record that work cleanly together.
- **Onboarding first; adventure later.** The pack's job is to get friends comfortable with modded Minecraft through Create, which provides enough depth on its own. Adventure and exploration content (structures, dungeons, new mobs and bosses) is deliberately deferred to a later phase, once the group is at an advanced level. An empty structures category is intentional, not a gap (decided 2026-11-21).
- **No magic system.** Ars Nouveau and Ars Creo were dropped (decided 2026-11-20).
- **Aeronautics is a separate integration effort**, not part of this pack's current build.
- **Modrinth only, stable releases only.** See the Rules in the [README](../README.md). Exceptions are listed under [Exceptions](#exceptions).
- **One pack for everyone.** The pack bundles everything (including shaders) so players who aren't familiar with mods get a complete setup from a single Modrinth install. The same `.mrpack` is used for the server.

Exact versions are pinned in each mod's metadata file under `mods/` and `shaderpacks/` (`*.pw.toml`), not in this doc.

**Side** is packwiz's marking from Modrinth's environment data: `client` means client-only (a server install skips it); `both` means client and server. It's recorded for reference; the pack is built as a single client-and-server monolith.

---

## Chosen mods (54)

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
| [Clumps](https://modrinth.com/mod/clumps) | both | Merges nearby XP orbs into one entity, cutting lag around XP farms (Create: Enchantment Industry makes a lot of XP). |

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
| [JEI](https://modrinth.com/mod/jei) | both | The sole recipe viewer. Create ships a JEI plugin. EMI was tried and turned off: it added little over JEI, its UI scales a bit too large, and its recipe tree handles Create poorly. |
| [Jade](https://modrinth.com/mod/jade) | both | Block and entity info on look-at. |
| [AppleSkin](https://modrinth.com/mod/appleskin) | both | Hunger and saturation display. |
| [Controlling](https://modrinth.com/mod/controlling) | client | Keybind search. |
| [Default Options](https://modrinth.com/mod/default-options) | client | Lets the pack ship default keybinds (from `config/defaultoptions/`) without overwriting players' own settings on updates. Added to resolve the B-key conflict between Sophisticated Backpacks and Xaero's Minimap (see [Caveats](caveats.md#b-key-opens-both-the-backpack-and-a-xaeros-waypoint-screen)). |
| [Mouse Tweaks](https://modrinth.com/mod/mouse-tweaks) | client | Inventory handling (drag, scroll and click transfers). |

### Stability and diagnostics
| Mod | Side | Why |
|---|---|---|
| [Neruina](https://modrinth.com/mod/neruina) | both | When an entity, block entity or item crashes while ticking, Neruina suspends it instead of letting it crash and brick the world. A safety net for a server full of Create contraptions. Suspended things are announced in chat with options to teleport to them, retry or kill them. |
| [spark](https://modrinth.com/mod/spark) | both | Performance profiler (`/spark profiler`, `/spark health`). Lightweight enough to leave installed; the tool for diagnosing lag on the server or a client. |

### Client polish and immersion
| Mod | Side | Why |
|---|---|---|
| [Freecam](https://modrinth.com/mod/freecam) | client | Detached camera for inspecting builds and contraptions. Added on purpose; it can see through walls, which is accepted for a friends server. |
| [Ok Zoomer](https://modrinth.com/mod/ok-zoomer) | client | Zoom key. |
| [AmbientSounds](https://modrinth.com/mod/ambientsounds) | client | Biome and environment ambience. |
| [Sound Physics Remastered](https://modrinth.com/mod/sound-physics-remastered) | both | Reverb and sound occlusion. Beta-only on NeoForge 1.21.1; accepted as an exception given its track record (see [Exceptions](#exceptions)). |
| [BetterF3](https://modrinth.com/mod/betterf3) | client | Cleaner, configurable F3 debug screen. |
| [3D Skin Layers](https://modrinth.com/mod/3dskinlayers) | client | Renders the outer skin layer in 3D. |

### Combat
| Mod | Side | Why |
|---|---|---|
| [Better Combat](https://modrinth.com/mod/better-combat) | both | Weapon-specific attack animations and combos. Changes how melee feels without making gear overpowered, so it stays vanilla++. |
| [Simply Swords](https://modrinth.com/mod/simply-swords) | both | More weapon types and unique loot weapons. Integrates with Better Combat. |

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
| [Chimes](https://modrinth.com/mod/chimes) | both | Wind chimes. Added because it's cute. |

### Create: core and integrations
| Mod | Side | Why |
|---|---|---|
| [Create](https://modrinth.com/mod/create) | both | The central content mod. |
| [Sophisticated Backpacks Create Integration](https://modrinth.com/mod/sophisticated-backpacks-create-integration) | both | Sophisticated and Create interoperate. |
| [Sophisticated Storage Create Integration](https://modrinth.com/mod/sophisticated-storage-create-integration) | both | Same, for Sophisticated Storage. |
| [Create: Enchantment Industry](https://modrinth.com/mod/create-enchantment-industry) | both | Create-path enchanting and XP. Pinned to the 2.4.x stable line; 2.5.x has been beta-only since Sept 2026. |
| [Create Slice & Dice](https://modrinth.com/mod/slice-and-dice) | both | Automates Farmer's Delight with Create. |
| [Create Cobblestone](https://modrinth.com/mod/create-cobblestone) | both | Cobblestone generation. |
| [Create Stuff 'N Additions](https://modrinth.com/mod/create-stuff-additions) | both | Create-style gear and items; the preferred choice over Create Jetpack for a jetpack. |
| [Steam 'n' Rails (NeoForge port)](https://modrinth.com/mod/create-steam-n-rails-1.21.1) | both | More train parts and track types. The official Steam 'n' Rails has no 1.21.1 build; this is the community NeoForge port, which Just Create SMP 2 runs without problems. Pinned to the stable 0.2.1; 0.3.0 is beta. |
| [Create: Liquid Fuel](https://modrinth.com/mod/create-liquid-fuel) | both | Liquid fuels for blaze burners. Used by Just Create SMP 2 without problems. |

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
| [Kotlin for Forge](https://modrinth.com/mod/kotlin-for-forge) | both | Create Slice & Dice, Fzzy Config |
| [Architectury API](https://modrinth.com/mod/architectury-api) | both | Simply Swords, Simply Tooltips; also Create Cobblestone (listed on Modrinth; that jar doesn't declare it) |
| [BaguetteLib](https://modrinth.com/mod/baguettelib) | both | Gravestone x Curios API Compat |
| [Searchables](https://modrinth.com/mod/searchables) | client | Controlling |
| [MezzConfig](https://modrinth.com/mod/mezzconfig) | both | JEI (beta-only; see [Exceptions](#exceptions)) |
| [Cloth Config API](https://modrinth.com/mod/cloth-config) | both | BetterF3, Better Combat |
| [playerAnimator](https://modrinth.com/mod/playeranimator) | both | Better Combat (beta-only; see [Exceptions](#exceptions)) |
| [CreativeCore](https://modrinth.com/mod/creativecore) | both | AmbientSounds |
| [Fzzy Config](https://modrinth.com/mod/fzzy-config) | both | Simply Swords, Simply Tooltips |
| [Simply Tooltips](https://modrinth.com/mod/simply-tooltips) | client | Simply Swords |
| [Balm](https://modrinth.com/mod/balm) | both | Default Options |
| [Configurable](https://modrinth.com/mod/configurable) | both | Neruina |

Bundled inside other jars (no separate file):
- **Flywheel, Ponder, Registrate:** inside Create.
- **Forgified Fabric API modules:** inside Sodium.
- **MezzConfig 0.6.6:** inside JEI, in addition to the standalone MezzConfig above. NeoForge loads the newest copy present.
- **XaeroLib:** inside both Xaero's Minimap and Xaero's World Map.
- **Wrench Wrapper:** inside Ok Zoomer.
- **Kuma API:** inside Balm.
- **Cloth Config 15.0.128:** inside Freecam, in a folder NeoForge doesn't load bundled mods from. The standalone Cloth Config above covers it.

### Dependency tree

Required dependencies only. A mod's children require it.

```
Create  (bundles Flywheel, Ponder, Registrate)
├── Create: Dragons Plus
│   └── Create: Enchantment Industry      (also requires Create)
├── Create Slice & Dice                   (also requires Kotlin for Forge)
├── Create Cobblestone                    (also requires Architectury API)
├── Steam 'n' Rails (NeoForge port)
├── Create: Liquid Fuel
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

Kotlin for Forge
└── Fzzy Config
    ├── Simply Tooltips                   (also requires Architectury API)
    │   └── Simply Swords                 (also requires Fzzy Config, Architectury API)
    └── Simply Swords

Cloth Config ──────┬── BetterF3
playerAnimator ────┴── Better Combat      (requires both)

Balm ────────── Default Options
Configurable ── Neruina
CreativeCore ── AmbientSounds
Searchables ─── Controlling
MezzConfig ──── JEI
```

Everything else (Lithium, FerriteCore, ModernFix, ImmediatelyFast, EntityCulling, Colorwheel Patcher, Clumps, Xaero's, Jade, AppleSkin, Mouse Tweaks, Freecam, Ok Zoomer, Sound Physics Remastered, 3D Skin Layers, spark, Carry On, Nature's Compass, GraveStone, Lootr, Farmer's Delight, Easy Villagers, Chimes) stands alone. Create Stuff 'N Additions declares no dependency on Create at all, on Modrinth or in its jar; it works because Create is in the pack.

---

## Exceptions

Departures from the pack rules, decided case by case.

| Mod | Rule | Why accepted |
|---|---|---|
| MezzConfig 0.7.1 (beta) | Stable only | Required by JEI and has never had a stable release on Modrinth. See [Caveats](caveats.md#jei-bundles-mezzconfig-and-modrinth-also-lists-it-as-a-separate-dependency). |
| playerAnimator 2.0.4 (beta) | Stable only | Required by Better Combat; no stable NeoForge 1.21.1 build exists (decided 2026-11-21). |
| Sound Physics Remastered 1.5.2 (beta) | Stable only | No stable NeoForge 1.21.1 build. Accepted given its track record (57M downloads); client-side sound only, easy to remove (decided 2026-11-21). |

Not exceptions, but worth knowing: Iris (`1.8.14-beta.1`) and Ok Zoomer (`10.0.0-beta.13`) have "beta" in their version numbers, yet their authors published them on Modrinth as releases.

---

## Under consideration
Nothing right now.

### Approved, add when needed
Already vetted as OK to add; not in the pack yet only because they aren't needed now (the servers will be small). If a need comes up, add them to the pack for everyone, without re-litigating whether they belong (decided 2026-11-21).

| Mod | Notes |
|---|---|
| Open Parties and Claims | Claims aren't needed on a small server. Just Create SMP 2 uses FTB Chunks instead. Xaero's maps list it as an optional integration. |
| Waystones | Pending the travel design. |
| Reese's Sodium Options | A nicer video settings screen for Sodium; Sodium Extra lists it as an optional pairing. |
| [Simple Voice Chat](https://modrinth.com/mod/simple-voice-chat) | Proximity voice chat. Has a stable NeoForge 1.21.1 build (newest is beta; pin the stable one). Pairs with Sound Physics Remastered. Needs a UDP port opened on the server (itzg: expose it in the container). |
| [Chunky](https://modrinth.com/mod/chunky) | Pre-generates chunks so exploring doesn't make the server generate terrain live. Server-side tool; run before players join. Note: structure mods added later won't appear in pre-generated chunks. |

### Candidates for categories not yet filled
Each has a NeoForge 1.21.1 build, either checked on its own page or present in ATM10's modlist. None are decided.
- **Terrain and biomes:** Tectonic, Terralith, Regions Unexplored, Oh The Biomes We've Gone. Tectonic and Terralith were in the pack from 0.3.0 to 0.4.0 and were removed on 2026-11-21: vanilla world generation is enough of a novelty for now. Worldgen mods need deciding before the server's world is created (see [Caveats](caveats.md#worldgen-mods-need-deciding-before-the-server-world)).
- **Structures and dungeons:** YUNG's suite (Better Dungeons, Better Mineshafts, Desert Temples, Strongholds, Nether Fortresses, End Island), When Dungeons Arise, Dungeon Crawl, Integrated Dungeons and Structures, Dungeons and Taverns, Repurposed Structures, Towns and Towers, Villages & Pillages, Deeper and Darker.
- **Weapons and gear (no magic):** Artifacts, Relics.
- **Mobs and bosses:** L_Ender's Cataclysm; Alex's Mobs (unofficial 1.21.1 port only).
- **Ideas from Just Create SMP 2:** FTB Chunks, Vanilla Backport and Copper Age Backport for vanilla catch-up, KubeJS and LootJS for scripting (needed for found-versus-made gear).

