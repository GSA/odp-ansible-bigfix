
This Ansible role installs and configures the BigFix agent required to communicate with client machines in AWS via the GRACE Relay.

The role supports Amazon Linux 2, Red Hat Enterprise Linux, Ubuntu and Windows.

## For Agent Configuration

Before installation, obtain the actionsite.afxm configuration file specific to GSA and place in the 'files' directory. Update the bigfix_custom_properties in the vars/main.yml to tag instances on which the BF agent will be installed by FISMA system. A playbook named playbook.yml can be used to run the  install by running the following command, assuming the role is located in a local directory called 'bigfix'

```
ansible-playbook playbook.yml -vvvv 
```

```
playbook.yml
---
- hosts: "localhost"
  become: yes
  become_user: "root"
  vars:
    ansible_os_family: "Ubuntu"
  roles:
    - bigfix
```


