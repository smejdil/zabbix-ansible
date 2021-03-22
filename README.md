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
cd /usr/ports/devel/py-pip && make install clean
cd /usr/ports/sysutils/ansible && make install clean

pip install zabbix-api
Collecting zabbix-api
  Downloading zabbix-api-0.5.4.tar.gz (5.6 kB)
Using legacy 'setup.py install' for zabbix-api, since package 'wheel' is not installed.
Installing collected packages: zabbix-api
    Running setup.py install for zabbix-api ... done
Successfully installed zabbix-api-0.5.4

ansible-galaxy collection install -r requirements.yml
rocess install dependency map
Starting collection install process
Installing 'community.zabbix:1.2.0' to '/root/.ansible/collections/ansible_collections/community/zabbix'
```

### Run playbook
```console
ansible-playbook zabbix-add-host.yml
PLAY [Using Zabbix collection] **********************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************
ok: [localhost]

TASK [Create a Seznam host or update] ***************************************************************************************************************************************
changed: [localhost]

PLAY RECAP ******************************************************************************************************************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

## To do

- Create Host group
- Create Zabbix user
- Create other Zabbix objects