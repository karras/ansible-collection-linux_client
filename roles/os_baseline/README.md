# Ansible Role - os\_baseline

Manages OS related basic configs for workstations.

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
- name: Converge
  hosts: all
  gather_facts: yes

  roles:
    - role: os_baseline
      os_baseline_locales:
        - 'en_GB.UTF-8 UTF-8'
      os_baseline_locales_config:
        lang: en_US.UTF-8
        language: en_US.UTF-8
        lc_address: en_US.UTF-8
        lc_collate: en_US.UTF-8
        lc_ctype: en_US.UTF-8
        lc_identification: en_US.UTF-8
        lc_measurement: en_US.UTF-8
        lc_messages: en_US.UTF-8
        lc_monetary: en_US.UTF-8
        lc_name: en_US.UTF-8
        lc_numeric: en_US.UTF-8
        lc_paper: en_GB.UTF-8
        lc_telephone: en_US.UTF-8
        lc_time: en_US.UTF-8
      os_baseline_timezone_hwclock: 0
      os_baseline_timezone: Etc/UTC
      os_baseline_vconsole_keymap: de
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# Domain of the system
os_baseline_domain: local

# Hostname of the system
os_baseline_hostname: '{{ ansible_hostname }}'

# List of locales to activate
os_baseline_locales:
  - 'en_US.UTF-8 UTF-8'
  - 'en_US ISO-8859-1'

# Configuration of the system-wide locales
os_baseline_locales_config:
  lang: en_US.UTF-8
  language: en_US.UTF-8
  lc_address: en_US.UTF-8
  lc_collate: en_US.UTF-8
  lc_ctype: en_US.UTF-8
  lc_identification: en_US.UTF-8
  lc_measurement: en_US.UTF-8
  lc_messages: en_US.UTF-8
  lc_monetary: en_US.UTF-8
  lc_name: en_US.UTF-8
  lc_numeric: en_US.UTF-8
  lc_paper: en_US.UTF-8
  lc_telephone: en_US.UTF-8
  lc_time: en_US.UTF-8

# List of mirrors to activate
os_baseline_mirrors:
  - 'https://pkg.adfinis.com/archlinux/$repo/os/$arch'

# List of baseline packages to install
os_baseline_packages:
  - base
  - binutils
  - dhclient
  - linux
  - linux-firmware
  - man-db
  - lvm2
  - vi

# Configuration for systemd-timesyncd (see `man timesyncd.conf`)
os_baseline_timesyncd_config:
  ntp:
  fallback_ntp: '0.arch.pool.ntp.org 1.arch.pool.ntp.org 2.arch.pool.ntp.org 3.arch.pool.ntp.org'
  root_distance_max_sec: 5
  poll_interval_min_sec: 32
  poll_interval_max_sec: 2048

# Timezone to configure
os_baseline_timezone: Etc/UTC

# Whether the hardware clock is in UTC or local timezone
# Valid values are 0 ('UTC') and 1 ('local')
os_baseline_timezone_hwclock: 0

# Keymap to configure for the virtual consoles (see `man vconsole.conf`)
os_baseline_vconsole_keymap: us
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main os_baseline
```

## Requirements

This roles has no additional requirements.

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
