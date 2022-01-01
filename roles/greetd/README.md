# Ansible Role - greetd

Installs and configures the greetd login manager.

The role also supports configuring greetd-gtkgreet and a custom CSS config.
Note the additional requirements described below though.

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes

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

# List of greetd related packages to install including their version
greetd_packages:
  - name: greetd
    version: 0.8.0-1
    url: 'https://github.com/karras/aur-package-builds/releases/download/v1.0.1'
    suffix: -x86_64.pkg.tar.zst
  - name: greetd-gtkgreet
    version: 0.7-1
    url: 'https://github.com/karras/aur-package-builds/releases/download/v1.0.1'
    suffix: -x86_64.pkg.tar.zst
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main greetd
```

## Requirements

This roles has no additional role requirements but depends on the greetd
package being pre-built and available via HTTPS for download.

By default the packages are downloaded from
[github.com/karras/aur-package-builds](https://github.com/karras/aur-package-builds).

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
