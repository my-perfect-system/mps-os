---
# Reference doc — auto-generated, do not edit by hand.
# Regenerate via: python3 manage/gen_role_readmes.py
namespace: mps
collection: os
role: system_settings
---

# `mps.os.system_settings`

Configure locale, keyboard, console, and timezone

## Default variables

| Variable | Default | Description |
|---|---|---|
| `system_settings_console_charset` | `UTF-8` | Console character map (CHARMAP) |
| `system_settings_console_codeset` | `Lat15` | Console code set (CODESET) |
| `system_settings_console_fontface` | `Terminus` | Console font face (FONTFACE) |
| `system_settings_console_fontsize` | `8x16` | Console font size (FONTSIZE) |
| `system_settings_keyboard_layout` | `de` | Keyboard layout (XKBLAYOUT) |
| `system_settings_keyboard_model` | `pc105` | Keyboard model (XKBMODEL) |
| `system_settings_keyboard_options` | `compose:menu` | Keyboard options (XKBOPTIONS) |
| `system_settings_keyboard_variant` | `nodeadkeys` | Keyboard variant (XKBVARIANT) |
| `system_settings_locale_name` | `en_US.UTF-8` | System locale (LANG/LANGUAGE/LC_ALL) |
| `system_settings_timezone` | `Europe/Berlin` | System timezone (timedatectl) |

## Dependencies

- `mps.base.assert_debian13`

## Example usage

```yaml
- hosts: all
  roles:
    - mps.os.system_settings
```

## Role metadata

- **Min Ansible version**: `2.16.0`
- **License**: GPL-3.0-or-later
- **Platforms**: Debian (trixie)
- **Tasks file lines**: 12

## Related files

- [`meta/main.yml`](meta/main.yml) — galaxy_info + role dependencies
- [`meta/argument_specs.yml`](meta/argument_specs.yml) — variable spec (the source of the variable table above)
- [`defaults/main.yml`](defaults/main.yml) — variable defaults (the source of the default values above)
