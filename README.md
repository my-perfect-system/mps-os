# `mps.os` Ansible Collection

Operating system init for Debian 13 (trixie): package sources,
unattended upgrades, locale / keyboard / console / timezone, core CLI
tooling.

## Galaxy metadata

- **namespace**: `mps`
- **name**: `os`
- **version**: `0.3.1`
- **dependencies**: `mps.base`, `ansible.posix`

See [`galaxy.yml`](galaxy.yml) for the canonical values.

## Roles

| Role | Purpose |
|---|---|
| `mps.os.package_manager` | Configure APT sources (4 pockets × components × deb-src), install base packages, configure unattended-upgrades. |
| `mps.os.system_settings` | Configure locale, keyboard, console, and timezone. 4 sub-areas with own handlers. |
| `mps.os.system_tools` | Apt-by-category groups for archives, build, file-manager, network, transfer, statistics tools. Per-area toggles. |

## Installation

```bash
ansible-galaxy collection install mps.os
```

## Usage

```yaml
- hosts: all
  become: true
  roles:
    - mps.os.package_manager
    - mps.os.system_settings
    - mps.os.system_tools
```

## Host prerequisites

Every role in this collection declares `mps.base.assert_debian13` as a
dependency, so the play fails fast if the target host isn't Debian 13.

## Documentation

- [`AGENTS.md`](AGENTS.md) — developer-facing conventions
- `roles/<role>/README.md` — per-role variable docs

## License

GPL-3.0-or-later
