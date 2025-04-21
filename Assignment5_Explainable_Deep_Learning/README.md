# 🚀 Explainable Deep Learning: Grad-CAM Analysis on Pascal VOC 2012

## 📌 Overview
This repository contains a detailed analysis of explainability in deep learning models using **Grad-CAM (Gradient-weighted Class Activation Mapping)**. The project aims to test whether a **ResNet-50** model relies primarily on the foreground object (airplanes) or also on background information when making classification decisions.

## 🧐 Hypothesis
### **Null Hypothesis (H₀):**
There is **no significant difference** between the Grad-CAM activations in the foreground (airplane) and background regions.

### **Alternative Hypothesis (H₁):**
Grad-CAM activations in the **foreground (airplane) are significantly higher** than in the background, meaning the model relies more on the object itself for classification.

## 📂 Dataset
We use the **Pascal VOC 2012 dataset**, specifically focusing on images labeled as **airplanes**, along with their segmentation masks for separating foreground and background.

## 🛠️ Implementation Steps
### **Step 1: Load Pretrained ResNet-50 Model**
- Load a **pretrained ResNet-50** model from PyTorch.
- Set it to evaluation mode.
- Select the last convolutional layer (`model.layer4[-1].conv3`) for Grad-CAM analysis.

### **Step 2: Load and Preprocess Images & Segmentation Masks**
- Resize input images to **224x224**.
- Resize segmentation masks to **match the model input size** while preserving label integrity.

### **Step 3: Compute Grad-CAM Heatmaps**
- Iterate through all airplane images.
- Generate Grad-CAM heatmaps for each image.
- Extract foreground (airplane) and background activations based on segmentation masks.

### **Step 4: Perform Paired t-Test**
- Compute the mean Grad-CAM activation values for foreground and background.
- Perform a **paired t-test** to compare activations.
- Calculate **Cohen’s d** effect size.

### **Step 5: Visualize Results**
- Display **Grad-CAM heatmaps** overlayed on the original images.
- Compare model focus areas.

## 📊 Results & Interpretation
### **1️⃣ Grad-CAM Visualization Findings**
- The model **strongly activates on airplane features** (cockpit, engines, tail).
- **Minimal activation in background areas**, suggesting little reliance on contextual information.
- Some activations on **logos and airline text**, which may indicate learned dataset biases.

### **2️⃣ Statistical Analysis**
- **t = 14.755, p = 0.000** → Significant difference between foreground and background activations.
- **Cohen’s d = 2.608** → Extremely large effect size, confirming strong reliance on airplane features.

### **Conclusion: Reject H₀, Accept H₁**
✅ The **Grad-CAM heatmaps and statistical tests confirm that the model predominantly focuses on the airplane rather than the background**, proving that it classifies airplanes based on relevant object features.

## 📌 Next Steps
- **Expand analysis** to other classes in Pascal VOC.
- **Test with different architectures** (e.g., ViTs, EfficientNet).
- **Investigate adversarial effects** on Grad-CAM attention.

## 💡 Contributors
- **Junyu Zhang** - Initial implementation & analysis

## 📜 License
MIT License © 2024
