# Galaxy-in-the-cloud-with-a-fair-heart
Project for the Bioinformatics Minor from Avans University of Applied Sciences. The goal of the project is to create a galaxy server in the surfsara reseach cloud. This galaxy will be specified with RNA-sequencing data analysis tool for the analysis of cardio-genetic data. You will have to manage a federated multi-user environment with GDPR-sensitive data and build a ready-to-use cardio-genetic analysis pipeline

## Setting up a federated multi-user environment with GDPR sensitive data. 
![image](https://user-images.githubusercontent.com/80160380/168887376-73f87853-0680-4b83-a05e-ea2dd3d78f75.png)

***Figure 1. Flowchart of the deployment of galaxy server in the SURF research cloud.** It starts with the creation of a own private and public SSH key which will be added to the SURF research cloud profile. Next a new ubuntu 20.04 workspace will be created which will make use of 2 (virtual) CPU cores and 16 GB of RAM. In this VM Ansible will be installed. After Ansible is installed Galaxy will be installed, as well as PostgreSQL, uWSGI MULES and NGINX. At last, multiple galaxy advances will be installed in order to run the workflows.*

## Cardio-genetic RNA sequencing analysis pipeline. 
![image](https://user-images.githubusercontent.com/80160380/168887779-b87bd891-84c1-4d9f-992f-8bbcc45699f1.png)

***Figure 2. Flowchart of the RNA sequencing analysis pipeline.** The pipeline starts with a FastQ format file of which the quality will be checked by FastQC and the low quality reads and adapters will be removed by cutadapt. Next, the reads are mapped against a reference genome using HISAT2. After mapping, featureCounts will be used to see which genes are active. Limma-Voom will then be used for the identification of the differentially expressed features and Goseq will be used to perform gene ontology analysis. To visualise the results, a heatmap and a volcano-plot will be made. Lastly, all of the obtained data will be combined in one single file by using the MultiQC tool.*
