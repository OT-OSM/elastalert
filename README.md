Role Name
=========
```
This role to install and setup elastalert along with relative alert configuration defined by user.
```

Supported OS
------------
```
ubuntu 18
```

Dependencies
------------
```
python3
python-pip3
PyYAML
```

Variables & Default vars for elastalert
---------------------------------------

We are using below mention variables in this role.
```
host_name: localhost
port: 9300
rule_dir: rules
elastalert_service_user_name: "elastalert"
elastalert_service_group_name: "elastalert"
elastalert_data_dir: "/opt"
installation_dir: "/opt"
elastalert_version: "0.2.1"
elastalert_rules_dir: "/opt/elastalert/rules"
elastalert_rules_file: "/home/ubuntu/example-rule.yml"
```

Example Playbook
----------------
```
---
- name: It will automate elastalert setup.
  hosts: server
  become_user: root
  gather_facts: true
  roles:
    - role: osm_elastalert
...

```

Author Information
------------------
```
Name: Ashutosh Mishra
MailID: ashutosh.mishra@opstree.com
```
