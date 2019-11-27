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
```

Variables & Default vars for elastalert
---------------------------------------

We are using below mention variables in this role.
```
host_name: localhost
port: 9300
rule_dir: rules
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
