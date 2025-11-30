# COVID-19 RNA-seq Reanalysis (GSE152075)

## Author
**Alexandra Gerveni**  
BIOS 658 - Final Project  
Virginia Commonwealth University  
Fall 2025

---

## Project Description

This project reanalyzes the RNA-seq dataset (GSE152075) from Lieberman et al. (2020) to identify differentially expressed genes and enriched biological pathways in COVID-19 patients compared to healthy controls. The analysis was performed using edgeR for differential expression and clusterProfiler for functional enrichment analysis.

---

## Dataset Information

| Item | Details |
|------|---------|
| **GEO Accession** | GSE152075 |
| **Organism** | Homo sapiens |
| **Tissue** | Nasopharyngeal swabs |
| **Total Samples** | 484 |
| **COVID-19 Positive** | 430 |
| **Negative Controls** | 54 |
| **Original Publication** | Lieberman et al. (2020) PLoS Biology |

---

## Data Access

The raw counts matrix can be downloaded from GEO:

1. Go to https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE152075
2. Download `GSE152075_raw_counts_GEO.txt.gz`
3. Unzip and place in the project folder

---

## Repository Contents

| File | Description |
|------|-------------|
| `README.md` | Project description (this file) |
| `manuscript.Gerveni.Rmd` | R Markdown file containing all analysis code and report |
| `manuscript.Gerveni.html` | Compiled HTML report |
| `references.bib` | BibTeX references for citations |

---

## Analysis Pipeline

### 1. Quality Assessment
- Library size distribution (bar plots, box plots)
- Count distribution (density plots)
- Sample correlation heatmap (50 random samples)
- PCA and MDS dimensionality reduction

### 2. Preprocessing
- Filtering lowly expressed genes using filterByExpr (35,784 to 11,284 genes)
- TMM normalization using edgeR

### 3. Batch Effect Correction
- Surrogate Variable Analysis (SVA) - 4 surrogate variables identified
- PCA plots before and after correction
- Hierarchical clustering on top 10% most variable genes (1,128 genes)

### 4. Differential Expression Analysis
- edgeR quasi-likelihood framework
- Design matrix with COVID status + 4 SVA covariates
- Benjamini-Hochberg FDR correction
- Significance threshold: FDR < 0.05 and |log2FC| > 1

### 5. Functional Enrichment Analysis
- **ORA:** Overrepresentation Analysis
- **GSEA:** Gene Set Enrichment Analysis
- **Databases:** GO (BP, MF, CC) and KEGG pathways

---

## Key Findings

### Upregulated in COVID-19:
- Interferon-stimulated genes (IFI44L, OAS2, IFIT1, MX1)
- Defense response to virus
- Type I interferon signaling pathway
- Cytokine-mediated signaling

### Downregulated in COVID-19:
- Ribosomal protein genes (RPS, RPL families)
- Cytoplasmic translation
- Ribosome biogenesis
- Oxidative phosphorylation

**Results are consistent with the original Lieberman et al. (2020) publication.**

---

## Software and Packages

- **R version:** 4.4.1 (2024-06-14)
- **Key packages:**
  - edgeR - Differential expression analysis
  - limma - Batch effect correction
  - sva - Surrogate variable analysis
  - clusterProfiler - Functional enrichment
  - org.Hs.eg.db - Gene ID conversion
  - pheatmap - Heatmaps
  - ggplot2 - Data visualization
  - ggrepel - Label positioning
  - tidyr - Data manipulation
  - enrichplot - Enrichment visualization
  - DOSE - Disease ontology

---

## How to Reproduce

1. Clone this repository
2. Download the data file from GEO (link above)
3. Place GSE152075_raw_counts_GEO.txt in the project folder
4. Open manuscript.Rmd in RStudio
5. Install required packages if needed
6. Knit to HTML

---

## Output Summary

| Analysis | Results |
|----------|---------|
| Genes tested | 11,284 |
| DE genes (FDR < 0.05) | ~6,000 |
| DE genes (FDR < 0.05 and logFC > 1) | ~2,100 |
| Upregulated | ~600 |
| Downregulated | ~1,500 |
| GO BP terms (ORA) | 100+ |
| KEGG pathways (ORA) | 15+ |

---

## References

- Lieberman NA, et al. (2020). In vivo antiviral host transcriptional response to SARS-CoV-2 by viral load, sex, and age. PLoS Biology, 18(9), e3000849.
- Robinson MD, et al. (2010). edgeR: a Bioconductor package for differential expression analysis. Bioinformatics, 26(1), 139-140.
- Yu G, et al. (2012). clusterProfiler: an R package for comparing biological themes among gene clusters. OMICS, 16(5), 284-287.

---

## Contact

GitHub: [@Alex05a](https://github.com/Alex05a)
