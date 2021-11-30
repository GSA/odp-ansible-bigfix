
This Ansible role installs and configures the BigFix agent required to communicate with client machines in AWS via the GRACE Relay.

The role supports Amazon Linux 2, Red Hat Enterprise Linux, Ubuntu and Windows.

## For Agent Configuration

This role needs the followings to successfully install and configure the BigFix agent:
 - installer binary file for the operating system, in which this role needs to install the agent. Installer file should be placed at files folder. For example:
     - BESAgent-10.0.3.66-rhe6.x86_64.rpm for RedHat and Amazon Linux
     - BESAgent-10.0.3.66-ubuntu10.amd64.deb for Ubuntu
     - BigFixAgent.msi for Windows
 - set the binary file name as value for BIGFIX_AGENT_PACKAGE_NAME as given in the code snippet below
 - license file. Obtain the license file actionsite.afxm from GSA and place under files folder



```
ansible-playbook playbook.yml -vvvv 
```

```
playbook.yml
---
- hosts: your-host-name-or-ip
  become: yes
  roles:
  - { role: odp-ansible-bigfix, BIGFIX_AGENT_PACKAGE_NAME: "BESAgent-10.0.3.66-rhe6.x86_64.rpm" }
```

  #- { role: odp-ansible-bigfix, BIGFIX_AGENT_PACKAGE_NAME: "BESAgent-10.0.3.66-rhe6.x86_64.rpm" }
  #- { role: odp-ansible-bigfix, BIGFIX_AGENT_PACKAGE_NAME: "BESAgent-10.0.3.66-ubuntu10.amd64.deb" }
  - { role: odp-ansible-bigfix, BIGFIX_AGENT_PACKAGE_NAME: "BigFixAgent.msi" }



