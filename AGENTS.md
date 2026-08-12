# AGENTS.md — mps-os

Operating system init for Debian 13 (trixie): package sources, unattended
upgrades, locale / keyboard / console / timezone, core CLI tooling.

## Galaxy

- **namespace**: `mps`
- **name**: `os`
- **version**: `0.3.1`
- **dependencies**: `mps.base >=0.1.0`, `ansible.posix >=1.0.0`

## Roles

| Role | Description | Complexity |
|---|---|---|
| `mps.os.package_manager` | Configure `/etc/apt/sources.list` (4 pockets × components × deb-src), install base apt packages, configure unattended-upgrades. | 2 |
| `mps.os.system_settings` | Configure locale, keyboard, console (kmscon / plymouth), and timezone / chrony. 4 area-specific sub-areas, each with its own handlers. | 2 |
| `mps.os.system_tools` | Apt-by-category groups (archives, build, core, file-manager, network, transfer, statistics). Each gated by a `<group>_enable_<area>` toggle. | 1 |

## Defaults (system-wide)

- Every role depends on `mps.base.assert_debian13` (Debian 13 only).
- Each `system_settings` sub-area is conditionally included via the toggle pattern documented in the top-level `manage/AGENTS.md`.
- `system_tools` has 7 sub-area toggles (`archives`, `build`, `core`, `fm`, `net`, `transfer`, `stats`); defaults to all true.

## Conventions

- **Multi-file sub-areas are intentional** — `system_settings` and `system_tools` are organized by concern (one file per sub-area), not by phase. Flattening would mix unrelated configs.
- **`package_manager` toggle pattern** — `package_manager_enable_repos_{main,updates,backports,security}`, `package_manager_enable_auto_upgrades`. Disabled sub-steps skip without effect.
