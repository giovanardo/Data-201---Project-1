# Data201-Project1
## Project description

This project evaluates classification models to predict whether a breast mass is **malignant** or **benign** from measurements of the mass. Malignant is the positive class.

The most serious error in this project is a **false negative**: classifying a malignant mass as benign can delay diagnosis and treatment. Because of this, the analysis focuses on recall and on the trade-off with false positives, not only on ROC-AUC.

## Data

- 569 breast masses: 357 benign (62.7%) and 212 malignant (37.3%).
- No missing values.
- Predictors used: mean radius, mean texture and mean concave points. Radius and concave points separate the two classes best, and their standard deviations are about twice as large in malignant masses.

## Methods

Four classifiers were compared: **Logistic Regression, LDA, QDA and KNN**.

- Standardization (inside a pipeline) for logistic regression and KNN.
- Evaluation on the test set at thresholds 0.50 and 0.20, with accuracy, precision, recall, specificity, F1 and ROC-AUC.

## Main finding

All four models have almost the same ROC-AUC (about 0.98), so the differences appear at a given threshold. **QDA with a threshold of 0.20** is the model I would deploy: it misses only 3 malignant masses with 11 false positives. Logistic regression misses none at 0.20, but sends 43 benign masses to extra testing, and LDA still misses 7 malignant masses. QDA also fits the data exploration, where the two classes have different variances, which goes against the covariance assumption of LDA.
