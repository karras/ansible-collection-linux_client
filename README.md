# Ansible Collection - karras.linux\_client

A collection of roles to manage Linux-based development clients.

[![Test](https://github.com/karras/ansible-collection-linux_client/actions/workflows/test.yml/badge.svg)](https://github.com/karras/ansible-collection-linux_client/actions/workflows/test.yml) [![Release](https://github.com/karras/ansible-collection-linux_client/actions/workflows/release.yml/badge.svg)](https://github.com/karras/ansible-collection-linux_client/actions/workflows/release.yml)

## Compatibility

Currently only supports Arch Linux.

## Roles

The following roles are part of this collection:

| Role                                          | Purpose                        | Dependencies |
| --------------------------------------------- | ------------------------------ | ------------ |
| [cis\_baseline](./roles/cis_baseline)         | CIS baseline configuration     | n/a          |
| [desktop\_baseline](./roles/desktop_baseline) | Desktop baseline configuration | n/a          |
| [firewalld](./roles/firewalld)                | Firewalld setup                | n/a          |
| [greetd](./roles/greetd)                      | Login manager greetd setup     | n/a          |
| [hardware](./roles/hardware)                  | Hardware related settings      | n/a          |
| [networkmanager](./roles/networkmanager)      | NetworkManager setup           | n/a          |
| [os\_baseline](./roles/os_baseline)           | OS baseline configuration      | n/a          |
| [users](./roles/users)                        | User and group management      | n/a          |
| [wayfire](./roles/wayfire)                    | Wayfire compositor setup       | n/a          |

Whenever possible only Ansible builtin modules are leveraged, which can lead to
some more complex tasks structures though.

## Usage

Follow the below steps to start using the collection:

* Install the latest collection version:

```sh
ansible-galaxy collection install karras.linux_client
```

* Create a new playbook (e.g. `client.yml`) which includes the desired roles:

```yaml
---

- name: deploy and manage linux clients
  hosts: all
  become: yes
  roles:
    - karras.linux_client.os_baseline
    - karras.linux_client.hardware
    - karras.linux_client.users
    - karras.linux_client.greetd
    - karras.linux_client.wayfire
    - karras.linux_client.desktop_baseline
    - karras.linux_client.networkmanager
    - karras.linux_client.firewalld
    - karras.linux_client.cis_baseline
```

* Define an inventory, in this case Ansible is executed against localhost:

```ini
[dev]
testclient ansible_connection=local
```

* Finally run the playbook:

```sh
ansible-playbook client.yml -i inventory -K
```

## License

See [LICENSE](./LICENSE)
