Role Name
=========

kafka: Kafka

[![Build Status](https://travis-ci.org/cmihai-ansible/kafka.svg?branch=master)](https://travis-ci.org/cmihai-ansible/kafka)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.kafka](https://galaxy.ansible.com/devopstoolbox.kafka)

```bash
ansible-galaxy install devopstoolbox.kafka
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
kafka_packages_state: present
kafka_remove_packages: true
kafka_enable_service: true
kafka_enable_selinux: true
kafka_copy_templates: true
kafka_firewall_configure: true
kafka_firewall_rules:
  - service: ssh
  - port: 3389
kafka_users:
  - user: devops
    group: docker
kafka_selinux_booleans:
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
- name: Install kafka on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: kafka is configured
      import_role:
        name: devopstoolbox.kafka
      vars:
        kafka_packages_state: present
        kafka_remove_packages: true
        kafka_enable_service: true
        kafka_enable_selinux: true
        kafka_copy_templates: true
        kafka_firewall_configure: true
        kafka_firewall_rules:
          - service: ssh
          - port: 3389
        kafka_users:
          - user: devops
            group: docker
        kafka_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: kafka
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
