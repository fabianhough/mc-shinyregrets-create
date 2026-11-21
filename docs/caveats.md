# Caveats and Known Issues

Quirks, conflicts and things to watch for that we've found while building the pack. Each entry says what we saw, what we did about it (often nothing), and what to check if something breaks.

Working policy: we trust packwiz's dependency handling. If packwiz adds a file because Modrinth lists it as required, it stays unless it breaks something in testing.

---

## Tooling (packwiz)

### packwiz picks the newest version regardless of release channel
- **Seen:** 2026-11-21, while adding JEI and Create: Enchantment Industry.
- **Detail:** `packwiz modrinth add` (and `packwiz update`) choose the most recently published version, betas included. Confirmed in packwiz's source (`modrinth/modrinth.go`, `getLatestVersion`).
- **Action:** stable versions are pinned with `--version-id` when adding. **`packwiz update --all` would bump JEI and Enchantment Industry to betas**, so check channels after any update.

### Some Modrinth environment values are unknown to packwiz
- **Seen:** 2026-11-21.
- **Detail:** Xaero's Minimap and World Map, CreativeCore and Sound Physics Remastered publish `client_only_server_optional`, Tectonic publishes `server_only_client_optional`, and the shader packs publish `unknown`. packwiz doesn't recognise these and marks them `both` (client and server). FerriteCore's and Balm's `client_or_server` also becomes `both`, with a warning.
- **Action:** none. Harmless for a single client-and-server pack.

---

## Gameplay and configuration

### B key opens both the backpack and a Xaero's waypoint screen
- **Seen:** 2026-11-21, testing v0.2.0.
- **Detail:** Sophisticated Backpacks' open-backpack key and one of Xaero's Minimap waypoint keys both default to B.
- **Decision:** B opens the backpack only; the Xaero's waypoint key is **unbound**.
- **Status:** Default Options added in v0.3.0. The keybind defaults file still needs creating: in a v0.3.0 instance, unbind the Xaero's key, run `/defaultoptions saveKeys` in a world, and commit the resulting files under `config/defaultoptions/`. Use `saveKeys`, not `saveAll`, so personal graphics settings aren't shipped.

### Worldgen mods are permanent per world
- **Seen:** 2026-11-21, adding Tectonic and Terralith.
- **Detail:** per Terralith's Modrinth page, it can't be removed from an existing world and shouldn't be added to one; start a new world. Tectonic changes terrain generation the same way. Switching between the mod and datapack versions of Terralith can also damage a world.
- **Action:** treat these two as fixed once the server world is generated. Any future biome or worldgen mod should be decided before the server's world is created.

### Terralith replaces vanilla granite, diorite and andesite blobs
- **Seen:** 2026-11-21, from Terralith's Modrinth page.
- **Detail:** Terralith moves those stones into dedicated cave biomes instead of scattering blobs underground. **Andesite matters for Create** (andesite alloy is early-game core), so it may be harder to find early on.
- **Action:** none yet; watch for it in testing. If it's a problem, Terralith's config has a "Vanilla Stone Generation" option (off by default), or its official add-on Terralith: ReStoned restores the blobs.

---

## Duplicate and bundled files

### JEI bundles MezzConfig, and Modrinth also lists it as a separate dependency
- **Seen:** 2026-11-21.
- **Detail:** JEI 19.64.0.455 ships MezzConfig 0.6.6 inside its jar. Its Modrinth listing also marks MezzConfig as required, so packwiz adds the standalone MezzConfig 0.7.1 (beta). NeoForge loads the newest copy present, so 0.7.1 is used, not the copy JEI was built with. MezzConfig has never had a stable release, so it's one of the pack's beta exceptions (logged under [Exceptions](mod-choices.md#exceptions)).
- **Earlier testing:** the pre-packwiz Prism setup ran JEI 19.70.0.467 (a beta) with MezzConfig 0.6.9. The pack now uses stable JEI 19.64.0.455, so JEI behaviour may differ slightly from that testing.
- **Action:** kept, per the working policy. If JEI's config screen misbehaves, try removing the standalone MezzConfig (`packwiz remove mezzconfig`) so JEI's bundled copy is used.

### Freecam bundles Cloth Config where NeoForge doesn't look
- **Seen:** 2026-11-21.
- **Detail:** Freecam's Modrinth listing marks Cloth Config as embedded. The copy (15.0.128) sits in `META-INF/jars/`, Fabric's location for bundled mods; NeoForge loads bundled mods from `META-INF/jarjar/`. Freecam's jar doesn't declare Cloth Config as required.
- **Action:** none. The standalone Cloth Config (pulled in by BetterF3 and Better Combat) is present anyway. If those two are ever removed and Freecam's settings screen breaks, this is why.

---

## Unofficial ports

### Steam 'n' Rails is a community NeoForge port
- **Seen:** 2026-11-21.
- **Detail:** the official Steam 'n' Rails (by IThundxr) has no 1.21.1 build. The pack uses "Steam 'n' Rails Neoforge" (`create-steam-n-rails-1.21.1`, by PoppyBlossom), a separate Modrinth project. Just Create SMP 2 runs it without problems. Pinned to stable 0.2.1; the 0.3.0 line is beta.
- **Action:** none. Worth watching for an official 1.21.1 release, which would be the one to switch to. Bug reports go to the port, not the official project.

---

## Metadata mismatches (Modrinth vs. the jar)

Modrinth's dependency list (what packwiz uses) doesn't always match what the jar itself declares in `META-INF/neoforge.mods.toml` (what NeoForge enforces at startup). None of these block anything; they explain why a file is or isn't present.

| Mod | Modrinth says | Jar says |
|---|---|---|
| Create Cobblestone | Requires Architectury API | No Architectury requirement |
| Iris | Requires Sodium | No Sodium requirement |
| Create Deco | No dependencies | Requires Create |
| Create: Dragons Plus | (pulled in as a dependency) | Requires Create |
| Create: Vibrant Vaults | Requires Create, pinned to 6.0.2 | Accepts the pack's Create 6.0.10 |
| Create: Liquid Fuel | No dependencies | Requires Create |
| Create Stuff 'N Additions | No dependencies | No dependencies (still needs Create to do anything) |

---

## Unverified

### Minecraft version range appears to exclude 1.21.1
- **Seen:** 2026-11-21, during the jar requirement check.
- **Detail:** Iris, JEI and Nature's Compass declare `versionRange = "[1.21,1.21.1)"` for Minecraft, which read literally excludes 1.21.1. All three are 1.21.1 builds with very high download counts, so they very likely load anyway. Why is unknown.
- **Action:** none. If the game refuses to start with a version error, look here first.
