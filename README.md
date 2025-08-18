# Uncovering the Pathophysiological Pattern of Expression from Integrated Analysis across Uniformly Processed RNA Sequencing COVID-19 Datasets  

## Pre-print https://www.biorxiv.org/content/10.1101/2025.06.18.660454v1

## Abstract

This study presents the first comprehensive molecular characterization of the complete COVID-19 pathophysiological spectrum, from health through acute severe infection to post-acute sequelae and mortality. Through integrative analysis of three independent RNA-seq datasets (n=142 samples) processed with a standardized pipeline, we reveal molecular dichotomies between disease phases. **Acute severe COVID-19 shows predominant TNF-α/NF-κB pathway enrichment (cytokine storm), while PASC exhibits dominant Myc Targets and Oxidative Phosphorylation pathway activation (metabolic dysregulation)**. These findings establish objective molecular biomarkers for precision diagnosis and potential phase-appropriate therapeutic targeting.

## Key Findings

- **Acute severe COVID-19**: Dominated by TNF-α signaling via NF-κB pathways (NES >2.5, FDR <0.001)
- **Post-acute sequelae (PASC)**: Characterized by Myc Targets V1 and Oxidative Phosphorylation enrichment (NES >2.2, FDR <0.005)
- **Clinical Translation**: Pathway signatures enable objective biomarker-based disease classification, moving beyond symptom-based diagnosis and toward precision medicine.

## Data Overview

| Dataset | Origin | Samples | Conditions | Sequencing |
|---------|---------|---------|------------|------------|
| Ryan et al. | Australia | n=69 + 14 controls | Healthy controls, PASC (mild/moderate/severe/critical) | Paired-end, PBMC |
| Yin et al. | USA | n=43 | Long COVID vs. recovered (no sequelae) | Paired-end, PBMC |
| Vlasov et al. | Russia | n=16 | Acute severe COVID-19 (survivors vs. fatalities) | Paired-end, PBMC |

**Total samples**: 142 across complete disease spectrum  
**Geographic diversity**: Three continents  
**Sample type**: Peripheral blood mononuclear cells (PBMC)  
**Data availability**: NCBI GEO (**Ryan et al.**: [GSE169687](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE169687), **Yin et al.**: [GSE224615](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE224615), **Vlasov et al.**: [GSE185863](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE185863))

## Repository Structure

```

```

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

## Key Results

### Data Processing Output Dataset

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.16751357.svg)](https://doi.org/10.5281/zenodo.16751357)

### Primary Molecular Signatures

1. **TNF-α/NF-κB Dominance in Acute Disease**
   - Enriched pathways: TNF-α signaling via NF-κB, Inflammatory response
   - Key genes: IL-6, TNF-α, BCL2 family
   - Clinical correlation: Cytokine storm, multi-organ dysfunction

2. **Metabolic Dysregulation in PASC**
   - Enriched pathways: Myc Targets V1, Oxidative Phosphorylation
   - Key genes: CCND2, LDHA, RPL family
   - Clinical correlation: Chronic fatigue, post-exertional malaise

### Clinical Significance

- **Diagnostic Biomarkers**: Pathway signatures distinguish disease phases objectively
- **Prognostic Value**: TNF-α signatures predict severe disease progression
- **Therapeutic Implications**: Phase-specific treatment strategies (anti-inflammatory vs. metabolic support)

## Software Requirements

### Core Dependencies
- **R** (≥4.1.0)
  - edgeR (≥3.36.0)
  - fgsea (≥1.20.0)
  - DESeq2 (≥1.34.0)
- **Command Line Tools**
  - STAR (v2.7.11a)
  - Salmon (v1.10.1)
  - Trim Galore (v0.6.10)
  - SRA Toolkit (≥3.0.0)
