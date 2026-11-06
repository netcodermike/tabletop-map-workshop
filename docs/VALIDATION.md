# Validation

Authoring date: November 6, 2026. Host: Windows. Target: Windows, macOS, Linux browser.

## Local result

Target-platform source CI is recorded after publication. This host has Python, Node.js, and .NET; other native toolchains are verified through CI. No unobserved GUI/device behavior is claimed.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `ubuntu-latest`:

```sh
node --test test.ts
node --check server.ts
```

## Manual acceptance

Paint a wall barrier, flood-fill one side with water, add/remove a token, undo, save, and export/import JSON. Export PNG and inspect tile/token placement. Also test malformed inputs and an unwritable output destination.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.
