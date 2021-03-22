## zabbix-ansible

First steps with Ansible and Zabbix collections on FreeBSD and Ubuntu

### Packages FreeBSD

- Package - py37-pip-20.2.3		Tool for installing and managing Python packages
- Package - py37-ansible-2.9.7		Radically simple IT automation

### Packages Ubuntu

- Package - ansible			2.0.0.2-2ubuntu1.3
- Package - python-pip			8.1.1-2ubuntu0.6

### How it works

Ansible use collections https://galaxy.ansible.com/community/zabbix and by
Zabbix API create Host's in Zabbix monitoring system.

### Install Ubuntu

```console
sudo apt install python-pip
sudo apt install ansible

pip3 install zabbix-api
Collecting zabbix-api
  Downloading zabbix-api-0.5.4.tar.gz (5.6 kB)
Building wheels for collected packages: zabbix-api
  Building wheel for zabbix-api (setup.py) ... done
  Created wheel for zabbix-api: filename=zabbix_api-0.5.4-py3-none-any.whl size=5612 sha256=f6903e16d4c89c507ee4cd8d8d70447a563731a89de33072799ed5d89f135343
  Stored in directory: /root/.cache/pip/wheels/a4/96/9f/c842db4c072e03fb30233828f7fceef11a92450964261de964
Successfully built zabbix-api
Installing collected packages: zabbix-api
Successfully installed zabbix-api-0.5.4
```

### Install FreeBSD

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
```

### Install ansible collection zabbix

```console
ansible-galaxy collection install -r requirements.yml
rocess install dependency map
Starting collection install process
Installing 'community.zabbix:1.2.0' to '/root/.ansible/collections/ansible_collections/community/zabbix'
```

### Run playbook
```console
ansible-playbook zabbix-add-host-group.yml
...
ansible-playbook zabbix-add-host-seznam.yml
PLAY [Using Zabbix collection] **********************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************
ok: [localhost]

TASK [Create a Seznam host or update] ***************************************************************************************************************************************
changed: [localhost]

PLAY RECAP ******************************************************************************************************************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

### Images

![Zabbix Host detail](./images/Zabbix-Host-Detail.png)

### To do

- Create Zabbix user
- Create other Zabbix objects