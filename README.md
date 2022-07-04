# Galaxy-in-the-cloud-with-a-fair-heart
Project for the Bioinformatics Minor from Avans University of Applied Sciences. The goal of the project is to create a galaxy server in the surfsara reseach cloud. This galaxy will be specified with RNA-sequencing data analysis tool for the analysis of cardio-genetic data. You will have to manage a federated multi-user environment with GDPR-sensitive data and build a ready-to-use cardio-genetic analysis pipeline

This Github page provides the following:
* An overview of the project.
* Tutorials for setting up a Galaxy server with Ansible.
* An RNA-sequencing analysis pipeline.

## Overview of the project.

### Setting up a federated multi-user environment with GDPR sensitive data. 
The first step of building the Galaxy server is the creation of a VM in the SURF research cloud. After the VM is created and can be accessed, Ansible needs to be installed, since Galaxy is depended on Ansible for its deployment. After the installation is complete, a Galaxy server and multiple requirements can be installed with Ansible. These are:
* PostgreSQL for the database
* uWSGI Mules for the processing of Galaxy jobs
* NGINX for automatically compressing selected content, making it easy to apply caching headers to specific types of content and providing authentication. <br>
After the Galaxy server is up and running, the RNA-sequencing tools will be installed with Ephemeris. 
<br>

![image](https://user-images.githubusercontent.com/80160380/177067198-c0aa2786-5fcb-45cc-a38b-015db66099fa.png)

***Figure 1: Setting up a federated multi-user environment with GDPR-sensitive data.** The flowchart shows the deployment of Galaxy in the SURF research cloud. It starts with the creation of an individual private and public SSH key which will be added to each users SURF research cloud profile. Next a new ubuntu 20.04 workspace will be created which will make use of 4 (virtual) CPU cores and 32GB of RAM. In this VM Ansible will be installed. After Ansible is installed, Galaxy will be installed, as well as PostgreSQL, uWSGI MULES and NGINX. After Galaxy is deployed the RNA-sequencing tools will be installed with Ephemeris.*

### Cardio-genetic RNA sequencing analysis pipeline. 
The RNA-sequencing analysis workflow in Galaxy start by downloading and extracting the reads from the input data set in FastQ format by their SRA number. The input data consists of single-reads sequenced with an Illumina HiSeq 2500. 
* The read quality of the FastQ file will be assessed by using FastQC. 
* Next, Cutadapt will find and removes adapter sequences, primers, poly-A tails and other types of unwanted sequence. 
* After the trimming and filtering of the reads, the reads will be mapped against the reference genome, which in this case is GRCh38, by using HISAT2 to figure out where the sequences originated from in the genome.
* To quantify the number of reads mapping to the exons of each gene, featureCounts will be used.
* Limma-voom will then be used for the differential expression analysis. After this, Goseq detects gene ontology and will be used to establish biological pathways and enrichment.
* The results will then be visualized through a heatmap and a volcano-plot.
* Finally, MultiQC will be used to make an overview of the results by creating a report. 
<br>

![image](https://user-images.githubusercontent.com/80160380/168887779-b87bd891-84c1-4d9f-992f-8bbcc45699f1.png)

***Figure 2: RNA-sequencing analysis pipeline.** The flowchart shows the RNA sequencing analysis pipeline. The pipeline starts with a FastQ format file of which the quality will be checked by FastQC and the low-quality reads and adapters will be removed by Cutadapt. Next, the reads are mapped against a reference genome using HISAT2. After mapping, featureCounts will be used to see which genes are active. Limma-Voom will then be used for the identification of the differentially expressed features and Goseq will be used to perform gene ontology analysis. To visualize the results, a heatmap and a volcano-plot will be made. Lastly, all of the obtained data will be combined in one single file by using the MultiQC tool.*
