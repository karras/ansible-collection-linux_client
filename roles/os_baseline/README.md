# Ansible Role - os\_baseline

Manages OS related basic configs for workstations.

## Example Playbook

As this role is tested via Molecule one can use that playbook as a starting
point:

```
- name: Converge
  hosts: all
  gather_facts: yes

  roles:
    - role: os_baseline
      os_baseline_timezone_hwclock: 0
      os_baseline_timezone: Europe/Busingen
      os_baseline_locales:
        - 'en_GB.UTF-8 UTF-8'
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

## Requirements

This roles has no additional requirements.

```yml
# List of mirrors to activate
os_baseline_mirrors:
  - 'https://pkg.adfinis.com/archlinux/$repo/os/$arch'

# List of baseline packages to install
os_baseline_packages:
  - base
  - dhclient
  - intel-ucode
  - linux
  - linux-firmware
  - lvm2
  - vi

# Timezone to configure
os_baseline_timezone: Etc/UTC

# Whether the hardware clock is in UTC or local timezone
# Valid values are 0 ('UTC') and 1 ('local')
os_baseline_timezone_hwclock: 0

# Configuration for systemd-timesyncd (see `man timesyncd.conf`)
os_baseline_timesyncd_config:
  ntp:
  fallback_ntp: '0.arch.pool.ntp.org 1.arch.pool.ntp.org 2.arch.pool.ntp.org 3.arch.pool.ntp.org'
  root_distance_max_sec: 5
  poll_interval_min_sec: 32
  poll_interval_max_sec: 2048

# List of locales to activate
os_baseline_locales:
  - 'en_US.UTF-8 UTF-8'
  - 'en_US ISO-8859-1'
```

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
