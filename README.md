# AI-Based Prediction of Hormonal Disorders Using Non-Invasive Lifestyle and Clinical Features

## 1. Project Overview

This project presents a machine learning-based framework for non-invasive screening and classification of selected hormonal and metabolic disorders using demographic, anthropometric, clinical, and available lifestyle-related features.

The system focuses on three disease-specific binary classification tasks:

* Diabetes
* Polycystic Ovary Syndrome (PCOS)
* Thyroid-related classification

Multiple machine learning and deep learning models are implemented and compared, including Logistic Regression, Decision Tree, Random Forest, XGBoost, Standard Deep Neural Network (DNN), and the proposed Lifestyle Attention Neural Network (LANN).

The project also incorporates SHAP-based explainability and feature-level attention analysis to improve the interpretability of model predictions.

A functional PCOS screening prototype is included to demonstrate the complete prediction workflow from user input to model output.

---

## 2. Objectives

The main objectives of the project are:

1. To investigate the use of non-invasive demographic, anthropometric, clinical, and lifestyle-related features for disease-related classification.
2. To develop disease-specific machine learning models for Diabetes, PCOS, and Thyroid classification.
3. To compare conventional machine learning algorithms with neural-network-based approaches.
4. To implement a Lifestyle Attention Neural Network (LANN).
5. To analyze the contribution and relative emphasis of input features using attention mechanisms.
6. To provide model explainability using SHAP.
7. To develop a functional PCOS screening prototype demonstrating real-time model inference.

---

## 3. Dataset

The integrated dataset used in the project is:

`balanced_multidisease_model_dataset.csv`

The dataset contains:

* 2,298 records
* 150 columns
* 766 Diabetes records
* 766 PCOS records
* 766 Thyroid records

Each disease is treated as a separate binary classification problem.

The disease-specific target variables are:

* `diabetes_target`
* `pcos_target`
* `thyroid_target`

The dataset was constructed from multiple source datasets. Since the availability of lifestyle and clinical features differs across the source datasets, disease-specific feature sets were used rather than forcing a common feature set across all diseases.

---

## 4. Methodology

The overall workflow is:

```text
Dataset
   ↓
Disease-Specific Data Extraction
   ↓
Data Cleaning
   ↓
Feature Selection
   ↓
Train / Validation / Test Split
   ↓
Data Preprocessing
   ↓
Baseline Machine Learning Models
   ↓
Standard DNN
   ↓
Lifestyle Attention Neural Network
   ↓
Model Evaluation
   ↓
SHAP + Attention Analysis
   ↓
Functional Prototype
```

---

## 5. Data Preprocessing

The preprocessing pipeline includes:

* Invalid-value detection
* Missing-value handling
* Numerical feature imputation
* Categorical feature imputation
* One-hot encoding of categorical features
* Standardization of numerical features
* Stratified train-validation-test splitting

A 70:15:15 split is used for training, validation, and testing.

Numerical missing values are handled using median imputation, while categorical values are handled using most-frequent-value imputation where applicable.

---

## 6. Models Implemented

The following models are evaluated:

### Conventional Machine Learning Models

* Logistic Regression
* Decision Tree
* Random Forest
* XGBoost

### Neural Network Models

* Standard Deep Neural Network (DNN)
* Lifestyle Attention Neural Network (LANN)

---

## 7. Lifestyle Attention Neural Network

The proposed LANN introduces a feature-level attention mechanism before the fully connected neural-network layers.

The general architecture is:

```text
Input Features
      ↓
Feature Attention Layer
      ↓
Weighted Feature Representation
      ↓
Dense Layer
      ↓
Dropout
      ↓
Dense Layer
      ↓
Dropout
      ↓
Sigmoid Output
```

The attention mechanism learns feature weights that determine the relative emphasis placed on different input features.

Attention values are interpreted as model-level feature emphasis and not as causal relationships.

---

## 8. Evaluation Metrics

The models are evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC
* Confusion Matrix

ROC curves and other visualizations are generated to provide additional evaluation of classification performance.

---

## 9. Explainability

Two complementary approaches are used for model interpretation.

### Attention Analysis

The LANN attention layer provides relative feature weights learned by the model.

### SHAP Analysis

SHAP is used to examine the contribution of individual features toward model predictions.

These techniques are used to improve model interpretability and should not be interpreted as clinical or causal evidence.

---

## 10. PCOS Functional Prototype

A nine-feature PCOS LANN model is used for the functional prototype.

The prototype accepts:

