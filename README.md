Role Name
=========

time: Time

[![Build Status](https://travis-ci.org/cmihai-ansible/time.svg?branch=master)](https://travis-ci.org/cmihai-ansible/time)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.time](https://galaxy.ansible.com/devopstoolbox.time)

```bash
ansible-galaxy install devopstoolbox.time
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
time_packages_state: present
time_remove_packages: true
time_enable_service: true
time_enable_selinux: true
time_copy_templates: true
time_firewall_configure: true
time_firewall_rules:
  - service: ssh
  - port: 3389
time_users:
  - user: devops
    group: docker
time_selinux_booleans:
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
- name: Install time on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: time is configured
      import_role:
        name: devopstoolbox.time
      vars:
        time_packages_state: present
        time_remove_packages: true
        time_enable_service: true
        time_enable_selinux: true
        time_copy_templates: true
        time_firewall_configure: true
        time_firewall_rules:
          - service: ssh
          - port: 3389
        time_users:
          - user: devops
            group: docker
        time_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: time
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
