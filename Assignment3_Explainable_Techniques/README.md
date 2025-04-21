# Local Explanations for Blackbox Model Predictions

## Project Overview:
This project aims to generate local explanations for individual predictions from a pre-trained blackbox model using explanation techniques such as SHAP and LIME. The explanations help in understanding model behavior and providing interpretability in complex machine learning models.

## Explanation Techniques Used
We have employed Lime and Shap to interpret the image classification and text sentiment from InceptionV3 and Bert these two pretrained models.

## Why These Techniques Were Chosen
1. Lime Strengths:
* Model-agnostic and can work with any classifier.
* Provides intuitive and human-understandable explanations.
* Can show how small changes to input data affect the model's prediction.
2. SHAP Strengths:
* Provides consistent and theoretically good feature attributions.
* Explains the global and local importance of features.
* Works well for complex deep learning models.

## Limitations of the Techniques
1. Lime Limitations:
* Sensitive to perturbation strategy and sampling process.
* May produce inconsistent explanations due to local approximations.
2. Shap Limitations:
* Computationally expensive, especially for large datasets.
* Requires access to the model to compute contributions.
  ...

## How to Run the Code
* To reproduce the results, follow these steps:
* Install the required dependencies:
```pip install shap tensorflow matplotlib lime```
* Run the Jupyter Notebook provided to generate explanations for the model predictions.

## Files Included
* Explainable_Techniques.ipynb – Contains the implementation of Shap and Lime for explaining predictions.
* README.md – Explanation of the project, techniques used, and instructions.

