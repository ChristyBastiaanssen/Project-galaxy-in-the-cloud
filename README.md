# Galaxy-in-the-cloud-with-a-fair-heart
Project for the Bioinformatics Minor from Avans University of Applied Sciences. The goal of the project is to create a galaxy server in the surfsara reseach cloud. This galaxy will be specified with RNA-sequencing data analysis tool for the analysis of cardio-genetic data. You will have to manage a federated multi-user environment with GDPR-sensitive data and build a ready-to-use cardio-genetic analysis pipeline

## Setting up a federated multi-user environment with GDPR sensitive data. 
![image](https://user-images.githubusercontent.com/80160380/177067198-c0aa2786-5fcb-45cc-a38b-015db66099fa.png)

***Figure 1: Setting up a federated multi-user environment with GDPR-sensitive data.** The flowchart shows the deployment of Galaxy in the SURF research cloud. It starts with the creation of an individual private and public SSH key which will be added to each users SURF research cloud profile. Next a new ubuntu 20.04 workspace will be created which will make use of 4 (virtual) CPU cores and 32GB of RAM. In this VM Ansible will be installed. After Ansible is installed, Galaxy will be installed, as well as PostgreSQL, uWSGI MULES and NGINX. After Galaxy is deployed the RNA-sequencing tools will be installed with Ephemeris.*

## Cardio-genetic RNA sequencing analysis pipeline. 
![image](https://user-images.githubusercontent.com/80160380/168887779-b87bd891-84c1-4d9f-992f-8bbcc45699f1.png)

***Figure 2: RNA-sequencing analysis pipeline.** The flowchart shows the RNA sequencing analysis pipeline. The pipeline starts with a FastQ format file of which the quality will be checked by FastQC and the low-quality reads and adapters will be removed by Cutadapt. Next, the reads are mapped against a reference genome using HISAT2. After mapping, featureCounts will be used to see which genes are active. Limma-Voom will then be used for the identification of the differentially expressed features and Goseq will be used to perform gene ontology analysis. To visualize the results, a heatmap and a volcano-plot will be made. Lastly, all of the obtained data will be combined in one single file by using the MultiQC tool.*
