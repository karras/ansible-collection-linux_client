# Ansible Role - wayfire

Installs and configures the Wayfire compositor.

The role also supports deploying an integration into
[greetd](https://git.sr.ht/~kennylevinsen/greetd) and a custom `wayfire-run`
script that can be used to inject additional environment variables before
launching Wayfire. Note the additional requirements described below though.

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
      wayfire_run_wrapper: |
        export XDG_CONFIG_HOME="$HOME/.local/etc"
        export XDG_CACHE_HOME="$HOME/.local/var/cache"
        export XDG_DATA_HOME="$HOME/.local/share"
        export XDG_STATE_HOME="$HOME/.local/var/lib"

        systemctl --user set-environment XDG_CONFIG_HOME="$HOME/.local/etc"
        systemctl --user set-environment WAYLAND_DISPLAY=wayland-1

        systemctl --user set-environment $(/usr/lib/systemd/user-environment-generators/30-systemd-environment-d-generator)
        export $(/usr/lib/systemd/user-environment-generators/30-systemd-environment-d-generator)

        wayfire
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# Optional greetd integration config to deploy (multiline string)
# This allows running a greetd-gtkgreet session via Wayfire, which in turn
# spawns a proper Wayfire session after login
wayfire_greetd_config: ''

# List of Wayfire related packages to install
wayfire_packages:
  - polkit
  - wf-config
  - wayfire

# List of Pacman repositories to configure
wayfire_repositories:
  - name: karras
    server: https://github.com/karras/aur-package-builds/releases/download/v2.0.0
    key: https://raw.githubusercontent.com/karras/aur-package-builds/main/builder_public_key.asc
    key_id: 25267573FD638312C5EBE4C40C758F9503EDE7AF

# Optional wrapper script to deploy (multiline string)
# It can be desired to run Wayfire via wrapper script, which takes care of
# setting additional environment vars first (e.g. `XDG`) before starting
# Wayfire
wayfire_run_wrapper: ''
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main wayfire
```

## Requirements

This role has no additional role requirements but depends on the Wayfire
package(s) being pre-built and available through a repository.

Thus By default the repository
[github.com/karras/aur-package-builds](https://github.com/karras/aur-package-builds)
is configured and trusted.

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
