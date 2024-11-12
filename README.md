# Single-Cell RNA Sequencing Analysis of Aorta Tissue

## Overview
This project involves the analysis of single-cell RNA sequencing (scRNA-seq) data from aorta tissue using **Scanpy**, a Python-based toolkit for single-cell analysis. The goal is to identify distinct cell populations, annotate clusters with cell types, and explore potential biological insights such as gene expression patterns and cell state transitions.

---

## Objectives
1. **Preprocessing**:
   - Normalize and filter the raw scRNA-seq data to retain high-quality cells and genes.
   - Select highly variable genes and scale the dataset to prepare for downstream analyses.

2. **Clustering and Visualization**:
   - Perform Principal Component Analysis (PCA) to reduce dimensionality.
   - Cluster cells using the Leiden algorithm and visualize them using UMAP.
   - Annotate clusters with known cell types based on marker genes.

3. **Marker Gene Analysis**:
   - Identify genes that are differentially expressed across clusters.
   - Visualize the expression of relevant genes using dot plots and UMAP overlays.

4. **Trajectory and Connectivity Analysis**:
   - Use Partition-based Graph Abstraction (PAGA) to study relationships between clusters.
   - Combine PAGA with UMAP to investigate global transitions and local structures.

---

## Methods and Key Steps

### **1. Preprocessing**
- **Filter Cells and Genes**:
  - Remove cells with fewer than 200 genes and genes expressed in fewer than 3 cells.
- **Normalize and Log Transform**:
  - Scale each cell’s total counts to 10,000 and apply a log transformation.
- **Select Highly Variable Genes**:
  - Identify the top 2,000 highly variable genes.
- **Scale Data**:
  - Standardize the gene expression values to have zero mean and unit variance.

### **2. Clustering and UMAP**
- **Principal Component Analysis (PCA)**:
  - Reduce the dataset to the first 8–15 principal components based on variance explained.
- **Leiden Clustering**:
  - Perform clustering with a resolution of 2, producing fine-grained clusters.
- **UMAP Visualization**:
  - Visualize clusters and cell type annotations in 2D space.

### **3. Marker Gene Analysis**
- **Identify Marker Genes**:
  - Use the `rank_genes_groups` function to identify cluster-specific marker genes.
- **Dot Plot**:
  - Visualize the expression of key genes (e.g., **Pecam1**, **Acta2**, **Col1a1**, **Vwf**) across annotated cell types.

### **4. PAGA and Trajectory Analysis**
- **PAGA Graph**:
  - Construct a connectivity graph to study transitions between clusters.
- **Integrated PAGA and UMAP**:
  - Combine PAGA results with UMAP for a comprehensive visualization of global and local structures.

---

## Key Results
1. **Cell Populations**:
   - Identified distinct cell types, including:
     - **Endothelial cells** (e.g., **Pecam1**, **Vwf**)
     - **Smooth muscle cells** (e.g., **Acta2**)
     - **Fibroblasts** (e.g., **Col1a1**)
     - **Macrophages**, **T cells**, **B cells**, and others.

2. **Marker Genes**:
   - Cluster-specific marker genes were identified, aiding in cell type annotation.
   - Example: Cluster `0` highly expresses **Pecam1**, consistent with endothelial cells.

3. **Cluster Connectivity**:
   - PAGA revealed strong transitions between fibroblasts and smooth muscle cells, suggesting differentiation pathways.

4. **Visualizations**:
   - Generated UMAP plots, dot plots, and PAGA graphs to illustrate cell clustering, connectivity, and marker gene expression.

---

## Next Steps
- Perform pathway enrichment analysis for cluster-specific marker genes to uncover associated biological processes.
- Investigate weakly connected clusters in the PAGA graph for potential rare or novel cell populations.
- Explore temporal dynamics or developmental trajectories, if applicable.

---

## Tools and Libraries
- **Scanpy**: Preprocessing, clustering, and visualization.
- **Python Libraries**:
  - `matplotlib`: Data visualization.
  - `pandas`: Data handling and exporting.
  - `gseapy`: Functional enrichment analysis.

---

## How to Reproduce
1. **Set Up Environment**:
   - Install Python and required libraries:
     ```bash
     pip install scanpy matplotlib pandas
     ```

2. **Run the Analysis**:
   - Download the dataset (e.g., `aorta.h5ad`).
   - Follow the steps outlined in the scripts to preprocess, cluster, and analyze the data.

3. **Explore Results**:
   - View UMAP plots, dot plots, and PAGA graphs.
   - Interpret marker genes and cluster connectivity.

---

## Conclusion
This analysis provides a detailed view of the cellular composition of the aorta, identifying key cell types and their transitions. The results contribute to understanding vascular biology and potential roles of immune and structural cells in the tissue.

Feel free to extend this analysis by incorporating additional datasets or methods for further insights.
