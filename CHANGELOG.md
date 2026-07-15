# Changelog

All notable changes to this project are documented here.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
### Changed
### Deprecated
### Removed
### Fixed
### Security

## [1.0.0] - 2026-07-15

### Added
- Spawn-gear loadout preset (`custom/loadout.json`, adopted from Chernarus), wired into `cfggameplay.json` via `spawnGearPresetFiles`.

### Changed
- **Central economy loot reduced ~50%:** halved `nominal` and `min` for 1907 types in `db/types.xml` (ceil rounding, so `1` stays `1`), excluding `deloot="1"` and `Underground`-usage types.
- **Infected density raised:** every positive dynamic infected count (`dmin`/`dmax`) in `env/zombie_territories.xml` incremented by 1.
- `db/globals.xml`: adopted Chernarus idle-mode and login/hop/penalty timer values.
- `db/messages.xml`: adopted Chernarus new-player onboarding message rotation, rebranded "Chernarus" → "Livonia".
- `cfggameplay.json`: adopted Chernarus gameplay config (spawn loadout, base-building placement checks disabled, respawn-in-unconsciousness and personal-light tweaks); environment temperatures set to flat `-4`/`2` year-round.

## [0.1.0] - 2026-07-15

### Added
- Vanilla DayZ "Road to Badlands" mission files for the Livonia (Enoch) map as the project baseline — economy core (`cfgeconomycore.xml`), spawnable types, map group definitions/clusters/positions, environment territories (`env/`), central economy tables (`db/`), weather, effect areas, player spawn points, gameplay config, and `init.c`, all unmodified from the vanilla mission.

## Workflow template tooling (pre-project)

_These entries predate the DayZ mission and document the Claude Code workflow template that scaffolds this repo. They were originally labeled `1.0.1` / `1.0.0`; relabeled here so the mission's own SemVer line (starting at `0.1.0`) is unambiguous. No git tags were ever cut for them._

- Solo maintainer mode: back-merge PRs (`main`→`develop`) are no longer blocked by the contribution CHANGELOG/CLAUDE.md gate. The solo `gh-pr-create` check now parses `--head` and exempts `head == productionBranch`, mirroring the merge handler.
- `soloMaintainer` mode: an opt-in `.claude/workflow.json` flag that enables a `solo` guard role holding the union of contributor + maintainer permissions, so one person can run the full workflow (feature work, contribution merge, release, back-merge) from a single clone without swapping git remotes. Protected branches stay PR-only and contribution merges into `develop` still require `--squash` + a posted review (a `COMMENTED` review counts). Off by default.
