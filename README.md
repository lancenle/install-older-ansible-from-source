# Older Ansible installation from source with PIP
## This runs with CentOS and RHEL

In certain circumstances you may need to install an older version of Ansible.  Perhaps Ansible playbooks have been 
written under older Ansible versions, and the playbooks need to be migrated to a new server.  Ansible has evolved
and syntax and features have changed.  Old playbooks may break under newer Ansible versions.  
Older versions of Ansible did not provide neat installation packages, but rather must be installed from source.

Ensure yum has access to the EPEL repo in /etc/yum.repos.d/.  Execute the commands as root or with sudo.  In this example,
Ansible 1.7 is the installation target.


```
yum install python-devel python-setuptools python

yum --enablerepo=*EPEL install python-pip

easy_install pip

pip install --upgrade pip

pip install paramiko PyYAML jinja2 (optional, may not be necessary if software already installed)

(see notes if running pip install ansible==1.7 instead of cloning)

cd into a directory where you want to clone Ansible

git clone https://github.com/ansible/ansible.git (creates folder ./ansible/)

cd ansible/

git checkout release1.7.0

python setup.py install

ansible --version

```

Note:  Running "pip install ansible==1.7" (without quotes) instead of clonig appears to install Ansible correctly, however,
when running the ansible executable, several Python errors occur.
