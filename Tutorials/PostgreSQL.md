# PostgreSQL
Inleidende zin

```cd galaxy``` <br>
```mkdir group_vars``` <br>
```nano group_vars/galaxyservers.yml``` <br>

Add the following to the file:
```
---
# Python 3 support
pip_virtualenv_command: /usr/bin/python3 -m virtualenv # usegalaxy_eu.certbot, usegalaxy_eu.tiaas2, galaxyproject.galaxy
certbot_virtualenv_package_name: python3-virtualenv    # usegalaxy_eu.certbot
pip_package: python3-pip                               # geerlingguy.pip

# PostgreSQL
postgresql_objects_users:
  - name: galaxy
postgresql_objects_databases:
  - name: galaxy
    owner: galaxy
# PostgreSQL Backups
postgresql_backup_dir: /data/backups
postgresql_backup_local_dir: "{{ '~postgres' | expanduser }}/backups"
```
<br>



```nano galaxy.yml```

Add the following to the file: 
```
---
- hosts: galaxyservers
  become: true
  become_user: root
  pre_tasks:
    - name: Install Dependencies
      package:
        name: 'python3-psycopg2'
  roles:
    - galaxyproject.postgresql
    - role: natefoo.postgresql_objects
      become: true
      become_user: postgres
``` 
<br>



To view what the directory looks like by now, use the following command: <br>
```tree -L 2```

The directory should approximately look like this:
```
.
├── ansible.cfg
├── galaxy.yml
├── group_vars
│   └── galaxyservers.yml
├── hosts
├── requirements.yml
└── roles
    ├── galaxyproject.galaxy
    ├── galaxyproject.nginx
    ├── galaxyproject.postgresql
    ├── geerlingguy.pip
    ├── natefoo.postgresql_objects
    ├── uchida.miniconda
    └── usegalaxy_eu.certbot
```

### Sources
https://training.galaxyproject.org/training-material/topics/admin/tutorials/ansible-galaxy/tutorial.html#log-in-to-galaxy
