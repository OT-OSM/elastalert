Ansible Role: ElastAlert
========================
This role to install and setup elastalert along with relative alert configuration defined by user.

Version History
---------------

|**Date**| **Version**| **Description**| **Changed By** |
|----------|---------|---------------|-----------------|
|**June '25** | v.1.0 | Initial Draft | Ashutosh Mishra |

Salient Features
----------------
- This Role automates the Alert setup using ElastAlert.
In this role , can attach elastalert rules files.

Supported OS
------------
   * Ubuntu bionic
   * Ubuntu xenial

Requirements
------------
  * python3
  * python-pip3
  * PyYAML
  * setuptools

Dependencies
------------
  * Elasticsearch

Directory Layout
----------------
```
├── README.md
├── defaults
│   └── main.yml
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── tasks
│   ├── install.yml
│   ├── main.yml
│   └── service.yml
├── templates
│   ├── config.yaml.j2
│   └── elastalert-systemd.service.j2
├── tests
│   ├── inventory
│   └── test.yml
└── vars
    └── main.yml

7 directories, 12 files
```

Role Variables
--------------

|**Variables**| **Default Values**| **Description**| **Type**|
|----------|---------|---------------|-----------|
| host_name | localhost | ElastAlert host Name | Mandatory |
| port | 9300 | The port on which the elastalert server will work | Mandatory |
| rule_dir | rules | ElastAlert custom directory name | Mandatory |
| elastalert_service_user_name | elastalert | ElastAlert user name | Mandatory |
| elastalert_service_group_name | elastalert | ElastAlert group name | Mandatory |
| elastalert_data_dir | /opt | Data directory  | Mandatory |
| installation_dir | /opt | ElastAlert installation directory | Mandatory |
| elastalert_version | 0.2.1 | ElastAlert version | Mandatory |
| elastalert_rules_dir | /opt/elastalert/rules | Directory for ElastAlert | Mandatory |
| elastalert_rules_file | /home/ubuntu/example-rule.yml | Rule file for elastalert  | Mandatory |

Example Playbook
----------------
```
---
- name: It will automate ElastAlert setup
  hosts: server
  become: true
  roles:
    - role: osm_elastalert
...

$  ansible-playbook site.yml -i inventory

```

Inventory
----------
An inventory should look like this:-
```
[server]                 
192.xxx.x.xxx    ansible_user=ubuntu 
```

Future Proposed Changes
-----------------------
- Update elastalert for centos 6 , 7 as well.

References
----------
- **[Guide followed 1](https://elastalert.readthedocs.io/en/latest/running_elastalert.html)**
- **[Guide followed 2](https://www.fosslinux.com/6240/how-to-install-elastalert-with-elasticsearch-on-ubuntu.htm)**

Author Information
------------------
```
Name: Ashutosh Mishra
MailID: ashutosh.mishra@opstree.com
```
