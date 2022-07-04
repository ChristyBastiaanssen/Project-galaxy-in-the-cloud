# Installing reference data with CVMFS
This tutorial shows how to make the reference data publicly available to all users.
<br>

```Open requirements.yml```

Add the following:
```
- src: galaxyproject.cvmfs
  version: 0.2.13
```

Install the added requirement:
```
ansible-galaxy install -p roles -r requirements.yml
```
<br>

```open group_vars/all.yml```

Add the following:
```
# CVMFS vars
cvmfs_role: client
galaxy_cvmfs_repos_enabled: config-repo
cvmfs_quota_limit: 500
```
<br>

```open galaxy.yml```

Add the following under ```roles```:
```
    - galaxyproject.cvmfs
```
<br>

Run the playbook:
```
ansible-playbook galaxy.yml 
```


### Sources
https://training.galaxyproject.org/training-material/topics/admin/tutorials/cvmfs/tutorial.html
