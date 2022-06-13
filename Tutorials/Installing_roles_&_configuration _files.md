# Requirements
The first ting to do when connected to the VM is to install the needed dependencies. <br>
This will be done as followed.

## Installing roles
(In the home folder) <br>
```mkdir galaxy``` <br>
```cd galaxy``` <br>

Create a new file in the working directory called 'requirements.yml'. <br>
```nano requirements.yml```

Add the following to the file:
```
- src: galaxyproject.galaxy
  version: 0.9.16
- src: galaxyproject.nginx
  version: 0.7.0
- src: galaxyproject.postgresql
  version: 1.0.3
- src: natefoo.postgresql_objects
  version: 1.1
- src: geerlingguy.pip
  version: 2.0.0
- src: uchida.miniconda
  version: 0.3.0
- src: usegalaxy_eu.certbot
  version: 0.1.5
```

Install the requirements by running ```ansible-galaxy install -p roles -r requirements.yml```


## Configuration files
Create a new file in the working directory (the previously made 'galaxy' directory) called 'ansible.cfg'. <br>
```nano ansible.cfg```

Add the following to the file:
```
[defaults]
interpreter_python = /usr/bin/python3
inventory = hosts
retry_files_enabled = false
```

When connecting over SSH add the following to the file: 
```
[ssh_connection]
pipelining = true
```

Create a new file in the working directory called 'hosts'. <br>
```nano hosts```

Add the following to the file:
```
[galaxyservers]
X* ansible_connection=local ansible_user=ubuntu
```

For 'X' state the web-url or IP adress of the host were Galaxy will be installed. 

### Sources <br>
https://training.galaxyproject.org/training-material/topics/admin/tutorials/ansible-galaxy/tutorial.html#requirements 
