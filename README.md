# Identification of Cancer-Associated Biomarkers Using Fuzzy Clustering

## 📌 Project Overview

**Identification of Cancer Associated Biomarkers by Analysing Biologically Enriched Clusters** is a bioinformatics and machine learning project that aims to identify genes potentially associated with cancer by analyzing gene expression data from normal and carcinogenic states.

The project uses the **Gustafson-Kessel (GK) fuzzy clustering algorithm** to handle overlapping and non-spherical gene-expression patterns. Cluster validity indices and membership-score analysis are then used to determine meaningful clusters and identify genes showing significant changes between normal and cancerous conditions.

## 🎯 Objectives

* Analyze high-dimensional gene expression datasets.
* Apply fuzzy clustering to account for overlapping biological patterns.
* Use the **Gustafson-Kessel algorithm** for adaptive, non-spherical clustering.
* Determine suitable cluster numbers using:

  * Xie-Beni (XB) Index
  * Fukuyama-Sugeno (FS) Index
  * Dunn Index
* Compare membership scores between normal and carcinogenic conditions.
* Identify potentially significant cancer-associated genes using dynamic thresholding.
* Validate identified genes against known cancer-related gene information.

## 🧬 Methodology

The overall workflow consists of:

```text
Gene Expression Data
        ↓
Data Preprocessing
        ↓
Min-Max Scaling
        ↓
Optimal Cluster Selection
(XB + FS + Dunn)
        ↓
Gustafson-Kessel Clustering
        ↓
Membership Matrix Generation
        ↓
Membership Score Difference
        ↓
Dynamic Thresholding
        ↓
Significant Gene Identification
        ↓
Biological Validation
```

The datasets are separately analyzed for normal and carcinogenic conditions. The GK algorithm uses adaptive distance measures and cluster-specific covariance matrices to model complex cluster structures.

## 🔬 Key Techniques

### Gustafson-Kessel Clustering

GK is a fuzzy clustering technique that allows each gene to have different membership degrees across clusters. Unlike conventional hard clustering, it can represent overlapping biological behavior and adapt to non-spherical cluster structures.

### Cluster Validity Indices

Three validity indices are used to determine suitable clustering configurations:

* **Xie-Beni (XB):** Lower values indicate better compactness and separation.
* **Fukuyama-Sugeno (FS):** Lower values indicate better clustering quality.
* **Dunn Index:** Higher values indicate better separation and compactness.

### Membership Score Analysis

For every gene, the maximum absolute difference between membership scores in normal and carcinogenic conditions is calculated.

Genes with sufficiently large membership changes are considered potential cancer-associated biomarkers.

### Dynamic Thresholding

Instead of relying on a fixed threshold, the project uses a data-driven threshold based on the distribution of membership-score differences.

In the reported implementation:

```text
Threshold = Mean(Δu) + 2 × Standard Deviation(Δu)
```

Genes whose membership-score difference exceeds the threshold are selected for further validation.

## 📊 Datasets

The project evaluates two microarray gene-expression datasets:

| Dataset     |  Genes | Normal Samples | Carcinogenic Samples |
| ----------- | -----: | -------------: | -------------------: |
| Lung Cancer |  7,129 |             10 |                   86 |
| Leukemia    | 22,397 |             13 |                   43 |

The experiments use gene expression data containing normal and carcinogenic samples.

## 📈 Optimal Clusters

The reported experiments evaluated multiple cluster configurations using the validity indices.

| Dataset  | Condition    | Optimal Clusters |
| -------- | ------------ | ---------------: |
| Lung     | Normal       |                3 |
| Lung     | Carcinogenic |                8 |
| Leukemia | Normal       |                3 |
| Leukemia | Carcinogenic |               14 |

The GK algorithm was then applied using the selected clustering configurations.

## 🧪 Results

The membership-score analysis identified:

* **220 significant genes** from the lung cancer dataset.
* **1,100 significant genes** from the leukemia dataset.

Biological validation was performed by comparing predicted genes against known cancer-associated genes and their aliases. The report states that **131 of the 220 lung genes** matched known cancer-related genes, while the leukemia analysis reported **113 matches among 200 evaluated genes**.

Examples of identified genes include:

**Lung Cancer:**

* PLAB
* AQP3
* LGALS4
* AKR1C3
* PTGS2
* ANXA2
* TFPI2
* TOB1
* S100A6
* ID1

**Leukemia:**

* TRIP12
* SMARCD2
* MAPK14
* ABCC1
* LPHN1
* TPMT
* RUNX3
* PIGF
* SPI1
* IL8

The report notes that the gene selection was unsupervised and based on expression dynamics and membership shifts, followed by biological validation.

## 📊 Visualizations

The project generates visualizations for:

* Cluster validity indices
* GK clustering results
* Normal vs. carcinogenic cluster structures
* Membership-score distributions
* Dynamic thresholds
* Comparison of clustering approaches

The project report includes separate clustering and validity visualizations for both lung cancer and leukemia datasets.

## 🔍 Why Fuzzy Clustering?

Gene expression data can contain overlapping biological patterns where a gene may participate in multiple pathways or regulatory processes. Fuzzy clustering represents this behavior by assigning membership values to multiple clusters rather than forcing each gene into a single cluster.

The GK algorithm further improves flexibility by adapting to different cluster shapes through cluster-specific covariance matrices.

## 🚀 Applications

This framework can support research in:

* Cancer biomarker discovery
* Gene expression analysis
* Cancer genomics
* Bioinformatics
* Computational biology
* Personalized medicine research
* Identification of potential therapeutic targets

## 📁 Suggested Project Structure

```text
Cancer-Biomarker-Fuzzy-Clustering/
│
├── data/
│   ├── lung/
│   └── leukemia/
│
├── notebooks/
│   └── analysis.ipynb
│
├── src/
│   ├── preprocessing/
│   ├── clustering/
│   ├── validity_indices/
│   ├── membership_analysis/
│   └── validation/
│
├── results/
│   ├── clusters/
│   ├── validity_indices/
│   ├── membership_scores/
│   └── identified_genes/
│
├── visualizations/
│
├── requirements.txt
├── README.md
└── LICENSE
```

> **Note:** Adjust the folder structure above to match the actual files you upload to GitHub.

## ⚠️ Disclaimer

This project is intended for **academic and research purposes**. The identified genes represent potential cancer-associated biomarkers based on computational analysis and biological validation. They should not be interpreted as clinically validated diagnostic or therapeutic markers without further experimental and clinical validation.

## 👨‍💻 Author

**Ritam Nath**
B.Tech – Information Technology
Meghnad Saha Institute of Technology
2025

## 📚 Project Report

This repository is based on the final-year project:

**"Identification of Cancer Associated Biomarkers by Analysing Biologically Enriched Clusters"**

The project was completed under the supervision of **Prof. Subir Hazra**, Department of Information Technology, Meghnad Saha Institute of Technology.
