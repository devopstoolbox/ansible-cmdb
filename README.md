Role Name
=========

ansible-cmdb: Ansible-cmdb

[![Build Status](https://travis-ci.org/cmihai-ansible/ansible-cmdb.svg?branch=master)](https://travis-ci.org/cmihai-ansible/ansible-cmdb)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.ansible-cmdb](https://galaxy.ansible.com/devops-toolbox.ansible-cmdb)

```bash
ansible-galaxy install devops-toolbox.ansible-cmdb
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
ansible-cmdb_packages_state: present
ansible-cmdb_remove_packages: true
ansible-cmdb_enable_service: true
ansible-cmdb_enable_selinux: true
ansible-cmdb_copy_templates: true
ansible-cmdb_firewall_configure: true
ansible-cmdb_firewall_rules:
  - service: ssh
  - port: 3389
ansible-cmdb_users:
  - user: devops
    group: docker
ansible-cmdb_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install ansible-cmdb on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: ansible-cmdb is configured
      import_role:
        name: devops-toolbox.ansible-cmdb
      vars:
        ansible-cmdb_packages_state: present
        ansible-cmdb_remove_packages: true
        ansible-cmdb_enable_service: true
        ansible-cmdb_enable_selinux: true
        ansible-cmdb_copy_templates: true
        ansible-cmdb_firewall_configure: true
        ansible-cmdb_firewall_rules:
          - service: ssh
          - port: 3389
        ansible-cmdb_users:
          - user: devops
            group: docker
        ansible-cmdb_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: ansible-cmdb
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
