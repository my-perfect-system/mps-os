# `odem.os` Ansible Collection

Operating system init for Debian 13 (trixie): package sources,
unattended upgrades, locale / keyboard / console / timezone, core CLI
tooling.

## Galaxy metadata

- **namespace**: `odem`
- **name**: `os`
- **version**: `0.3.1`
- **dependencies**: `odem.base`, `ansible.posix`

See [`galaxy.yml`](galaxy.yml) for the canonical values.

## Roles

| Role | Purpose |
|---|---|
| [`odem.os.package_manager`](roles/package_manager/README.md) | Configure APT sources (4 pockets × components × deb-src), install base packages, configure unattended-upgrades. |
| [`odem.os.system_settings`](roles/system_settings/README.md) | Configure locale, keyboard, console, and timezone. 4 sub-areas with own handlers. |
| [`odem.os.system_tools`](roles/system_tools/README.md) | Apt-by-category groups for archives, build, file-manager, network, transfer, statistics tools. Per-area toggles. |

## Installation

```bash
ansible-galaxy collection install odem.os
```

## Usage

```yaml
- hosts: all
  become: true
  roles:
    - odem.os.package_manager
    - odem.os.system_settings
    - odem.os.system_tools
```

## Host prerequisites

Every role in this collection declares `odem.base.assert_debian13` as a
dependency, so the play fails fast if the target host isn't Debian 13.

## Documentation

- [`AGENTS.md`](AGENTS.md) — developer-facing conventions
- `roles/<role>/README.md` — per-role variable docs

## License

GPL-3.0-or-later
