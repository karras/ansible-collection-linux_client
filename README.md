# Ansible Collection - karras.linux\_client

A collection of roles to manage Linux-based development clients.

[![Test](https://github.com/karras/ansible-collection-linux_client/actions/workflows/test.yml/badge.svg)](https://github.com/karras/ansible-collection-linux_client/actions/workflows/test.yml)[![Release](https://github.com/karras/ansible-collection-linux_client/actions/workflows/release.yml/badge.svg)](https://github.com/karras/ansible-collection-linux_client/actions/workflows/release.yml)

## Compatibility

Currently only supports Arch Linux.

## Roles

The following roles are part of this collection:

| Role                                          | Purpose                        | Dependencies |
| --------------------------------------------- | ------------------------------ | ------------ |
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

TODO

## License

See [LICENSE](./LICENSE)
