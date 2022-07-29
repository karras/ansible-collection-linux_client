# Ansible Role - cis\_baseline

Manages CIS security baseline settings for clients.

* Arch Linux: CIS Distribution Independent Linux" (`v2.0.0` - `07-06-2019`)

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes

  roles:
    - role: cis_baseline
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# List of CIS rule sections to include
cis_baseline_sections:
  - 1_1_filesystem

# List of specific CIS rules to ignore
cis_baseline_ignored_rules: []
#  - 1.1.1.1
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
