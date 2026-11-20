# mc-shinyregrets-create
A modded Minecraft modpack designed to primarily feature the Create mod. 

## Pack targets

- Minecraft: 1.21.1
- Loader: NeoForge
- Distribution: `.mrpack` exports, published and managed on Modrinth

## Rules

Working rules for this pack (for humans and agents alike). Added as they are agreed on.

1. **Modrinth-only sourcing.** Every mod must be available on Modrinth and added via `packwiz modrinth add`. No CurseForge, GitHub, or direct-URL sources.

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
