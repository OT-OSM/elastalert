Role Name
=========
```
This role to install elastAlert repository with the most recent changes/updates. 
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
```

Example Playbook
----------------
```
- hosts: localhost
  remote_user: root
  roles:
    - elastalert
```

Author Information
------------------
```
Name: Ashutosh Mishra
MailID: ashutosh.mishra@opstree.com
```
