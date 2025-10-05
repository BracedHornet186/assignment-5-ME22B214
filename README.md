# DA5401: A5 – Visualizing Data Veracity Challenges in Multi-Label Classification
**Author:** Yash Purswani\
**Roll Number:** ME22B214

## Overview
This project aims to deepen understanding of the challenges in **real-world multi-label classification** by applying advanced **non-linear dimensionality reduction techniques** (t-SNE and Isomap) on the **Yeast gene expression dataset** (multi-label classification) from the [Mulan repository](http://mulan.sourceforge.net/datasets-mlc.html). 

Through visualization, we investigate **data veracity issues** such as:
- **Noisy or ambiguous labels** (genes spanning multiple categories or misclassified),
- **Outliers** (unusual gene expression profiles),
- **Hard-to-learn samples** (regions where categories are thoroughly mixed).

## Methods

1. **Preprocessing**
 - Load `.arff` dataset into Pandas DataFrame.
 - Split into feature matrix `X` and label matrix `Y`.
 - Create a simplified categorical target for visualization:
   - Two most frequent single-label classes,
   - Most frequent multi-label combination,
   - “Other” for all remaining samples.
 - Standardize features using `StandardScaler`.

2. **t-SNE**
 - Reduce dimensionality to 2D for visualization.
 - Experimented with perplexities (5, 10, 20, 30, 40, 50).
 - Selected **perplexity=30** for best balance of local and global structure.
 - Identified noisy labels, outliers, and hard-to-learn samples using neighborhood statistics.

3. **Isomap**
 - Reduced dimensionality to 2D using manifold learning.
 - Compared with t-SNE in terms of **global vs local structure preservation**.
 - Discussed manifold curvature and implications for classification.

## Findings
- **Noisy/Ambiguous Labels:** 269 samples detected where local neighborhoods disagreed with assigned labels.  
- **Outliers:** 3 highly unusual points found, likely rare or erroneous gene expression profiles.  
- **Hard-to-Learn Samples:** 52 points flagged with high label diversity in local neighborhoods.  

t-SNE highlighted **fine-grained clusters and local anomalies**, while Isomap provided a better sense of the **global manifold structure**.

## Requirements
- Python 3.x
- Libraries: `numpy`, `pandas`, `scikit-learn`, `matplotlib`, `scipy`

## Project Structure
- `DA5401_A5_yeast_visualization.ipynb` → Main notebook with preprocessing, dimensionality reduction, plots, and analysis.  
- `yeast/yeast-train.arff` → Dataset file (must be placed in the `yeast/` folder).  
- `README.md` → Project overview and usage instructions.

## How to Run
1. Clone or download this repository.  
2. Ensure the dataset file `yeast/yeast.arff` is placed in the `yeast/` folder.  
4. Open the notebook in Jupyter or VSCode:
    ```bash
    jupyter notebook ME22B214_A5.ipynb
5. Run all cells to reproduce results.