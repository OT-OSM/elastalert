### https://galaxy.ansible.com/opstree_devops/elastalert BY Ashutosh Mishra.


Ansible Role: ElastAlert
========================
This role to install and setup elastalert along with relative alert configuration defined by user.

Version History
---------------

|**Date**| **Version**| **Description**| **Changed By** |
|----------|---------|---------------|-----------------|
|**27 June 2020** | v0.0.1 | Initial Draft | Ashutosh Mishra |
|**11 January 2021** | v0.0.2 | Rule management update | Paul Belloc @NanoPish |

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
| host_name | localhost | Elasticsearch host | Mandatory |
| es_port | 9200 | Elasticsearch port | Mandatory |
| elastalert_rules_dir | /opt/elastalert/rules | Directory for ElastAlert rules | Mandatory |
| elastalert_upload_local_rules_dir | files/elastalert/rules | Ansible machine uploads rules in this directory. Use False if you want to upload manually | Mandatory if you want the role to upload rules from elastalert_upload_local_rules_dir on ansible machine to elastalert_rules_dir in elastalert machine |
| elastalert_delete_rules_not_in_elastalert_upload_local_rules_dir | yes | Will delete rules not present in elastalert_upload_local_rules_dir | Mandatory if you want to delete rules on elastalert machine that are not in elastalert_upload_local_rules_dir on ansible machine|
| elastalert_service_user_name | elastalert | ElastAlert user name | Mandatory |
| elastalert_service_group_name | elastalert | ElastAlert group name | Mandatory |
| elastalert_data_dir | /opt | Data directory  | Mandatory |
| installation_dir | /opt | ElastAlert installation directory | Mandatory |
| elastalert_version | 0.2.1 | ElastAlert version | Mandatory |
| es_user | elastic | elasticsearch username | Manadatory if there is authentication in ES |
| es_pass | password | elasticsearch password | Manadatory if there is authentication in ES |
| use_ssl | False | use SSL | Optional (only if you need SSL) |
| verify_certs | False | verify certs | Optional (only if you need SSL and want to verify certs) |
| client_cert | /opt/elastalert/clientcert.cer | ssl cert | Optional (only if you need SSL) |
| client_key | /opt/elastalert/clientcert.key | ssl cert key | Optional (only if you need SSL) |

Example Playbook
----------------
Simple example

```
---
- name: It will automate ElastAlert setup
  hosts: elastalert
  roles:
    - role: osm_elastalert
        es_pass: password
        host_name: "your elasticsearch ip or domain"
...
```

With HTTP elasticsearch auth + SSL + specific local elastalert rules dir + slack webhook used in rules file

```
---
- name: It will automate ElastAlert setup
  hosts: elastalert
  roles:
    - role: osm_elastalert
        es_pass: password
        use_ssl: True
        client_cert: /opt/elastalert/clientcert.cer
        client_key: /opt/elastalert/clientcert.key
        slack_webhook_url: "https://hooks.slack.com/services/your_webhook_url"
        host_name: "your elasticsearch ip or domain"
        elastalert_upload_local_rules_dir: files/elastalert/cluster_one_elastalert_rules/
...
```

Run all tasks

```
$  ansible-playbook site.yml -i inventory
```

Only run tasks related to uploading and deleting rules to sync elastalert rules directory's content with the local ansible rules directory's  content
```
$  ansible-playbook site.yml --tags elastalert,elastalert-rules
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
