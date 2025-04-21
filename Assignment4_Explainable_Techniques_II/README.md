# Explainability Techniques for Machine Learning Models

## Overview
This project explores explainability techniques for a **machine learning model** trained on the **Heart Disease dataset**. The focus is on generating **PDP, ICE, and ALE plots** to analyze feature importance and interactions.

## Dataset
- **Source:** `heart.csv`
- **Target Variable:** `target` (0 = No Heart Disease, 1 = Heart Disease)
- **Features:** Includes patient demographics, ECG results, blood pressure, cholesterol, and heart rate.

## Exploratory Data Analysis (EDA)
- A **correlation heatmap** was generated to assess relationships between features.
- A **pairplot** was created to visualize feature distributions and interactions.
- Some categorical variables were converted to meaningful labels (e.g., chest pain types, fasting blood sugar levels).

## Model
A **Random Forest Classifier** was trained to predict heart disease.

## Explainability Techniques
### **1. ICE (Individual Conditional Expectation)**
- ICE plots show how **each individual’s prediction** changes as a feature varies.
- Useful for detecting **heterogeneous effects** between variables.
  
### **2. PDP (Partial Dependence Plot)**
- PDPs display the **average effect** of a feature on model predictions.
- Helps understand general trends but can obscure feature interactions.

### **3. ALE (Accumulated Local Effects)**
- ALE plots capture **local feature effects while accounting for interactions**.
- Unlike PDP, ALE does not assume independence between features.

## Findings and Comparisons
- **PDP showed smooth increasing/decreasing trends**, while **ALE highlighted abrupt changes**, suggesting feature interactions.
- **ICE plots revealed variability among individuals**, confirming that different patients are affected differently by certain features.
- A **2D ALE plot** for `max_heart_rate_achieved` and `age` confirmed interactions between these features.

## Conclusion
Using **ICE, PDP, and ALE together** provided a deeper understanding of feature importance and interactions, ensuring better interpretability of the machine learning model.
