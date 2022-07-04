# Installing tools with Ephemeris

## Installing Ephemeris
This tutorial shows how to easily install a list of tools at once into the Galaxy server by using Ephemeris. <br>

To install Ephemeris ```virtualenv``` must be installed. In Ubuntu this can be done with the following command: ```sudo apt install virtualenv```


A virtual environment needs to be created for Ephemeris: <br>
```
virtualenv -p python3 python3 ~/ephemeris_venv
```

After this the environment needs to be activated and Ephemeris needs to be installed: <br>
```
. ~/ephemeris_venv/bin/activate
pip install ephemeris
```

## Extracting tools
The required tools, in this case the RNA sequencing tools, can be extracted from a workflow. This is done as follows:
``` 
workflow-to-tools -w Galaxy-Workflow-RNA-seq-Galaxy-with-a-heart.ga -o workflow_tools.yml -l RNA-seq
```

## Installing tools
For the installation of the tools the URL of the Galaxy server and an API key for the account are required, where the account must be an admin. 

Ephemeris can now be used to install the tools.
```
shed-tools install -g https://your-galaxy -a <api-key> -t workflow_tools.yml
```

### Sources
https://training.galaxyproject.org/training-material/topics/admin/tutorials/tool-management/tutorial.html

