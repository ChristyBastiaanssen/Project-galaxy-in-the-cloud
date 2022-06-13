#Required dependencies 
The first ting to do when connected to the VM is to install the needed dependencies.

The first step of installing the dependencies is to create a new directory called ```galaxy``` in the home folder.
After this ```cd``` in that directory. 
Create a new file called ```requirements.yml``` in the working directory and include the following contents:

```
requirements.yml
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
