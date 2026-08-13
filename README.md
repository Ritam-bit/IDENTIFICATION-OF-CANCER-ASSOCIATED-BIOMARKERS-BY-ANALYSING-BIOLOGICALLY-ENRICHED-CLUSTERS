# 🧬 Identification of Cancer-Associated Biomarkers Using Fuzzy Clustering

> **Fuzzy clustering-based analysis of gene expression data for identifying potential cancer-associated biomarkers using the Gustafson-Kessel algorithm.**

## 📌 Project Overview

**Identification of Cancer Associated Biomarkers by Analysing Biologically Enriched Clusters** is a bioinformatics and machine learning project focused on identifying genes that show significant changes between **normal and carcinogenic conditions**.

The project applies the **Gustafson-Kessel (GK) fuzzy clustering algorithm**, which is suitable for gene-expression data containing overlapping and non-spherical cluster structures. Cluster validity indices are used to determine appropriate cluster configurations, followed by membership-score analysis and dynamic thresholding to identify potentially significant genes.

The complete methodology combines **fuzzy clustering, cluster validation, membership analysis, dynamic thresholding, and biological validation**.

---

## 🎯 Objectives

* Analyze high-dimensional gene expression datasets.
* Apply fuzzy clustering to handle overlapping biological patterns.
* Use the Gustafson-Kessel algorithm for adaptive clustering.
* Determine suitable cluster numbers using:

  * Xie-Beni (XB) Index
  * Fukuyama-Sugeno (FS) Index
  * Dunn Index
* Compare gene membership scores between normal and carcinogenic conditions.
* Identify potentially significant cancer-associated genes.
* Validate predicted genes against known cancer-related gene information.

---

## 🔬 Methodology

The project follows the workflow below:

```text
Gene Expression Data
        │
        ▼
Data Preprocessing
        │
        ▼
Min-Max Scaling
        │
        ▼
Optimal Cluster Selection
   (XB + FS + Dunn)
        │
        ▼
Gustafson-Kessel Clustering
        │
        ▼
Membership Matrix Generation
        │
        ▼
Membership Score Difference
        │
        ▼
Dynamic Thresholding
        │
        ▼
Significant Gene Identification
        │
        ▼
Biological Validation
```

The normal and carcinogenic datasets are processed separately before their membership patterns are compared. The GK algorithm uses adaptive distance measures and cluster-specific covariance matrices to model complex gene-expression structures.

---

## 🧠 Key Techniques

### 1. Gustafson-Kessel Fuzzy Clustering

The **Gustafson-Kessel algorithm** is a fuzzy clustering technique that allows genes to have different membership degrees across multiple clusters.

Unlike hard clustering, fuzzy clustering can represent overlapping biological behavior. GK additionally adapts to different cluster shapes using cluster-specific covariance matrices.

This makes it suitable for complex, high-dimensional gene-expression data.

### 2. Cluster Validity Indices

Three validity indices are used to evaluate clustering quality:

| Index                    | Purpose                                                    | Better Value |
| ------------------------ | ---------------------------------------------------------- | ------------ |
| **Xie-Beni (XB)**        | Measures compactness and separation                        | Lower        |
| **Fukuyama-Sugeno (FS)** | Evaluates intra-cluster compactness and cluster dispersion | Lower        |
| **Dunn Index**           | Measures separation relative to cluster spread             | Higher       |

These indices are used to determine an appropriate number of clusters for the datasets.

### 3. Membership Score Analysis

After clustering the normal and carcinogenic datasets, membership matrices are compared for each gene.

For each gene, the maximum absolute difference in membership scores is calculated:

```text
Δuᵢ = max |uᵢⱼ(cancer) − uᵢⱼ(normal)|
```

A larger membership difference indicates a stronger change in the gene's cluster-association behavior between the two conditions.

### 4. Dynamic Thresholding

Instead of using an arbitrary fixed threshold, the project determines a data-driven threshold from the distribution of membership-score differences.

The reported implementation uses:

```text
Threshold = Mean(Δu) + 2 × Standard Deviation(Δu)
```

Genes with membership differences above the threshold are selected for further analysis.

---

## 📊 Datasets

The project evaluates two microarray gene-expression datasets:

| Dataset         |  Genes | Normal Samples | Carcinogenic Samples |
| --------------- | -----: | -------------: | -------------------: |
| **Lung Cancer** |  7,129 |             10 |                   86 |
| **Leukemia**    | 22,397 |             13 |                   43 |

The experiments consist of preprocessing, clustering, validity evaluation, membership-score analysis, and biological validation.

---

## 📈 Optimal Number of Clusters

The clustering process was evaluated across multiple cluster configurations using the three validity indices.

| Dataset  | Condition    | Optimal Clusters |
| -------- | ------------ | ---------------: |
| Lung     | Normal       |            **3** |
| Lung     | Carcinogenic |            **8** |
| Leukemia | Normal       |            **3** |
| Leukemia | Carcinogenic |           **14** |

