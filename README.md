# DRUGseq-Pipeline
# Author: Muralidharan Mani
# Affiliation: University of Wisconsin-Madison
DRUGseq-Bioinformatics-Pipeline
 DRUG-seq Data Analysis Pipeline

## Overview
This repository contains a comprehensive pipeline for analyzing DRUG-seq data using R, incorporating tools such as Seurat for single-cell analysis and DESeq2 for differential expression analysis. The pipeline includes steps for data loading, quality control, normalization, differential gene expression analysis, pathway enrichment analysis, and optional drug response prediction.

## Table of Contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [Data Input](#data-input)
4. [Metadata](#metadata)
5. [Analysis Steps](#analysis-steps)
6. [Visualization](#visualization)
7. [License](#license)
8. [Contact](#contact)

## Installation
Ensure you have R and RStudio installed. Then, install the required packages by running the following code in your R console:

```r
# Setup & Install Required Packages
if (!requireNamespace("BiocManager", quietly = TRUE)) {
    install.packages("BiocManager")
}

# List of required Bioconductor packages
pkgs_bioc <- c("Seurat", "DESeq2", "edgeR", "limma", "clusterProfiler", "org.Hs.eg.db", "NicheNetR")

for (pkg in pkgs_bioc) {
    if (!requireNamespace(pkg, quietly = TRUE)) {
        BiocManager::install(pkg)
    }
}

# List of required CRAN packages
pkgs_cran <- c("tidyverse", "ggplot2", "pheatmap", "viridis", "EnhancedVolcano")

for (pkg in pkgs_cran) {
    if (!requireNamespace(pkg, quietly = TRUE)) {
        install.packages(pkg)
    }
}
Usage
To use the pipeline, load the script in R and follow the prompts. Key sections of the workflow include:

Loading the data from your specified count matrix directory.
Performing quality control on the data.
Normalizing the data and conducting differential expression analysis.
Visualizing differential gene expression results and conducting pathway enrichment analysis.
Optionally using NicheNetR for drug response prediction.
Data Input
Make sure to specify the path to your count matrix directory in the data_dir variable. Replace the placeholder "path/to/counts_matrix/" with your actual path.

Metadata
Metadata can be assigned in two ways:

Option 1: Infer conditions from column names for a simple case.
Option 2: Load from a separate metadata file for complex designs (recommended).
Ensure your metadata file has a column that matches the Seurat object's cell names.

Analysis Steps
The pipeline includes:

Data loading and creation of a Seurat object
Quality control measures including filtering based on metrics such as the number of genes, UMI counts, and percentage of mitochondrial genes
Normalization using SCTransform
Differential gene expression analysis using both Seurat's FindMarkers and DESeq2 for robustness
Pathway enrichment analysis using clusterProfiler
Visualization
The pipeline provides visualizations for:

Volcano plots for differential expression
Heatmaps of top differentially expressed genes
Additional visualizations for quality control metrics
License
This project is licensed under the MIT License - see the LICENSE file for details.

Contact
For any questions, suggestions, or issues, please contact mmani3@wisc.edu.
