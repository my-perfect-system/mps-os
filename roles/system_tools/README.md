---
namespace: odem
collection: os
role: system_tools
---

# `odem.os.system_tools`

Install essential CLI tools, grouped in configurable categories

## Default variables

| Variable | Default | Description |
|---|---|---|
| `system_tools_enable_archives` | `true` | Install archive tools (zip, unzip, bzip2, attr, dtrx) |
| `system_tools_enable_build` | `true` | Install build tools (gcc, gdb, lldb, build-essential, check, flex, bison, automake) |
| `system_tools_enable_core` | `true` | Install core system packages (sudo, gnupg, rsyslog, jq, ...) |
| `system_tools_enable_fm` | `true` | Install file management CLI tools (bat, eza, tree, ncdu, entr, ripgrep) |
| `system_tools_enable_net` | `true` | Install networking tools (net-tools, bind9-dnsutils, tcpdump, nmap, ...) |
| `system_tools_enable_stats` | `true` | Install monitoring tools (htop, iftop, sysstat, fio) |
| `system_tools_enable_transfer` | `true` | Install transfer tools (curl, wget, rsync) |

## Dependencies

- `odem.base.assert_debian13`

## Example usage

```yaml
- hosts: all
  roles:
    - odem.os.system_tools
```

## Role metadata

- **Min Ansible version**: `2.16.0`
- **License**: GPL-3.0-or-later
- **Platforms**: Debian (trixie)
- **Tasks file lines**: 28

## Related files

- [`meta/main.yml`](meta/main.yml) — galaxy_info + role dependencies
- [`meta/argument_specs.yml`](meta/argument_specs.yml) — variable spec (the source of the variable table above)
- [`defaults/main.yml`](defaults/main.yml) — variable defaults (the source of the default values above)
