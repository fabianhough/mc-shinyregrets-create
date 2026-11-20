# Mod Choices

Why each mod is in the pack. Minecraft 1.21.1, NeoForge 21.1.x. Last updated 2026-11-20.

## Principles
- **Pure NeoForge.** No Sinytra Connector or Fabric API layers (Continuity was rejected for this reason). Mods that bundle Forgified Fabric API modules internally (Sodium) are fine.
- **Why NeoForge 1.21.1.** Create's active development branch is `mc1.21.1/dev`; its 1.20.1 branch has been quiet since Nov 2025, and Create Aeronautics is NeoForge 1.21.1 only. Fabric 1.20.1 was evaluated and rejected: Create Fabric is a community port that trails (6.0.8.1 vs 6.0.10), and several add-ons have no Fabric build.
- **Vanilla++.** Vanilla plus performance, visual and UI mods and cohesive vanilla-style additions, with Create as the central content mod.
- **Community-proven and polished.** Prefer mods with a long track record that work cleanly together.
- **No magic system.** Ars Nouveau and Ars Creo were dropped (decided 2026-11-20).
- **Aeronautics is a separate integration effort**, not part of this pack's current build.

Version numbers aren't pinned yet.

---

## Chosen mods (38)

### Performance and rendering
| Mod | Why |
|---|---|
| Sodium | Core rendering engine. Chunk loading is noticeably smoother when flying fast. Create lists Sodium ≥ 0.6.9 as its optional floor. |
| Sodium Extra | Rendering options, including a built-in FPS counter. |
| Iris | Shader support. About 120 FPS average with a shader active. |
| Lithium | Game logic and tick performance. Create lists ≥ 0.14.7 as its optional floor. |
| FerriteCore | Memory usage. |
| ModernFix | Load time and memory. |
| ImmediatelyFast | GUI and text rendering. |
| EntityCulling | Entity rendering. **Under retest:** earlier it dropped FPS from about 120 to about 100 (about 80 looking at a sheep) with shaders on. |
| Colorwheel | Bridges Create's Flywheel renderer and Iris shaders. Works with Complementary and Bliss. Do not combine with Iris Flywheel Compat. |
| Colorwheel Patcher | Shader-pack patches for Colorwheel. |

Shader packs are optional and chosen per player: Complementary Reimagined, Complementary Unbound, Bliss. Bliss works with Create via Colorwheel and Colorwheel Patcher.

### Maps, recipes and information
| Mod | Why |
|---|---|
| Xaero's Minimap | Minimap. |
| Xaero's World Map | World map. Create requires ≥ 1.40.2 for its built-in train-map overlay. |
| JEI | The sole recipe viewer. Create ships a JEI plugin. EMI was tried and turned off (see Rejected and turned off). |
| Jade | Block and entity info on look-at. |
| AppleSkin | Hunger and saturation display. |
| Controlling | Keybind search. |
| Mouse Tweaks | Inventory handling (drag, scroll and click transfers). |

### Gameplay and quality of life (vanilla++)
| Mod | Why |
|---|---|
| Carry On | Enabler for moving animals and relocating mob spawners. |
| Nature's Compass | Biome finder. Removes the frustration of hunting for a specific biome; fun over friction. |
| Sophisticated Backpacks | Backpacks that scale well, a clean answer to inventory pressure. |
| Sophisticated Storage | Storage with upgrades. Briefly cut because backpacks already cover a lot, then kept for players who want the customization. |
| GraveStone Mod | Death and graves. Chosen over Epitaphs: it integrates well with Xaero's and is less obnoxious than Epitaphs was on the ATM10 Aeronautics server. |
| Gravestone x Curios API Compat | Grave handling for Curios slots, so worn backpacks come back. |
| Curios API | Accessory slots. Crucial to the setup: GraveStone's Curios compat depends on it. Promoted from a dependency to a chosen mod. |
| Lootr | Per-player loot chests, so every player gets their own loot from each chest. |
| Farmer's Delight | Food and cooking. The first content mod in the pack, in keeping with the vanilla feel. |
| Easy Villagers | Villagers as items. |

### Create: core and integrations
| Mod | Why |
|---|---|
| Create | The central content mod. |
| Sophisticated Backpacks Create Integration | Sophisticated and Create interoperate. |
| Sophisticated Storage Create Integration | Same, for Sophisticated Storage. |
| Create: Enchantment Industry | Create-path enchanting and XP. |
| Create Slice & Dice | Automates Farmer's Delight with Create. |
| Create Cobblestone | Cobblestone generation. |

### Create: decor and building
| Mod | Why |
|---|---|
| Create: Design n' Decor | Industrial decor blocks. The main decor mod: it covers what Create Deco and Vibrant Vaults add (including shipping-container vaults) and more. |
| Copycats+ | Shaped copycat blocks (still testing). |
| Create Deco | Added by choice. Earlier saw an x-ray glitch when breaking a middle block of a shipping container. Overlaps Design n' Decor. |
| Create Encased | Added by choice (extra Create casings and components). |
| Create: Vibrant Vaults | Added by choice. Overlaps Design n' Decor's shipping-container vaults. |

---

## Dependencies (installed automatically, not chosen)
| Mod | Pulled in by |
|---|---|
| Flywheel, Ponder, Registrate | Bundled inside the Create jar |
| Forgified Fabric API modules | Bundled inside Sodium |
| MezzConfig | Bundled with JEI |
| Sophisticated Core | Sophisticated Backpacks and Storage |
| Create: Dragons Plus | Required by Enchantment Industry |
| Searchables | Most likely Controlling (not re-verified) |
| Architectury, Kotlin for Forge, BaguetteLib | Not traced to a specific mod |

---

## Under consideration
| Mod | Notes |
|---|---|
| Inventory Essentials | Inventory sorting (middle-click) and moving all stacks of one type. Overlaps Mouse Tweaks on shift-drag. Just Create SMP 2 runs both. Check that middle-click sorting doesn't clash with creative-mode stack copying. |
| Create Stuff 'N Additions | Optional add-on; the preferred choice over Create Jetpack if a jetpack goes in. |
| Create: Numismatics | Optional add-on (currency and shops). |
| Open Parties and Claims | Claims are optional; unsure they are needed. Just Create SMP 2 uses FTB Chunks instead. |
| Waystones | Optional; pending the travel design. |
| Steam 'n' Rails | No official NeoForge 1.21.1 release. Only an unofficial NeoForge port exists (alpha); Just Create SMP 2 runs a NeoForge listing of it. |

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
