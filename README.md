# 🧠 TissueGraph: Spatial Graphs for Tissue Microenvironments 🔬

**TissueGraph** is a Python tool designed to explore and visualize spatial organization in tissue samples from multiplexed imaging technologies (e.g. MIBI, CODEX). Given cell coordinates from multiplexed imaging datasets, the tool constructs graphs representing spatial neighborhoods, helping to visualize and quantify cell-cell proximity and microenvironmental organization.

---

## 📚 Scientific Background 🧬

**Spatial biology** is revolutionizing our understanding of tissue architecture by enabling researchers to map the localization and interactions of dozens of proteins or RNA molecules at single-cell resolution, directly on the tissue. Technologies like **Multiplexed Ion Beam Imaging (MIBI)** and **CODEX (CO-Detection by Indexing)** generate high-dimensional data that include both cellular phenotypes and spatial positions.
In cancer research, studying how non-cancerous cells (e.g. immune cells, fibroblasts) are distributed around tumor cells or how different cell types form spatial "neighborhoods" can reveal patterns of tumor remodeling and growth. However, the complexity of high-resolution datasets makes visual interpretation and analysis challenging.

**TissueGraph** offers three core strategies to simplify and analyze spatial organization: 

--- 

## 💡 Features 🚀

### 1️⃣ Super-node Graphs from Cell Neighborhoods

- Groups nearby cells into spatial **neighborhoods** using DBSCAN (Density-Based Spatial Clustering of Applications with Noise) or a fixed-radius method.
- Each neighborhood becomes a **super-node** in the graph.
- Edges connect neighborhoods that are spatially adjacent (e.g., within a threshold distance).
- Ideal for visualizing high-level structure across large tissue sections or tumor compartments.

---

### 2️⃣ Cell-level Graphs with Participation-Based Node Sizes 

- Each node represents a **single cell**.
- Cell are grouped into neighborhoods.
- Node size or label shows **how many neighborhoods** a cell belongs to.
- Helps detecting cells involved in multiple compartments. 

---

### 3️⃣ Barycentric Plots based on Neighborhood Relationships

- Shows how each **cell is positioned relative to nearby spatial neighborhoods** (clusters of cells).
- Using cluster centroids, the tool generates **barycentric-like plots** that represent how close a cell is to each sorrounding neighborhood.
- Helps detecting cells that are phisically embedded, offset or at the interface between regions
  
---

## ▶️ How to Run

To run the tool from command line:

```bash
python tissuegraph.py --input_csv my_data.csv --output_dir results/
```

Optional arguments:

- `--input_csv`: Path to CSV with cell centroids.
- `--input_mask`: Alternatively, use a labeled segmentation mask (e.g. TIFF).
- `--group_mode`: Enables super-node graph construction via DBSCAN.
- `--eps`: DBSCAN neighborhood distance (default: 30).
- `--min_samples`: Minimum samples for DBSCAN clustering (default: 5).
- `--participation`: Builds the cell-level graph with participation metric.
- `--radius`: Distance threshold for participation graphs (default: 20).
- `--barycentric`: Activates barycentric plot generation.
- `--output_dir`: Output directory for saving figures and results.

Example using a mask:

```bash
python tissuegraph.py --input_mask path/to/mask.tif --group_mode --participation --barycentric --output_dir results/
```

---

## 📥 Input Format ⬇️

The tool expects a CSV file with the following fields:

| Column Name   | Description                              |
|---------------|------------------------------------------|
| `Cell_ID`     | Unique identifier for each cell          |
| `X`, `Y`      | (Optional) 2D coordinates of each cell in microns   |
| `Cell_Type`   | (Optional) Biological annotation         |
| `Region_Label`| (Optional) Region identifier (e.g., Core) |

---

## 📤 Output Files ⬆️

- `supernode_graph.png`: Graph of neighborhoods (1 node = 1 group of cells)
- `cell_graph_participation.png`: Cell graph with labels showing how many neighborhoods each cell belongs to
- `barycentric_plot.png`: Barycentric visualization showing spatial position of each cell relative to nearby neighborhoods 
- `neighborhood_graph.gml`: GraphML file for interactive exploration
- `graph_summary.csv`: Table of graph stats (e.g. neighbors, centrality, participation)

---

## ⚙️ Installation 🧑‍💻

```bash
git clone https://github.com/carra99/tissuegraph.git
cd tissuegraph
pip install -r requirements.txt
```

Dependencies:
- `pandas`, `numpy`, `networkx`, `scipy`, `matplotlib`
- Optional: `seaborn`, `scikit-learn`

---

## 🧠 Use Cases 🧪

- Visualizing **microenvironments** in tumors
- Comparing **spatial architecture** across patient samples
- Identifying **hub** or **bridging** cells in complex tissues

---

## 📎 Links

This tool was developed as a final project for the course [WIS Python Course – March 2025](https://github.com/code-Maven/wis-python-course-2025-03).
