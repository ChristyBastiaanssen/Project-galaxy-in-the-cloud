# Object storage
To add extra storage to the galaxy the following tutorial needs to be followed. 

```open galaxyservers.yml```.


Add the following:
```
galaxy_config:
  galaxy:
    object_store_config_file: "{{galaxy_config_dir}}/object_store_conf.xml"
```

Also add the following: 
```galaxy_config_templates:
  - src: templates/galaxy/config/object_store_conf.xml.j2
    dest: "{{ galaxy_config.galaxy.object_store_config_file }}"
```
<br>
<br>

```nano templates/galaxy/config/object_store_conf.xml.j2``` 

Add the following to the file:
```
<?xml version="1.0"?>
<object_store type="hierarchical">
    <backends>
        <backend id="newdata" type="disk" order="0">
            <files_dir path="/data2" />
            <extra_dir type="job_work" path="/data2/job_work_dir" />
        </backend>
        <backend id="olddata" type="disk" order="1">
            <files_dir path="/data" />
            <extra_dir type="job_work" path="/data/job_work_dir" />
        </backend>
    </backends>
</object_store>
```

Add a pre task in your playbook galaxy.yml file to create the /data2 folder by using the file module, if the /data2 folder already exists, this step can be skipped:
```
    - name: Create the second storage directory
      file:
        owner: galaxy
        group: galaxy
        path: /data2
        state: directory
        mode: '0755'
```
<br>
<br>

Run the playbook and restart galaxy.
```
ansible-playbook galaxy.yml
```


### Sources
https://training.galaxyproject.org/training-material/topics/admin/tutorials/object-store/tutorial.html

