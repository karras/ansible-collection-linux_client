# Ansible Role - networkmanager

Manages NetworkManager related settings for workstations.

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes

  roles:
    - role: networkmanager
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# List of networkmanager related packages to install
networkmanager_packages:
  - networkmanager
  - network-manager-applet
  - nm-connection-editor

# List of networkmanager related services to activate
networkmanager_service_activation:
  - NetworkManager
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main networkmanager
```

## Requirements

This roles has no additional requirements.

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
