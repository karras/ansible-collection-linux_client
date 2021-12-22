# Ansible Role - users

Manages user accounts and groups.

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes

  roles:
    - role: users
      users_group_list:
        - name: clark
          gid: 1000
          system: no
          state: present
        - name: superheroes
          gid: 2000
          system: no
          state: present
      users_user_list:
        - name: clark
          append: no
          comment: ''
          create_home: yes
          expires:
          group: clark
          groups:
            - superheroes
          home: /home/clark
          password: 'schmetterling12'
          remove: no
          shell: /bin/zsh
          system: no
          uid: 1000
          update_password: on_create
          state: present
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
# List of user packages to install
users_packages:
  - sudo
  - zsh

# List of groups to manage
users_group_list: []
#  - name: clark
#    gid: 1000
#    system: no
#    state: present
#  - name: superheroes
#    gid: 2000
#    system: no
#    state: present

# List of users to manage
users_user_list: []
#  - name: clark
#    append: no
#    comment: ''
#    create_home: yes
#    expires:
#    group: clark
#    groups:
#      - superheroes
#    home: /home/clark
#    password: ''
#    remove: no
#    shell: /bin/zsh
#    system: no
#    uid: 1000
#    update_password: on_create
#    state: present
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r roles -e main users
```

## Requirements

This roles has no additional requirements.

## License

See [LICENSE](./LICENSE)

## Author Information

[Karras](https://github.com/karras)
