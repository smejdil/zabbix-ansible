## zabbix-ansible

First steps with Ansible and Zabbix collections on FreeBSD

## Dependencies

- Package on server - py37-pip-20.2.3                Tool for installing and managing Python packages
- Package on server - py37-ansible-2.9.7             Radically simple IT automation

## How it works

Ansible use collections https://galaxy.ansible.com/community/zabbix and by
Zabbix API create Hosts in Zabbix monitoring system.

### Installation

```console
pip install zabbix-api
ansible-galaxy collection install -r requirements.yml
```

### Run playbook
```console
ansible-playbook zabbix-add-host.yml
```

## To do

- Create Host group
- Create Zabbix user
- Create other Zabbix objects