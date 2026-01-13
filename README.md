# BRCA-Hub-Gene-Network
Author: Sounish Singha

# Identification of a 10-Gene Prognostic Hub Signature in Breast Carcinoma

## Project Overview
This study utilizes an integrated bioinformatics approach to identify key molecular drivers of breast carcinoma. By analyzing transcriptomic data from the **GSE10810** dataset, I identified a core signature of 10 hub genes that are significantly upregulated in tumor tissues and strongly correlated with poor patient prognosis.

## Key Findings
* **Hub Gene Identification:** Isolated a 10-gene signature (*MCM4, CCNB2, MAD2L1, SPAG5, NUSAP1, UBE2C, BIRC5, RRM2, BUB1B, PBK*) using the CytoHubba MCC algorithm.
* **Prognostic Validation:** High expression of these hub genes, specifically **UBE2C** and **BIRC5**, correlates with a statistically significant reduction in Relapse-Free Survival (RFS).
* **Clinical Metric:** UBE2C demonstrated a **Hazard Ratio (HR) of 1.84** ($P < 1 \times 10^{-16}$) in a cohort of $n=4929$ patients.



## Methodology
### 1. Data Acquisition & Pre-processing
* **Dataset:** [GSE10810](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE10810) (Affymetrix GPL570 platform).
* **Normalization:** Sample distribution and quality were verified via UMAP and Boxplots.

### 2. Differential Expression Analysis (GEO2R)
* **Tools:** GEO2R (limma-based).
* **Criteria:** Adjusted $P$-value < 0.05 and $|\log FC| > 1.5$.

### 3. Network Construction & Hub Identification
* **PPI Network:** Constructed via the **STRING** database (Medium confidence 0.4).
* **Visualization:** Analyzed in **Cytoscape 3.9.1**.
* **Algorithm:** **Maximal Clique Centrality (MCC)** via the CytoHubba plugin to identify the top 10 bottlenecks in the interactome.



### 4. Survival Analysis (KM Plotter)
* **Platform:** [KM Plotter (Breast Cancer mRNA)](https://kmplot.com/analysis/).
* **Sample Size:** $n=4929$ patients.
* **Metric:** Relapse-Free Survival (RFS).

## Project Structure
BRCA-Hub-Gene-Network/
├── data/
│   ├── raw_GSE10810_data.txt      # The file from GEO2R
│   ├── processed_DEGs.xlsx        # Your Excel file with UP/DOWN sheets
│   └── string_interactions.tsv    # The file from STRING
├── results/
│   ├── volcano_plot.png           # From GEO2R
│   ├── string_network.png         # From STRING
│   └── hub_gene_network.png       # Your Cytoscape Image (The one you made)
├── docs/
│   └── manuscript_draft.pdf       # The paper you are writing
└── README.md                      # The "Landing Page" (See below)
