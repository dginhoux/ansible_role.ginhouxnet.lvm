Ansible Role : dginhoux.lvm
=========

This ansible role configure lvm, create, remove, extend and mount


Requirements
------------

This role is built to only run on platforms defined in `meta/main.yml`


Role Variables
--------------



```yaml
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

  - vg_name: vg_swarm_registry
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
```


Dependencies
------------

none


Example Playbook
----------------



License
-------

BSD


Author Information
------------------

https://github.com/dginhoux/
