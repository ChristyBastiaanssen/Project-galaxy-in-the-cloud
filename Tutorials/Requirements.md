# Requirements for installing Galaxy with Ansible
## VM requirements
The VM needs to have:
- At least 2 v(irtual)CPU
- At least 4GB RAM
- Preferably running Ubuntu 18.04 - 20.04.

## Ansible
Ansible needs to be installed on the machine where you will install Galaxy.

Ansible can be installed by following the installation guide from the Ansible documentation.
For example when using Ubuntu as the OS:

```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

As of May 31 2022, the Ansible version needs to be >=2.7.
The version can be checked by running the following command:

```
ansible --version
```

## Other requirements
Besides having Ansible installed, it is expected that:
- There is an inventory file with the VM or host specified where you will deploy Galaxy.
- The VM has a public DNS name.
- The full DNS hostname is written in the inventory file and not localhost. 
- The following ports are exposed:
1. 22 for SSH, this can be a different port or via VPN or similar.
2. 80 for HTTP, this needs to be available to the world if you want to follow the LetsEncrypt portion of the tutorial.
3. 443 for HTTPs, this needs to be available to the world if you want to follow the LetsEncrypt portion of the tutorial.
4. 5671 for AMQP for Pulsar, needed if you plan to setup Pulsar for remote job running.
- Python3 is installed. This can be checked by running the following command: 

```
python3 -V
```


### Sources
https://docs.ansible.com/ansible/2.9/installation_guide/intro_installation.html 
https://training.galaxyproject.org/training-material/topics/admin/tutorials/ansible-galaxy/tutorial.html#installing-galaxy 
