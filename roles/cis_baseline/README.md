# Ansible Role - cis\_baseline

Manages CIS security baseline settings for clients.

* Arch Linux: CIS Distribution Independent Linux" (`v2.0.0` - `07-06-2019`)

Due to missing packages or capabilities related to Arch Linux, the following
chapters and controls have not yet been implemented:

* 1.3 Filesystem Integrity Checking (missing and broken AIDE packages)

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
# List of CIS rule sections to include
cis_baseline_sections:
  - 1_1_filesystem
  - 1_2_software_updates

# List of specific CIS rules to ignore
cis_baseline_ignored_rules: []
#  - 1.1.1.1

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
