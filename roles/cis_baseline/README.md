# Ansible Role - cis\_baseline

Manages CIS security baseline settings for clients.

* Arch Linux: CIS Distribution Independent Linux" (`v2.0.0` - `07-06-2019`)

Due to missing packages or capabilities related to Arch Linux, the following
chapters and controls have not yet been implemented:

* 1.3 Filesystem Integrity Checking (missing and broken AIDE packages)
* 1.4.4 Interactive Boot Deactivation (not supported for systemd-boot)
* 1.5.4 Prelink Deactivation (not available for Arch Linux)
* 1.6 Mandatory Access Control (not available for Arch Linux)

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: true

  roles:
    - role: cis_baseline
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# List of bootloader configs for which to verify their permissions (1.4.1)
cis_baseline_bootloader_configs:
  - /boot/loader/loader.conf
  - /boot/loader/entries/arch.conf

# Main systemd boot loader config to disable editor (1.4.2)
cis_baseline_bootloader_loader_config: /boot/loader/loader.conf

# List of specific CIS rules to ignore
cis_baseline_ignored_rules: []
#  - 1.1.1.1

# List of CIS rule sections to include
cis_baseline_sections:
  - 1_1_filesystem
  - 1_2_software_updates
  - 1_3_filesystem_integrity     # Not implemented yet
  - 1_4_boot_settings
  - 1_5_process_hardening
  - 1_6_mandatory_access_control
  - 1_7_warning_banners

# List of mandatory repositories to verify (1.2.1)
cis_baseline_repositories:
  - core
  - extra

# List of mandatory repository signature trust levels to verify (1.2.2)
cis_baseline_repository_siglevel:
  - PackageRequired
  - PackageTrustedOnly
  - DatabaseOptional
  - DatabaseTrustedOnly
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main cis_baseline
```

## Requirements

This roles has no additional requirements.

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
