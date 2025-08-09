# Ansible Role - desktop\_baseline

Manages Linux desktop related basic configs for clients.

The following components are managed by this role:

* Desktop baseline packages

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: true

  roles:
    - role: desktop_baseline
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# Whether to enable multilib support or not
desktop_baseline_multilib: no

# List of desktop packages to install
desktop_baseline_packages:
  - bemenu-wayland
  - brightnessctl
  - neovim
  - swaybg
  - swayidle
  - swaylock
  - terminator
  - waybar
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main desktop_baseline
```

## Requirements

This roles has no additional requirements.

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
