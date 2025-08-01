# Included Salmon STAR RNA-Seq Workflows

![alt text](../../doc/images/salmon_workflow.png)

Workflow using STAR aligner and Salmon quantification based on the [star_salmon_short workflow from the morphic-rna-seq repo](https://github.com/BioDepot/morphic-rna-seq).

Fives sets of workflows are provided; one is a general template ("generalized") and the remaining four use the template to run data processing for the four studies datasets.

## Generalized workflow

The main Salmon RNA-Seq workflow to handle COVID data processing. Reference files and genome & transcriptome are prepared first. FASTQ files from SRA are downloaded and trimmed with Trim Galore. Trimmed FASTQ files are aligned with STAR Aligner to get aligned BAM files, one for genome and another with transcriptome coordinates. The transcriptome BAM file is used in Salmon quant to obtain both genome and transcriptome-level counts. All counts are then formatted into spreadsheets for downstream analysis.

The other four workflows in this directory is built from this generalized workflow to process their own sets of data. 

## [1] Ryan et al. Workflow

Ryan FJ, Hope CM, Masavuli MG, Lynn MA et al. Long-term perturbation of the peripheral immune system months after SARS-CoV-2 infection. BMC Med 2022 Jan 14;20(1):26. PMID: 35027067 ([GEO link](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE169687))

There are 152 samples taken from the Ryan et al. dataset. These samples have "disease_severity" of Healthy or Mild (COVID), samples classified as Moderate, Severe, or Critical in that category are filtered out.

## [2] Yin et al. Workflow

Yin K, Peluso MJ, Luo X, Thomas R et al. Long COVID manifests with T cell dysregulation, inflammation and an uncoordinated adaptive immune response to SARS-CoV-2. Nat Immunol 2024 Feb;25(2):218-225. PMID: 38212464 ([GEO link](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE224615))

There are 36 samples taken from the Yin et al. dataset, either long COVID or non-long COVID.

## [3] Vlasov et al. Workflow

Vlasov I, Panteleeva A, Usenko T, Nikolaev M et al. Transcriptomic Profiles Reveal Downregulation of Low-Density Lipoprotein Particle Receptor Pathway Activity in Patients Surviving Severe COVID-19. Cells 2021 Dec 10;10(12). PMID: 34944005 ([GEO link](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE185863))

There are 16 samples taken from the Vlasov et al. dataset, blood samples from either deceased COVID patients or surviving COVID patients.