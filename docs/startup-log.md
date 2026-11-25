# Server Startup Log

What happens when each pack version is stood up on the server (itzg, see [`deploy/docker-compose.yml`](../deploy/docker-compose.yml)). One entry per version, newest first. Each entry records what worked, which errors are harmless noise, and anything worth acting on.

**How to capture a log** (on the server, from the compose directory):

```sh
docker compose logs --no-color mc > mc-startup.log
docker compose logs --no-color backups > backups-startup.log
```

Summarize the logs here; don't commit raw logs (they can contain player names and IP addresses).

---

## 0.6.0 (2026-11-25)

Upgrade from 0.5.0, on a new server machine (data copied over with rsync). Modpack resolved as `shinyregrets-create 0.6.0`.

### Working as intended
- **Upgrade:** itzg downloaded only the 9 new files (RightClickHarvest, JamLib, TrashSlot, Accelerated Decay, Waystones, Supplementaries, Amendments, Comforts, Moonlight Lib) and kept the rest. NeoForge unchanged at 21.1.267; Java 21.0.13 (Eclipse Adoptium), image tag `java21`.
- **Startup:** `Done (0.943s)!` (existing world, spawn already generated); ModernFix reports 15.9 s total server load.
- **New machine:** RCON secret, whitelist, Aikar's flags and the 8G heap all applied (`[init]` lines).
- **Backups:** backup on startup succeeded (`world-<timestamp>.tar.zst`), followed by pruning; then `No players online, waiting 5m...`.
- **Chat notices:** `[Rcon] Backing up the world...` and `[Rcon] Backup complete.` both appeared.
- **New mods:** no errors from any of them.

### Harmless noise
Same as 0.5.0 (see below): 538 loot-table errors (Steam 'n' Rails 276, Design n' Decor 256, Create: Enchantment Industry 6), about 125 mixin warnings, the `AbstractClientPlayer` dist error, the Create Dragons Plus data-map warnings and the Create Cobblestone config warning. New in 0.6.0:

| What | Why it's harmless |
|---|---|
| `[Lithium] Mod 'supplementaries' attempted to override option 'mixin' with an invalid value, ignoring` (also for `mixins` and `block`) | Supplementaries ships Lithium config overrides that this Lithium version doesn't recognize; Lithium ignores them. |
| Refmap warnings for Comforts, TrashSlot and Waystones (`Reference map ... could not be read`) | Normal outside a development environment. |
| Supplementaries: `Dye color white produced diffuse color -1 (white), this should never happen` | A cosmetic self-check in the mod. |

The two Simply Swords compat-recipe errors from 0.5.0 didn't appear this time.

### Worth noting
- **Create Deco's `createdeco:placard` recipe** still fails to load (same as 0.5.0).
- **Not visible in the log:** whether `/data/config/rightclickharvest.json5` has `requireHoe: true`. Check the file on the server.

---

## 0.5.0 (2026-11-21)

First stand-up of the pack on the server. Modpack resolved from Modrinth (`shinyregrets-create 0.5.0`).

### Working as intended
- **Install:** 52 of 68 mods downloaded; the 16 client-only mods were skipped. NeoForge 21.1.267 installed; running on Java 21 (Eclipse Adoptium), image tag `java21`.
- **Startup:** `Done (8.151s)!`; ModernFix reports 24.1 s total server load.
- **RCON secret:** the backup container connected on the first attempt, with no permission errors reading `RCON_PASSWORD_FILE`.
- **Backups:** backup on startup succeeded (`world-<timestamp>.tar.zst`), followed by pruning (14 days). Then `No players online, waiting 5m...`, so `PAUSE_IF_NO_PLAYERS` is working.
- **Chat notices:** `[Rcon] Backing up the world...` and `[Rcon] Backup complete.` both appeared. The `[Not Secure]` tag is because RCON messages aren't signed by a player; it's cosmetic.
- **Join test:** a player logged in from Prism, moved around, and ran a manual backup (`docker compose exec backups backup now`); the chat notices showed in game and no errors appeared in the `mc` log.

### Harmless noise
| What | Count | Why it's harmless |
|---|---|---|
| `LootDataType` "Couldn't parse element ... Unknown registry key" | 538 | Loot tables for compat blocks of mods we don't have. Steam 'n' Rails 276 (tracks for BYG, TerraFirmaCraft, Biomes O' Plenty, Twilight Forest, Quark and others), Design n' Decor 256, Create: Enchantment Industry 6. |
| `RecipeManager` errors for `simplyswords:` recipes | 2 | Compat recipes for Eldritch End and Mythic Metals, which aren't installed. |
| `mixin` warnings | about 120 | Client-only classes that don't exist on a dedicated server, plus ModernFix skipping methods Lithium already patches. |
| `RuntimeDistCleaner` error for `AbstractClientPlayer` | 1 | A client class requested on the server; skipped. |
| Create: Enchantment Industry config "not correct. Correcting" | 1 | One key reset to its default on the first run. |
| Create Dragons Plus `DataMapLoader` warnings, Create Cobblestone config warning | a few | Data and config notices; no effect. |
| `LanServerPinger: Network is unreachable` | 1 | LAN discovery inside a container. |

### Worth noting
- **Create Deco: the `createdeco:placard` recipe fails to load** (a recipe format error in the mod). Placards may not be craftable. A mod bug that affects only that block.
- **Steam 'n' Rails reports `v1.6.13-alpha` internally,** although the NeoForge port publishes it on Modrinth as a release (0.2.1). It's consistent with it being an unofficial port (see [Caveats](caveats.md#steam-n-rails-is-a-community-neoforge-port)).
- **The shader packs are downloaded to the server too.** packwiz marks them for both sides (see [Caveats](caveats.md#some-modrinth-environment-values-are-unknown-to-packwiz)). Unused and harmless.
