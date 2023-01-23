# Utilizing DNA Methylation Signature to Detect Cancer Tumors
Marva Loyfer | DSI 321 | June 2022 
## Problem Statement
This project will take two DNA methylation signature data sets: one of healthy tissues and one of malignant tumors. Based on DNA methylation signatures, I will build several classification models and attempt to predict whether a random sample comes from healthy tissue or a cancer tumor.
## Project Directory
```
Capstone  
|__ images  
|   |__ decision_tree    
|   |__ decision_tree_model.png    
|   |__ normalized_rf_confusion_matrix.png    
|   |__ rf_confusion_matrix.png    
|   |__ rf_e34.png   
|   |__ rf_e89.png   
|   |__ tSNE.png     
|__ models    
|   |__ et_class_model.pkl      
|   |__ rf2_class_model.pkl      
|__ code    
|   |__ 01_Data_Cleaning_and_EDA.ipynb    
|   |__ 02_Supervised_Models.ipynb    
|   |__ 03_Unsupervised_Models.ipynb    
|   |__ 04_Plotting.ipynb    
|   |__ 05_Evaluation.ipynb   
|__ Capstone - DNA Methylation Analysis.pdf  
|__ README.md  
|__ | link to the datasets  
```
## The Datasets  
This data set is part of the [TCGA](https://www.cancer.gov/about-nci/organization/ccg/research/structural-genomics/tcga) project, which identifies and analyzes the genetic mutations that cause cancer in 33 different types of cancer. In this project, I will only analyze breast cancer.
The data sets for this project are organized into two tables, each with 423,669 rows. Each row represents a DNA methylation site. The columns represent tissue samples from different donors. DNA methylation is binary: a methyl group either binds to certain sites or not. But this is true when observing only one cell. If we look at millions of cells, we will find millions of binary observations at the same DNA site. Some cells are methylated and some are not. The decimals in the data frame are the average values of methylation for each DNA site.
As the data shows, 95 healthy tissue samples were collected versus 641 tumor samples. A biopsy is not typically performed on healthy people, which leads to the imbalance data.  
The datasets are too large to upload to repository and can be found [here](https://drive.google.com/drive/folders/1mZVxI0hLVPL3OaPELygZTQUJDhXLRJnd?usp=sharing).
## Executive Summary  
### Data Cleaning & Processing  
In order to classify the tissue samples some initial data cleaning was required. I filled the missing values using sklearn KNN imputer.  
Due to the lage number of features, some of the model could not be run with the original dataset. I therefore created a subset of data that included 2% (n = 9,000) of the DNA sites with the highest variance in methylation patterns. This data set was used for models that broke with the whole df (KNN, tSNE)
### Modeling  
#### Supervised Models
Different supervised machine learning models were used, starting with Logistic Regression, which had low accuracy and was difficult to interpret. In the next step, a Decision Tree, Random Forest, and Extra Tree were applied. Random Forest ranked highest in accuracy and also provided information on what sites were metylated in the DNA and how to split the data. Due to the imbalance in the data, I used a random forest balance algorithm to adjust the model parameters.
#### Unsupervised Models
As a sanity check, unsupervised clustering models were used to verify Random Forest results. The initial KNN model did not cluster according to the desired classes. Next, a tSNE was used. The t-Distributed Stochastic Neighbor Embedding (t-SNE) is an unsupervised, non-linear technique primarily used for data exploration and visualizing high-dimensional data [(source)](https://towardsdatascience.com/an-introduction-to-t-sne-with-python-example-5a3a293108d1). The model returned the desired class clusters, in addition to a few additional pieces of information of interest, such as two different clusters of the malignant class.
## Conclusion & Summary  
DNA methylation signatures can be used to detect cancer, and they already are. New cancer tests and treatments are also being developed using these signatures.  
As a next step I would investigate the random forest model's features importance to learn more about those informative sites, as well as explore the tSNE clustering model.
