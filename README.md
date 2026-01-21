# Mitochondrial dysfunction drives progression from acute to Long COVID

## Integrated transcriptomic analysis reveals universal mitochondrial targeting across the COVID-19 disease spectrum

[![DOI](https://img.shields.io/badge/Zenodo-10.5281%2Fzenodo.16751357-blue)](https://doi.org/10.5281/zenodo.16751357)
[![bioRxiv](https://img.shields.io/badge/bioRxiv-10.1101%2F2025.06.18.660454-red)](https://doi.org/10.1101/2025.06.18.660454)

---

## Abstract

This study presents the first comprehensive molecular characterization of the complete COVID-19 pathophysiological spectrum, from health through acute severe infection to post-acute sequelae and mortality. Through integrative analysis of three independent RNA-seq datasets (n=152 samples across eight disease states) processed with a standardized containerized pipeline, we reveal mitochondrial dysfunction as the universal molecular signature of COVID-19. 

Oxidative Phosphorylation (OXPHOS) emerged as the most consistently enriched pathway across disease states, ranking first in five of six comparisons with Enrichr Combined Scores ranging from 6,742 to 10,227. A three-pathway molecular triad—OXPHOS, MYC Targets V1, and mTORC1—demonstrated distinct patterns across disease progression, with fatal cases uniquely exhibiting MYC Targets V1 dominance (Combined Score 173,380,125), representing a metabolic-to-proliferative switch characteristic of irreversible disease progression.

Four critical mitochondrial components (NDUFA1, COX5A, ATP5F1, TOMM20) emerged as shared targets across all three pathways, indicating coordinated viral disruption of cellular bioenergetics rather than collateral inflammatory damage. These findings fundamentally reframe COVID-19 from a respiratory illness with systemic complications to a primary mitochondrial disease with respiratory manifestations, opening new therapeutic avenues targeting cellular bioenergetics for both acute COVID-19 and Long COVID management.

---

## Data Overview

This study integrates three independent RNA-seq datasets capturing the complete COVID-19 pathophysiological spectrum:

| Dataset | Disease States | Notes |
|---------|----------------|-------|
| [Ryan et al. (GSE169687)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE169687) | Healthy controls (n=14)<br>PASC mild (n=98)<br>PASC moderate (n=11)<br>PASC severe (n=14)<br>PASC critical (n=15) | Australia<br>n=152 total<br>Paired-end PBMC |
| [Yin et al. (GSE224615)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE224615) | Recovered without sequelae (n=13)<br>Long COVID (n=23) | United States<br>n=36 total<br>Paired-end PBMC |
| [Vlasov et al. (GSE185863)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE185863) | Acute severe survivors (n=5)<br>Fatal cases (n=3)<br>*Technical replicates: 16 samples from 8 patients* | Russia<br>n=16 total<br>Paired-end PBMC |

**Total samples analyzed**: 152 across eight disease groups  


## Methods Summary

**Pipeline Overview**: Containerized, standardized workflow ensuring reproducible cross-dataset integration

1. **Quality Control**: Trim Galore (v0.6.10) for adapter trimming
2. **Alignment**: STAR (v2.7.11a) to GRCh38 reference genome (Ensembl release 110)
3. **Quantification**: Salmon (v1.10.1) with transcript-level quantification
4. **Differential Expression**: edgeR with FDR <0.05, log2FC >1.25
5. **Pathway Analysis**: GSEA using MSigDB Hallmark gene sets (fgsea R package)

**Reference**: GRCh38 primary assembly, GENCODE annotation release 44  
**Statistical Thresholds**: FDR <0.05, |log2FC| >1.25  
**Pathway Filtering**: Gene sets with 15-500 genes per pathway

## Analysis Notebooks

The following Jupyter notebooks reproduce the analyses from our manuscript. All notebooks are available in our [shared Google Drive folder](https://drive.google.com/drive/folders/1TNfcrKa-jA2k7-o0Q7jRlqaohT-nsT_S).

### Notebooks

1. [A vs B](https://github.com/BioDepot/LongCOVID-RNAseq/blob/main/notebooks/Gene_Counts_A_vs_B(5).ipynb) - Group A vs B: Healthy controls vs. recovered patients with no PASC signs and symptoms (to identify the main post-recovery molecular signatures)
2. [A vs CD](https://github.com/BioDepot/LongCOVID-RNAseq/blob/main/notebooks/Gene_Counts_A_vs_CD.ipynb) - Group A vs C+D: Healthy controls vs. mild/moderate PASC (to help us investigate the dominant gene expression pathways as patients enter the PASC phase)
3. [A vs EF](https://github.com/BioDepot/LongCOVID-RNAseq/blob/main/notebooks/Gene_Counts_A_vs_EF.ipynb) - Group A vs E+F: Healthy controls vs. severe/critical PASC (to characterize the molecular associations differentially expressed genes with severe/critical PASC)
4. [A vs H](https://github.com/BioDepot/LongCOVID-RNAseq/blob/main/notebooks/Gene_Counts_A_vs_H.ipynb) - Group A vs H: Healthy controls vs. acute severe COVID-19 survivors (examining enriched gene pathways around resolution of severe active COVID-19)
5. [A vs I](https://github.com/BioDepot/LongCOVID-RNAseq/blob/main/notebooks/Gene_Counts_A_vs_I.ipynb) - Group A vs I: Healthy controls vs. acute severe COVID-19 fatalities (identifying maximal infection related inflammatory pathway activation secondary to COVID-19)
6. [H vs I](https://drive.google.com/file/d/1uv3ZqAz1nzHCHzcDxqRj-68dW7h5kmdk/view?usp=drive_link) - Group H vs I: Acute severe survivors vs. fatalities (contrasting the dominant gene expression profiles of pathways related to fatality versus near-fatal cases)




