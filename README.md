# 🧬 Tumor vs Normal Classification Using Gene Expression Data
### 📌 Overview
This project applies basic machine learning models to classify tumor vs normal brain tissue samples using gene expression data.
### Dataset
Source: Gene Expression Omnibus (GEO)
Dataset: GSE68848 (Glioblastoma vs Normal brain tissue)

Due to GitHub file size limits, the dataset is not included in this repository.

To reproduce:
Download the dataset from the GEO link: https://ftp.ncbi.nlm.nih.gov/geo/series/GSE68nnn/GSE68848/matrix/GSE68848_series_matrix.txt.gz

Place the file in the data/ directory
Ensure filename:
GSE68848_series_matrix.txt
### ⚙️ Methods
1. Data preprocessing
Loaded GEO series matrix file
Extracted sample-level metadata
Converted disease labels into a binary classification task:
NON_TUMOR → normal
all other conditions → tumor
2. Handling high-dimensional data
Dataset contains ~54,000 gene features
Applied variance-based feature selection to remove low-information genes
3. Train/test split
Used stratified splitting to preserve class distribution
Prevented data leakage by fitting feature selection only on training data
4. Models
Logistic Regression
Random Forest
Both trained using class_weight='balanced' to address class imbalance
5. Evaluation
Accuracy
Precision, Recall, F1-score
Confusion Matrix
### 📊 Results
Model Performance
Logistic Regression Accuracy: 97.4%

Random Forest Accuracy: 97.4%

Classification Report (Random Forest):

Class	      Precision	Recall	F1-score

Normal (0)	1.00	    0.50	0.67

Tumor  (1)	0.97	    1.00	0.99
### ⚠️ Class Imbalance

The dataset is highly imbalanced (~552 tumor vs 28 normal samples).

Implications:

Accuracy alone is misleading
Model is biased toward tumor detection
Recall for the minority (normal) class is significantly lower (0.50)

This reflects a common challenge in biological datasets, where clinically relevant classes are often underrepresented.

### 📉 PCA Visualization

Principal Component Analysis (PCA) was used to project the data into 2D.

Observations:

Tumor samples dominate the feature space
Normal samples form a small cluster with partial separation
Some overlap exists, explaining imperfect classification of the minority class
### 🧬 Feature Importance

Random Forest feature importance was used to identify key genes contributing to classification.

A small subset of genes contributes disproportionately
Importance scores show a sharp drop after top-ranked features
Suggests potential biological signal but requires further validation
### 🚧 Limitations
Very small number of normal samples
High-dimensional data increases risk of overfitting
No external validation dataset
Results may not generalize to unseen data
### ✅ Key Takeaways
Gene expression data contains strong signal for tumor classification
Proper handling of data leakage and imbalance is critical
High accuracy does not necessarily imply good generalization
Interpretability (feature importance, PCA) adds value beyond raw metrics
### 🚀 Future Improvements
Use larger and more balanced datasets
Explore multi-class classification (tumor subtypes)
Apply cross-validation for more robust evaluation
Incorporate biological pathway analysis
### 🧠 Author Note

This project was built to explore the application of machine learning to biological datasets, particularly in the context of tumor classification.
