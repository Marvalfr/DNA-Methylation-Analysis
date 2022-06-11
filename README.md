# Utilizing DNA Methylation Signature to Detect Cancer Tumors
Marva Loyfer | DSI 321 | June 2022 
## Problem Statement
This project will take two DNA methylation signature data sets: one of healthy tissues and one of malignant tumors. Based on DNA methylation signatures, I will build several classification models and attempt to predict whether a random sample comes from healthy tissue or a cancer tumor.
## Project Directory
## Executive Summary
## Data Collection
This data set is part of the [TCGA](https://www.cancer.gov/about-nci/organization/ccg/research/structural-genomics/tcga) project, which identifies and analyzes the genetic mutations that cause cancer in 33 different types of cancer. In this project, I will only analyse breast cancer.
The data sets for this project are organized into two tables, each with 423,669 rows. Each row represents a DNA methylation site. The columns represent tissue samples from different donors.
As the data shows, 95 healthy tissue samples were collected versus 641 tumor samples. A biopsy is not typically performed on healthy people, which leads to the imbalance data.  
- Since the data is imbalanced, I used the random forest and extra tree balance algorythm to tune the model preds.

DNA methylation is binary: a methyl group either binds to certain sites or not. But this is true when observing only one cell. If we look at millions of cells, we will find millions of binary observations at the same DNA site. Some cells are methylated and some are not. The decimals in the data frame are the average values of methylation for each DNA site.
### Data Cleaning Procedure
- imputing the missing values with KNNImputer
## Data Exploration and Modeling
- notebook 03: creating a subset of data with 2% (n = 9,000) of the DNA sites with the highest variance in methylation patterns. I used this data set for the models that broke with the whole df (knn, tsne). 
### Supervised Models
#### Logistic Regression
- preformed poorly
#### Decision Tree & Random Forest
- the ensembled modled provided high accuracy scores even after balancing the data.
- extremely informative: privided the namds of DNA splitting sites
### Unsupervised Models
#### KNN Model
- didn't cluster according to the malignant/benign classes.
#### tSNE
- t-Distributed Stochastic Neighbor Embedding (t-SNE) is an unsupervised, non-linear technique primarily used for data exploration and visualizing high-dimensional data [source](https://towardsdatascience.com/an-introduction-to-t-sne-with-python-example-5a3a293108d1). 
- in my model it shows the benign group cluster
- (and another interesting cluster nearby of a malignant group that is probably worth looking into).
## Conclusion & Summary
