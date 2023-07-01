# Ansible Role - greetd

Installs and configures the [greetd](https://git.sr.ht/~kennylevinsen/greetd)
login manager.

The role also supports configuring `greetd-gtkgreet` and a custom CSS config
for it. Note the additional requirements described below though.

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: true

  roles:
    - role: greetd
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# Command to run at start
greetd_config_command: 'agreety --cmd $SHELL'

# The user to run the command as
greetd_config_user: greeter

# The VT to run the greeter on. Can be "next", "current" or a number
# designating the VT (must be a string).
greetd_config_vt: '1'

# List of environments to configure for selection at login
greetd_environments:
  - wayfire

# Custom CSS configuration for greetd-gtkgreet (multiline string)
greetd_gtkgreet_css: ''

# List of greetd related packages to install
greetd_packages:
  - greetd
  - greetd-gtkgreet
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main greetd
```

## Requirements

This role has no additional role requirements but depends on the greetd
package(s) being pre-built and available through a repository (which is the
case for Arch Linux).

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
