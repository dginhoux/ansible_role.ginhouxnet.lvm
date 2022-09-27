# ROLE dginhoux.lvm



## DESCRIPTION

This ansible role configure lvm, create, remove, extend and mount



## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip node with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36 |
| EL | 7, 8 |

#### ANSIBLE VERSION

Ansible >= 2.12

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.lvm
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.lvm dginhoux.lvm
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.lvm
      ansible.builtin.include_role:
        name: dginhoux.lvm
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

```yaml
---
lvm_configure: "yes"
lvm_pvresize_to_max: "true"

lvm_vg_list:
  - vg_name: vg_ansible
    pv_list:
      - /dev/sdc
    state: present
    lv_list:
      - lv_name: lv_ansible
        size: 15G
        filesystem: ext4
        # mount: "true"
        # mount_point: /mnt/lv_ansible
        state: present

  - vg_name: vg_swarm
    pv_list:
      - /dev/sdd
    state: present
    lv_list:
      - lv_name: lv_swarm_registry
        size: 35G
        filesystem: ext4
        # mount: "true"
        # mount_point: /mnt/lv_swarm_registry
        state: present
      - lv_name: lv_swarm_prod3
        size: 120G
        filesystem: xfs
        # mount: "true"
        # mount_point: /mnt/lv_swarm_prod3
        state: present
```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
