## zabbix-ansible

First steps with Ansible and Zabbix collections on FreeBSD 12.2, OpenBSD 6.8, Ubuntu 20.04, CentOS Stream

### Packages FreeBSD

- Package - py37-pip-20.2.3				Tool for installing and managing Python packages
- Package - py37-ansible-2.9.7		Radically simple IT automation

### Packages OpenBSD

- Package - py3-pip-20.3.4      	tool for installing Python packages
- Package - ansible-2.9.19				ssh based config management framework

### Packages Ubuntu

- Package - python-pip						20.0.2-5ubuntu1.1
- Package - ansible								2.9.6+dfsg-1

### Packages CentOS

- Package - python3-pip						9.0.3-19.el8
- Package - ansible								2.9.18-2.el8	

### How it works

Ansible use collections https://galaxy.ansible.com/community/zabbix and by
Zabbix API create Host's and Host's Group in Zabbix monitoring system.

- Python package - zabbix-api 0.5.4

### Install FreeBSD

```console
cd /usr/ports/devel/py-pip && make install clean
cd /usr/ports/sysutils/ansible && make install clean

pip install zabbix-api
```

### Install OpenBSD

```console
export FLAVOR=python3
cd /usr/ports/devel/py-pip && make install clean
cd /usr/ports/sysutils/ansible && make install clean

pip3.8 install zabbix-api
```

### Install Ubuntu

```console
apt install python-pip
apt install ansible

pip3 install zabbix-api
```

### Install CentOS
```console
dnf install ansible

pip3 install zabbix-api
```

### Install ansible collection zabbix

```console
ansible-galaxy collection install -r requirements.yml
Process install dependency map
Starting collection install process
Installing 'community.zabbix:1.3.0' to '/root/.ansible/collections/ansible_collections/community/zabbix'
```

### Run playbook
```console
export ZABBIX_USER=zabbix_admin_user
export ZABBIX_PASSWORD=*******************

ansible-playbook setup_zabbix_server.yml 
PLAY [Using Zabbix collection] **********************************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************************
ok: [localhost]

TASK [include_tasks] ********************************************************************************************************************************************************************
included: /root/work/zabbix-ansible/tasks/zabbix-add-host-group.yml for localhost

TASK [Create host groups] ***************************************************************************************************************************************************************
changed: [localhost]

TASK [include_tasks] ********************************************************************************************************************************************************************
included: /root/work/zabbix-ansible/tasks/zabbix-add-host-freebsd.yml for localhost

TASK [Create a FreeBSD host or update] **************************************************************************************************************************************************
changed: [localhost]

TASK [include_tasks] ********************************************************************************************************************************************************************
included: /root/work/zabbix-ansible/tasks/zabbix-add-host-seznam.yml for localhost

TASK [Create a Seznam host or update] ***************************************************************************************************************************************************
changed: [localhost]

TASK [include_tasks] ********************************************************************************************************************************************************************
included: /root/work/zabbix-ansible/tasks/zabbix-add-host-smejdil.yml for localhost

TASK [Create a SmEjDiL host or update] **************************************************************************************************************************************************
changed: [localhost]

TASK [include_tasks] ********************************************************************************************************************************************************************
included: /root/work/zabbix-ansible/tasks/zabbix-add-screen.yml for localhost

TASK [Create screen Public/WWW-servers or update the existing screen items] *************************************************************************************************************
changed: [localhost]

TASK [include_tasks] ********************************************************************************************************************************************************************
included: /root/work/zabbix-ansible/tasks/zabbix-add-template.yml for localhost

TASK [Import Zabbix Training from XML] **************************************************************************************************************************************************
changed: [localhost]

TASK [include_tasks] ********************************************************************************************************************************************************************
included: /root/work/zabbix-ansible/tasks/zabbix-add-user.yml for localhost

TASK [create a new zabbix user.] ********************************************************************************************************************************************************
changed: [localhost]

PLAY RECAP ******************************************************************************************************************************************************************************
localhost                  : ok=15   changed=7    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

### Images

![Zabbix Host detail](./images/Zabbix-Host-Detail.png)

### To do

- Import Media
- Create other Zabbix objects