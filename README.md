# Spatial-Neighborhood-Graph-Builder 🧠🔬

A Python tool to generate and analyse spatial interaction graphs between cells in multiplexed imaging data (e.g. MIBI, CODEX). Given cell coordinates from multiplexed imaging datasets, the tool constructs graphs representing spatial neighborhoods, helping to visualize and quantify cell-cell proximity and microenvironmental organization.

---

## 📚 Scientific Background 

**Spatial biology** is revolutionizing our understanding of tissue architecture by enabling researchers to map the localization and interactions of dozens of proteins or RNA molecules at single-cell resolution, directly on the tissue. Technologies like **Multiplexed Ion Beam Imaging (MIBI)** and **CODEX (CO-Detection by Indexing)** generate high-dimensional data that include both cellular phenotypes and spatial positions.
In cancer research, studying how non-cancerous cells (e.g. immune cells, fibroblasts) are distributed around tumor cells or how different cell types form spatial "neighborhoods" can reveal patterns of tumor remodeling and growth. However, this rich spatial information is often underutilized due to a lack of lightweight, accessible tools.

This project presents a Python-based tool that transforms cell coordinate data into an analyzable **spatial graph** using `k-nearest neighbors (k-NN)` or distance thresholds, allowing researchers to explore spatial context and cell-cell interaction landscapes.

## 🚀 What this tool does
