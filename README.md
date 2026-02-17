# 📊 Feature Contribution & Recourse Analysis  

Performs **feature contribution analysis** and **counterfactual recourse analysis** using the California Housing dataset from `sklearn`.  
The objective is to understand how different features influence house price predictions and generate actionable explanations using modern XAI techniques.

---

## 📌 Project Objectives

- Train a regression model to predict median house prices
- Perform SHAP-based feature contribution analysis
- Generate counterfactual explanations using DiCE
- Conduct experimental what-if studies
- Identify surprising feature behavior and potential model bias

---

## 🗂 Dataset

**California Housing Dataset** (from `sklearn`)

Features include:
- Median Income (MedInc)
- House Age
- Average Rooms
- Average Bedrooms
- Population
- Average Occupancy
- Latitude
- Longitude

Target:
- Median House Value

---

## 🤖 Model Training

Model Used:
- **XGBoost Regressor**

Train-Test Split:
- 80% Training
- 20% Testing

Performance:
- **RMSE ≈ 0.44**
- **R² ≈ 0.85**

This indicates strong predictive performance.

---

## 🔍 SHAP Analysis

SHAP (SHapley Additive exPlanations) was used for feature contribution analysis.

### ✔ Global Feature Importance
- Latitude (~0.48)
- Longitude (~0.41)
- Median Income (~0.36)

### ✔ Summary Plot
Shows direction and magnitude of feature impact across the dataset.

### ✔ Local Explanation (Waterfall Plot)
Explains how individual feature contributions produce a prediction for a specific instance.

---

## 🔄 Counterfactual Explanations (DiCE)

Counterfactuals were generated to:

- Increase predicted house price by a specified amount
- Identify minimal feature changes required to alter predictions

### Experimental What-If Studies

1. **Actionable Counterfactual**
   - Allowed changes only in:
     - Median Income
     - House Age

2. **Realistic Constraint Counterfactual**
   - Fixed:
     - Latitude
     - Longitude

---

## 📊 Key Insights

### 1️⃣ SHAP Importance ≠ Counterfactual Change
Although SHAP identifies Latitude as the most globally important feature, counterfactual explanations primarily modify Median Income.  
This shows that SHAP captures global model sensitivity, while DiCE identifies actionable recourse.

### 2️⃣ Surprising Feature Behaviour
Average Occupancy exhibits a non-linear relationship:
- Moderate values increase predicted price
- Extremely high values decrease predicted price  
This indicates threshold-based effects rather than linear influence.

### 3️⃣ Model Bias Observation
The model heavily depends on geographic features (Latitude & Longitude), suggesting potential geographic bias where coastal regions receive consistently higher predicted values.

---

## 🛠 Technologies Used

- Python
- XGBoost
- SHAP
- DiCE (dice-ml)
- Scikit-learn
- Pandas
- NumPy

---

