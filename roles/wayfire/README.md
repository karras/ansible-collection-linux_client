# Ansible Role - wayfire

Installs and configures the Wayfire compositor.

The role also supports deploying an integration into greetd. Note the
additional requirements described below though.

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes

  roles:
    - role: wayfire
      wayfire_greetd_config: |
        [autostart]
        autostart_wf_shell = false
        dm = gtkgreet -l -s /etc/greetd/gtkgreet.css && wayland-logout

        [core]
        plugins  = autostart
        vheight  = 1
        vwidth   = 1
        xwayland = false
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# List of additional packages to install
wayfire_dependencies:
  - polkit

# Optional greetd integration config to deploy
wayfire_greetd_config: ''

# List of wayfire related packages to install including their version
wayfire_packages:
  - name: wf-config
    version: 0.7.1-3
    url: 'https://github.com/karras/aur-package-builds/releases/download/v1.0.1'
    suffix: -x86_64.pkg.tar.zst
  - name: wayfire
    version: 0.7.2-1
    url: 'https://github.com/karras/aur-package-builds/releases/download/v1.0.1'
    suffix: -x86_64.pkg.tar.zst
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main wayfire
```

## Requirements

This roles has no additional role requirements but depends on the Wayfire
package(s) being pre-built and available via HTTPS for download.

By default the packages are downloaded from
[github.com/karras/aur-package-builds](https://github.com/karras/aur-package-builds).

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
