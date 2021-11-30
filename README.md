
odp-ansible-bigfix
==================

The ansible role `odp-ansible-bigfix` is used to install and configure the BigFix agent.

Requirements
------------

### OS Supported

* RHEL 8
* CentOS 7
* Amazon Linux 2
* Amazon EKS enhanced Linux ( Based on Amazon Linux 2 )
* Ubuntu releases running systemd ( 16.04, 18.04, etc )

### Requirements

This role needs the followings to successfully install and configure the BigFix agent:
 - installer binary file for the operating system, in which this role needs to install the agent. Installer file should be placed at files folder. For example:
     - BESAgent-10.0.3.66-rhe6.x86_64.rpm for RedHat and Amazon Linux
     - BESAgent-10.0.3.66-ubuntu10.amd64.deb for Ubuntu
     - BigFixAgent.msi for Windows
 - set the binary file name as value for BIGFIX_AGENT_PACKAGE_NAME as given in the code snippet below
 - license file. Obtain the license file actionsite.afxm from GSA and place under files folder

Role Variables
--------------
| Variable | Description | Required |
| ---  | ---  | --- |
| bigfix_server_url |  BigFix Server | true  |
| BIGFIX_AGENT_PACKAGE_NAME | BigFix Installer file name | true  |
| GSA_FISMA_System_ID |  GSA FISMA System ID  | false |
| GSA_Patch_Group | GSA Patch Group  | false |


Dependencies
------------

* No external role dependencies

Example Playbook
----------------
```
ansible-playbook playbook.yml
```

```
playbook.yml
---
- hosts: your-host-name-or-ip
  become: yes
  roles:
  - { role: odp-ansible-bigfix, BIGFIX_AGENT_PACKAGE_NAME: "BESAgent-10.0.3.66-rhe6.x86_64.rpm",  bigfix_server_url: "server-name:port"}
```

License
-------

BSD

Author Information
------------------

GSA OCISO DevSecops Team - ociso-devsecops@gsa.gov
Github Repository - https://github.com/GSA/odp-ansible-bigfix