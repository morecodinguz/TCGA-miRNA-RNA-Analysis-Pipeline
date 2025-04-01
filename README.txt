## Description
This repository provides an automated pipeline for downloading, preprocessing, analyzing, and preparing TCGA (The Cancer Genome Atlas) miRNA and RNA expression data for bioinformatics and machine learning analyses. It specifically targets metastasis classification such as lymph node (LNM) and distant metastasis (DM).

## Pipeline Workflow
- **Data Acquisition:** Downloads RNA and miRNA expression data from TCGA using TCGAbiolinks.
- **Data Preprocessing:**
  - Clinical data cleaning
  - Separation of normal and tumor samples
  - Gene expression normalization (TMM normalization)
- **Correlation Analysis:** Pearson correlation coefficient calculations for miRNA-RNA pairs
- **Statistical Analysis:** Wilcoxon tests to identify significant miRNA-RNA interactions
- **Machine Learning Preparation:** Generation of input datasets ready for predictive modeling

## Requirements

### R Dependencies
Install via CRAN and Bioconductor:

```R
install.packages(c("beepr", "readxl", "dplyr", "DT", "stringr", "doParallel", "data.table", "limma", "psych", "corpcor", "ggplot2", "purrr", "NetworkToolbox", "reticulate", "RMySQL", "reshape2", "spatstat", "gplots", "RColorBrewer", "pROC", "pheatmap", "enrichR", "progress", "tidyr"))

BiocManager::install(c("TCGAbiolinks", "SummarizedExperiment", "edgeR", "miRBaseConverter"))
```

```

## Folder Structure
```
.
├── plots/                # Directory for generated plots
├── target/               # Directory for target databases
├── tcga_data/            # Main directory containing processed data
│   └── [Cancer_Type]/    # Specific cancer datasets (e.g., HNSC)
├── tmp/                  # Temporary files
├── function2.R           # Main R functions for data processing
├── annotation.csv        # Annotation reference file
└── README.md             # Documentation
```

## Output Files
- Normalized and filtered miRNA and RNA expression matrices
- Lists of significant miRNA-RNA correlation pairs
- Final datasets suitable for machine learning (e.g., `ml_input.csv`)

## Notes
- Customize correlation (`pcc_filter`) and statistical test (`wilcox_pval`) thresholds as needed.
- Ensure sufficient computational resources due to the heavy data processing involved.
