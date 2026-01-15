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

## Key Findings

### Universal Mitochondrial Dysfunction
* **OXPHOS Dominance**: Oxidative Phosphorylation ranked as the #1 enriched pathway in 5 of 6 disease comparisons (Enrichr Combined Scores: 6,742-10,227)
* **Exclusive Mitochondrial Signature**: OXPHOS is the exclusive domain of mitochondria in eukaryotic cells, providing molecular evidence that mitochondrial dysfunction is the most robust signature across the COVID-19 continuum

### Three-Pathway Molecular Triad
* **Consistent Ranking**: OXPHOS, MYC Targets V1, and mTORC1 consistently ranked as the top 3 enriched pathways across all six comparisons
* **Disease Progression Patterns**: 
  - Recovery (no Long COVID): Lowest mTORC1 activity (Combined Score 283.43), highest OXPHOS/MYC ratio (4.7)
  - Long COVID: Progressive OXPHOS dysfunction (Combined Scores 7,504-9,164)
  - Fatal cases: MYC Targets V1 dominance (Combined Score 173,380,125)

### Fatal Transition: Metabolic-to-Proliferative Switch
* **Unique MYC Dominance**: Fatal cases were the only comparison where MYC Targets V1 displaced OXPHOS as the top pathway
* **Five-Order-of-Magnitude Shift**: MYC enrichment in fatal vs. survivor comparison represents qualitative shift from metabolic to proliferative dysregulation
* **Complete Cellular Control Breakdown**: Accompanied by cell cycle pathway dysregulation (G2-M Checkpoint, E2F Targets)

### Critical Mitochondrial Targets
* **Four Shared Genes**: NDUFA1 (Complex I), COX5A (Complex IV), ATP5F1 (ATP synthase), TOMM20 (mitochondrial import)
* **Coordinated Disruption**: Presence across all three pathways indicates targeted viral hijacking of cellular bioenergetics
* **Mechanistic Specificity**: Points to primary pathophysiological mechanism rather than passive inflammatory complications

### Clinical Translation
* **Objective Long COVID Diagnosis**: Pathway signatures provide quantitative molecular criteria beyond subjective symptom reporting
* **Prognostic Stratification**: Pathway patterns distinguish recovery, persistent dysfunction, and fatal outcomes
* **Therapeutic Targets**: mTORC1 modulation for Long COVID; MYC pathway inhibition for critically ill patients
* **Mitochondrial Function Testing**: Foundation for objective diagnostic test analogous to pulmonary or liver function tests

---

## Data Overview

| Dataset | Origin | Samples | Conditions | Sequencing |
|---------|---------|---------|------------|------------|
| [Ryan et al. (GSE169687)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE169687) | Australia | n=69 + 14 controls | Healthy controls, PASC (mild/moderate/severe/critical) | Paired-end, PBMC |
| [Yin et al. (GSE224615)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE224615) | USA | n=43 | Long COVID vs. recovered (no sequelae) | Paired-end, PBMC |
| [Vlasov et al.(GSE185863)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE185863) | Russia | n=16 | Acute severe COVID-19 (survivors vs. fatalities) | Paired-end, PBMC |

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

### Table 1. Three-Pathway Molecular Triad Enrichment Scores

| Comparison | Description | OXPHOS | MYC Targets V1 | mTORC1 |
|------------|-------------|--------|----------------|---------|
| **A vs B** | Healthy vs. Recovered | 9,343.63 | 1,997.78 | 283.43 |
| **A vs CD** | Healthy vs. Mild/Moderate PASC | 7,503.93 | 2,232.66 | 646.62 |
| **A vs EF** | Healthy vs. Severe/Critical PASC | 9,164.01 | 2,744.80 | 392.70 |
| **A vs H** | Healthy vs. Acute Survivors | 9,005.45 | 4,260.94 | 340.63 |
| **A vs I** | Healthy vs. Fatal Cases | 10,227.68 | 4,849.22 | 353.53 |
| **H vs I** | Survivors vs. Fatal Cases | 6,742.48 | **173,380,125.4** | 520.12 |

**Key observation**: In five comparisons, ranking was (1) OXPHOS, (2) MYC Targets V1, (3) mTORC1. Only in H vs I did MYC Targets V1 displace OXPHOS, representing the metabolic-to-proliferative switch in fatal outcomes.

### Critical Mitochondrial Genes (Shared Across All Three Pathways)

1. **NDUFA1** - NADH dehydrogenase (Complex I) - Essential for electron transport chain
2. **COX5A** - Cytochrome c oxidase (Complex IV) - Terminal enzyme in cellular respiration  
3. **ATP5F1** - ATP synthase - ATP production machinery
4. **TOMM20** - Translocase of outer mitochondrial membrane - Protein import

These four genes represent core mitochondrial machinery essential for cellular bioenergetics, and their consistent dysregulation underscores fundamental mitochondrial dysfunction across COVID-19.

### Clinical Significance

#### Diagnostic Applications
- **Objective Long COVID Diagnosis**: Quantitative pathway signatures replace subjective symptom-based criteria
- **Disease Phase Classification**: Molecular markers distinguish acute severe, recovery, and persistent sequelae
- **Prognostic Stratification**: Pathway patterns predict disease trajectory before clinical deterioration

#### Therapeutic Implications
- **mTORC1 Modulation**: Potential treatment target for Long COVID based on recovery signature
- **MYC Pathway Inhibition**: Life-saving intervention for critically ill patients showing proliferative switch
- **Mitochondrial Support**: Restoration of cellular bioenergetics as therapeutic strategy
- **Precision Medicine**: Patient stratification for targeted interventions


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
