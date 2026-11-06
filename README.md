# Tabletop Map Workshop

Paint a local tabletop terrain map, flood-fill regions, place labels, undo, and export editable or flattened maps.

[![Build and verify](https://github.com/netcodermike/tabletop-map-workshop/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/tabletop-map-workshop/actions/workflows/verify.yml)

**Language:** TypeScript · **Platform:** Windows, macOS, Linux browser · **App type:** Browser tile-map editor for tabletop games

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- 30×20 terrain grid
- Paint and bounded flood fill
- Named tokens and removal
- Browser save, JSON, and PNG

## Requirements

Node.js 24.12+ and a modern browser; no npm dependencies.

## Quick start

```sh
git clone https://github.com/netcodermike/tabletop-map-workshop.git
cd tabletop-map-workshop
node server.ts
# Open http://127.0.0.1:3030
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Paint a wall barrier, flood-fill one side with water, add/remove a token, undo, save, and export/import JSON. Export PNG and inspect tile/token placement.

## Architecture, configuration, and data

core.ts validates a fixed version-1 map with four terrain IDs and up to 100 bounded token records. Flood fill returns an immutable validated copy. The canvas UI paints cells, stores 30 undo states, and exports PNG/JSON. One map is saved per browser origin; no autosave. server.ts exposes loopback port 3030 HTML and a stripped module. Tests check fill barriers, immutability, serialization, and invalid coordinates.

## Verification

Build with the quick-start command where needed, then run:

```sh
node --test test.ts
```

Manual acceptance: Paint a wall barrier, flood-fill one side with water, add/remove a token, undo, save, and export/import JSON. Export PNG and inspect tile/token placement. Also test malformed inputs and an unwritable output destination.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

No collaboration, fog of war, game rules, image tiles, token dragging, layer system, scale units, zoom, or hosting. Flood fill uses four-neighbor terrain connectivity. Tokens can overlap and labels can extend beyond cells. PNG is flattened; JSON retains data. Drawing requires pointer input.

## Troubleshooting

Use the exact platform/toolchain above. Preserve originals and use synthetic fixtures first. Errors are displayed in the UI or stderr. A headless machine can run the model tests but cannot verify native GUI/audio behavior. Output paths are chosen explicitly; keep backups of important data.

## Source map

- `core.ts`
- `package.json`
- `server.ts`
- `test.ts`
- `public/index.html`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
