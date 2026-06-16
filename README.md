# Breast Cancer Diagnosis Classification: Algorithm Benchmark

## Project Overview
This project builds an end-to-end predictive model using the Breast Cancer Wisconsin dataset to classify tumors as either benign or malignant. Five supervised classification algorithms are trained, evaluated, and compared across standard performance metrics.

---

## 1. Data Preprocessing & Theoretical Justifications
* **Missing Values Assessment:** The scikit-learn breast cancer dataset is clean and contains zero missing entries.
* **Feature Scaling (Standardization):** Features were transformed using standard normalization ($z = (x - \mu) / \sigma$).
* **Justification:** Algorithms like Support Vector Machines (SVM), Logistic Regression, and k-Nearest Neighbors (k-NN) calculate spatial distances or vector weights. Features measuring cellular attributes (e.g., `mean area` vs `mean smoothness`) reside on radically different numerical scales. Scaling prevents large-magnitude features from overwhelming the model parameters, ensuring stable and reliable classification gradients.
* **Stratification:** Splitting data using `stratify=y` ensures that the proportions of malignant and benign samples remain uniform across both the training and testing sets, preventing class imbalance bias.

---

## 2. Classification Algorithms & Suitability

### 1. Logistic Regression
* **How it Works:** Calculates a linear combination of input features and applies the sigmoid function to map the result into a probability value between 0 and 1.
* **Suitability:** Establishes a highly interpretable probabilistic baseline for binary classification tasks.

### 2. Decision Tree Classifier
* **How it Works:** Segregates data step-by-step by selecting feature thresholds that maximize class purity (e.g., minimizing Gini Impurity or Entropy).
* **Suitability:** Uncovers simple, rule-based clinical decision boundaries without demanding intricate feature normalization dependencies.

### 3. Random Forest Classifier
* **How it Works:** An ensemble bagging method that trains multiple distinct decision trees in parallel over random bootstrap subsets and aggregates their votes.
* **Suitability:** Limits overfitting and provides strong robustness against variance while sorting through high-dimensional cellular features.

### 4. Support Vector Machine (SVM)
* **How it Works:** Projects features into a higher-dimensional space using a kernel function to locate an optimal hyperplane that maximizes the margin distance between classes.
* **Suitability:** Exceptionally powerful at drawing smooth, complex non-linear clinical boundaries in setups where feature columns are highly dense.

### 5. k-Nearest Neighbors (k-NN)
* **How it Works:** A lazy learning instance algorithm that classifies an incoming query based on the majority vote of its '$k$' closest neighbors in feature space.
* **Suitability:** Works intuitively on the assumption that closely related physiological metrics share identical diagnostic outcomes.

---

## 3. Benchmark Evaluation Summary

| Algorithm | Accuracy | Precision | Recall | F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 0.9737 | 0.9726 | 0.9861 | 0.9793 |
| **Decision Tree** | 0.9386 | 0.9577 | 0.9444 | 0.9510 |
| **Random Forest** | 0.9649 | 0.9595 | 0.9861 | 0.9726 |
| **Support Vector Machine (SVM)** | 0.9825 | 0.9730 | 1.0000 | 0.9863 |
| **k-Nearest Neighbors (k-NN)** | 0.9649 | 0.9595 | 0.9861 | 0.9726 |

### Operational Conclusions
* **Best-Performing Algorithm:** **Support Vector Machine (SVM)** ($98.25\%$ Accuracy, $1.0000$ Recall). In medical diagnoses, **Recall** is a critical metric because it measures the model's ability to identify all true positive cases, minimizing dangerous false negatives. SVM correctly flagged 100% of the benign instances while maintaining the highest accuracy.
* **Worst-Performing Algorithm:** **Decision Tree Classifier** ($\approx 93.86\%$ Accuracy). Standalone decision trees create rigid, axis-aligned rectangular boundaries that are prone to overfitting and struggle to capture the fluid, smooth boundaries of overlapping physiological features.

---

## Workspace Local Run Guidelines
1. Clone this repository to your local directory.
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn
