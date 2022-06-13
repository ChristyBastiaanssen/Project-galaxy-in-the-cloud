# Deploying a copy of Galaxy

```open galaxy.yml``` 

Make the following changes to the file:
```
pre_tasks:
    - name: Install Dependencies
      package:
        ~~name: 'python3-psycopg2'~~
        **name: ['acl', 'bzip2', 'git', 'make', 'python3-psycopg2', 'tar', 'virtualenv']**
  roles:
    - galaxyroject.postgresql
    - role: natefoo.postgresql_objects
      become: true
      become_user: postgres
  **- geerlingguy.pip
    - galaxyproject.galaxy
    - role: uchida.miniconda
      become: true
      become_user: "{{ galaxy_user.name }}"**
```

### Sources
https://training.galaxyproject.org/training-material/topics/admin/tutorials/ansible-galaxy/tutorial.html#log-in-to-galaxy