1. Age
2. Height
3. Weight
4. Waist circumference
5. Hip circumference
6. Systolic blood pressure
7. Diastolic blood pressure
8. Regular exercise
9. Fast-food consumption

BMI and Waist-Hip Ratio are calculated automatically.

The prototype workflow is:

```text
User Input
    ↓
Input Validation
    ↓
BMI Calculation
    ↓
Waist-Hip Ratio Calculation
    ↓
Feature Preprocessing
    ↓
PCOS LANN
    ↓
Model Probability
    ↓
PCOS Screening Classification
```

The prototype is intended for academic demonstration and research purposes.

---

## 11. Project Structure

```text
Hormonal_Disorder_AI/
│
├── data/
│   └── balanced_multidisease_model_dataset.csv
│
├── models/
│   ├── PCOS_LANN_9Feature_Model.keras
│   └── PCOS_LANN_9Feature_Preprocessing.npz
│
├── notebooks/
│   └── implementation.ipynb
│
├── results/
│   ├── model_results/
│   ├── confusion_matrices/
│   ├── roc_curves/
│   ├── attention/
│   ├── shap/
│   └── ablation/
│
├── app/
│   └── app.py
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 12. Installation

Clone the repository:

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd Hormonal_Disorder_AI
```

Create a virtual environment:

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux/macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

---

## 13. Running the Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
notebooks/implementation.ipynb
```

Run the cells sequentially.

The notebook performs:

1. Dataset loading
2. Dataset inspection
3. Data cleaning
4. Feature selection
5. Train-validation-test splitting
6. Preprocessing
7. Baseline model training
8. DNN training
9. LANN training
10. Evaluation
11. Attention analysis
12. SHAP analysis
13. Prototype prediction

---

## 14. Running the PCOS Prototype

The functional prototype can be executed from the notebook.

Open:

```text
notebooks/implementation.ipynb
```

Run the required model-loading and preprocessing cells first.

Then execute the prototype cell containing the interactive input widgets.

The interface will display fields for the required PCOS input parameters.

After entering the values, click:

```text
Perform PCOS Screening
```

The system will calculate BMI and Waist-Hip Ratio, preprocess the input, and pass it to the trained PCOS LANN model.

The output will display:

* BMI
* Waist-Hip Ratio
* Model probability
* PCOS screening classification

---

## 15. Running the Streamlit Interface

If the Streamlit prototype is included, navigate to the application directory:

```bash
cd app
```

Run:

```bash
streamlit run app.py
```

The application will open in the browser.

If Streamlit does not automatically open the browser, copy the local URL shown in the terminal and open it manually.

---

## 16. Model Files

The functional PCOS prototype uses the trained model:

```text
PCOS_LANN_9Feature_Model.keras
```

and its corresponding preprocessing configuration:

```text
PCOS_LANN_9Feature_Preprocessing.npz
```

The preprocessing configuration must correspond to the preprocessing procedure used during model training.

---

## 17. Results

The experiments demonstrate different performance characteristics across the three disease-specific classification tasks.

The models were evaluated using Accuracy, Precision, Recall, F1-score, and ROC-AUC.

The final results and visualizations are stored in the `results/` directory.

The functional nine-feature PCOS LANN prototype achieved:

| Metric    | Result |
| --------- | -----: |
| Accuracy  | 63.48% |
| Precision | 61.19% |
| Recall    | 71.93% |
| F1-score  | 66.13% |
| ROC-AUC   | 67.48% |

---

## 18. Limitations

The project has several limitations:

* The disease-specific datasets contain a limited number of records.
* Feature availability varies across the source datasets.
* Lifestyle features were not available for the thyroid source dataset.
* The integrated dataset combines records from multiple source datasets.
* The models have not undergone clinical validation.
* Model output represents classification/screening and not medical diagnosis.
* Attention values indicate model emphasis and should not be interpreted as causal relationships.

---

## 19. Disclaimer

This project is developed for academic and research purposes.

The predictions generated by the system are machine-learning-based screening classifications and are not intended to provide medical diagnosis, treatment recommendations, or clinical decisions.

The system should not be used as a substitute for consultation with a qualified healthcare professional.

---

## 20. Future Improvements

Future development may include:

* Increasing dataset size
* Incorporating additional validated clinical and lifestyle features
* External validation using independent datasets
* Improving handling of heterogeneous source data
* Hyperparameter optimization
* Calibration of predicted probabilities
* Evaluation on larger and more diverse populations
* Clinical validation before any real-world deployment
