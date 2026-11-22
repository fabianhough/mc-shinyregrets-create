# mc-shinyregrets-create
A modded Minecraft modpack designed to primarily feature the Create mod. 

## Purpose

Get a small group of friends comfortable with Minecraft again, with modded Minecraft, and especially with Create. The pack is a polished vanilla++ base with Create as the depth. Adventure and exploration content (structures, dungeons, new mobs) is intentionally deferred to a later phase, once the group is at an advanced level. See the principles in [Mod Choices](docs/mod-choices.md#principles).

## Pack targets

- Minecraft: 1.21.1
- Loader: NeoForge
- Distribution: `.mrpack` exports, published and managed on Modrinth

## Deployment

- **Server:** Docker, using [`itzg/minecraft-server`](https://hub.docker.com/r/itzg/minecraft-server), running the same `.mrpack` players install (one pack for client and server).
- **Backups:** the [`itzg/mc-backup`](https://hub.docker.com/r/itzg/mc-backup) sidecar container alongside the server.
- **Sample compose file:** [`deploy/docker-compose.yml`](deploy/docker-compose.yml). Replace the `<PLACEHOLDERS>` and create `secrets/rcon_password.txt` next to it before the first start (see the comments at the top of the file).

## Documentation

- [Mod Choices](docs/mod-choices.md): why each mod is in the pack, what's approved for later, and what's under consideration. Kept up to date as the pack changes.
- [Caveats and Known Issues](docs/caveats.md): quirks, duplicate files, metadata mismatches and other things to watch for, logged as we find them.
- [Server Startup Log](docs/startup-log.md): what happens when each pack version is stood up on the server: what worked, harmless log noise, and issues worth acting on.

## Rules

Working rules for this pack (for humans and agents alike). Added as they are agreed on.

1. **Modrinth-only sourcing.** Every mod must be available on Modrinth and added via `packwiz modrinth add`. No CurseForge, GitHub, or direct-URL sources.
2. **Stable releases only.** Use Modrinth versions marked "release", not beta or alpha. packwiz picks the newest version regardless of channel, so add mods with an explicit `--version-id` when the newest is a beta. Exceptions are decided case by case and logged in [Mod Choices](docs/mod-choices.md#exceptions).

## Tooling

### packwiz

Managed with [packwiz](https://github.com/packwiz/packwiz). packwiz has no tagged releases, so it is pinned to a commit:

- Pinned commit: `170b22d78595` (2026-10-14)
- Requires Go 1.23+ (per packwiz's `go.mod`)

Install:

```sh
go install github.com/packwiz/packwiz@170b22d78595
```

The binary lands in `$(go env GOPATH)/bin` (usually `~/go/bin`); make sure that is on your `PATH`. Bump the pin deliberately and update this section when doing so.