The selected configurations were subsequently used for the GK clustering analysis.

---

## 🧪 Results

The membership-score analysis identified:

* **220 significant genes** from the lung cancer dataset.
* **1,100 significant genes** from the leukemia dataset.

### Biological Validation

The predicted genes were compared with a curated reference list of known cancer-associated genes and aliases obtained from the **NCBI gene database**.

Reported validation results include:

* **Lung:** 220 predicted genes, with **131 matching known cancer-related genes**.
* **Leukemia:** 1,100 predicted genes, with **200 evaluated and 113 matching known genes**.

### Example Identified Genes

**Lung Cancer**

```text
PLAB
AQP3
LGALS4
AKR1C3
PTGS2
ANXA2
TFPI2
TOB1
S100A6
ID1
```

**Leukemia**

```text
TRIP12
SMARCD2
MAPK14
ABCC1
LPHN1
TPMT
RUNX3
PIGF
SPI1
IL8
```

These genes were identified through unsupervised membership-score analysis and subsequently evaluated using biological reference information.

---

## 📊 Visualizations

The project includes visual analysis of:

* Xie-Beni Index
* Fukuyama-Sugeno Index
* Dunn Index
* Gustafson-Kessel clustering
* Normal vs. carcinogenic cluster structures
* Membership-score distributions
* Dynamic thresholds
* Comparison of clustering approaches

The project report contains separate clustering and validity visualizations for both lung cancer and leukemia datasets.

---

## 💡 Why Fuzzy Clustering?

Gene-expression data can contain overlapping biological patterns, where a gene may participate in multiple biological pathways or regulatory processes.

Hard clustering forces every gene into a single cluster. Fuzzy clustering instead assigns **membership scores across multiple clusters**, allowing the model to represent biological uncertainty and overlapping behavior.

The Gustafson-Kessel algorithm further improves this by adapting to non-spherical cluster structures.

---

## 🛠️ Technologies & Tools

* **Python**
* **Jupyter Notebook**
* **NumPy**
* **Pandas**
* **Matplotlib**
* **Scikit-learn**
* **Fuzzy Clustering**
* **Gustafson-Kessel Algorithm**
* **PCA**
* **Bioinformatics / Gene Expression Analysis**
* **NCBI Gene Database**

---

## 📁 Repository Structure

The repository currently contains:

```text
IDENTIFICATION-OF-CANCER-ASSOCIATED-BIOMARKERS/
│
├── Final_year_project_Leukemia.ipynb
├── Ritam FINAL YEAR PROJECT-2025.pdf
└── README.md
```

The Jupyter Notebook contains the project analysis, while the PDF contains the complete final-year project report.

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/Ritam-bit/IDENTIFICATION-OF-CANCER-ASSOCIATED-BIOMARKERS-BY-ANALYSING-BIOLOGICALLY-ENRICHED-CLUSTERS.git
```

### 2. Navigate to the project

```bash
cd IDENTIFICATION-OF-CANCER-ASSOCIATED-BIOMARKERS-BY-ANALYSING-BIOLOGICALLY-ENRICHED-CLUSTERS
```

### 3. Open the Jupyter Notebook

```bash
jupyter notebook Final_year_project_Leukemia.ipynb
```

Run the notebook cells sequentially to reproduce the analysis available in the repository.

---

## 📚 Research Reference

The research discussion and development of the project methodology can be found here:

**[Cancer Biomarker Presentation Guide – Project Research](https://chatgpt.com/share/684fa8d7-0210-800f-bfc5-c700ad7e2e14)**

---

## 📄 Project Report

The complete final-year project report is included in this repository:

**Identification of Cancer Associated Biomarkers by Analysing Biologically Enriched Clusters**

The project was completed as part of the **B.Tech in Information Technology** program at **Meghnad Saha Institute of Technology** under the supervision of **Prof. Subir Hazra**.

---

## ⚠️ Disclaimer

This project is intended for **academic and research purposes**.

The identified genes represent potential cancer-associated biomarkers based on computational analysis and biological validation. They should **not** be considered clinically validated diagnostic or therapeutic biomarkers without further experimental and clinical validation.

---

## 👨‍💻 Author

**Ritam Nath**

B.Tech – Information Technology
Meghnad Saha Institute of Technology
2025

---

## ⭐ Project Highlights

* 🧬 Gene expression analysis
* 🧠 Gustafson-Kessel fuzzy clustering
* 📊 Multiple cluster validity indices
* 🔍 Membership-score analysis
* 📈 Dynamic thresholding
* 🧪 Biological validation
* 🫁 Lung cancer analysis
* 🩸 Leukemia analysis
* 💻 Python & Jupyter Notebook
* 🔬 Bioinformatics-based biomarker discovery
