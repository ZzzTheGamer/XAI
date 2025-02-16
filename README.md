# **Mechanistic Interpretability: Code Report**

## **Project Overview**
This repository explores a key technique from the paper **"Towards Monosemanticity: Decomposing Language Models With Dictionary Learning"** by implementing a **sparse autoencoder** to analyze Transformer MLP activations. The goal is to investigate whether Transformer activations can be decomposed into **monosemantic features**, meaning that individual neurons encode distinct, interpretable concepts.

## **Key Finding Implemented**
- We apply **dictionary learning via a sparse autoencoder** to decompose Transformer **MLP activations** into a set of sparse, interpretable features.
- The paper hypothesizes that Transformer activations store multiple features in **superposition**, and by learning a sparse feature basis, we can **recover monosemantic neurons**.

## **Why This Technique?**
- Transformer MLP layers are known to store **multiple entangled features** in the same neurons (polysemanticity).
- Understanding whether these activations can be **decomposed into independent features** provides insights into how Transformers process information.
- Sparse autoencoders have shown promise in extracting **more interpretable representations** from deep neural networks.

## **Implementation Plan**
1. **Set up** and configure the Transformer model and data.
2. **Implement a sparse autoencoder** to extract structured representations from MLP activations.
3. **Train the autoencoder** on Transformer-generated activations.
4. **Analyze extracted features**, checking if they align with meaningful tokens or concepts.
5. **Visualize activations and feature sparsity**, comparing results with findings from the paper.
6. **Test whether monosemantic neurons exist** by examining high/low-frequency activations.
7. **Evaluate reconstruction quality** and compare it with the original model activations.

---

## **Structure of the Jupyter Notebook**

### **1. Implementing the Chosen Technique**
- Code implementation of the **sparse autoencoder**.
- Transformer **MLP activation extraction**.
- **Training and evaluation** of the autoencoder.
- Token-level **feature activation analysis**.

### **2. Documentation and Visualizations**
- Clear **inline documentation** explaining the logic behind each step.
- **Activation frequency histograms** to analyze sparse feature usage.
- **Token feature visualization** showing how different tokens activate different features.

### **3. Demonstrating Understanding**
- Applying the technique to **synthetic activations (Experiment 1)** and **real Transformer activations (Experiment 2)**.
- Comparing our results to **the findings in the paper**.
- Checking **feature interpretability** by identifying tokens that strongly activate specific neurons.

### **4. Challenges Encountered**
- **Superposition Complexity**: Transformer activations are highly entangled, making it hard to obtain fully monosemantic neurons.
- **Feature Overlap**: Some extracted features show signs of polysemanticity, requiring further optimization.
- **Dataset Limitations**: Our autoencoder is trained on limited MLP activations, affecting generalization.

### **5. Potential Improvements**
- **Train autoencoder on larger datasets** for better feature separation.
- **Incorporate feature orthogonality constraints** to reduce overlap between learned features.
- **Apply this method to deeper Transformer layers** to analyze more abstract representations.

---

## **Key Findings**
- **Experiment 1**: Synthetic MLP activations confirm that sparse autoencoders can **decompose activations into distinct features**.
- **Experiment 2**: Real Transformer MLP activations also show **sparse feature representation**, reinforcing the monosemantic neuron hypothesis.
- **Reconstruction Quality**: The autoencoder achieves **91.12% reconstruction accuracy**, indicating that a **small set of features can explain most MLP activations**.
- **Low-frequency features** are **highly specialized** rather than dead neurons, supporting the idea that Transformers use sparse feature encoding.

---

## **How to Run the Notebook**
1. Install dependencies:  
   ```bash
   pip install torch transformers numpy pandas matplotlib gradio
   ```
2. Run the Jupyter notebook:
   ```bash
   jupyter notebook
   ```
3. Follow the sections step by step to execute the experiments.

---

## **References**
- Original Paper: [Towards Monosemanticity: Decomposing Language Models With Dictionary Learning](https://transformer-circuits.pub/2023/monosemantic-features)
- GitHub Implementation: [Sparse Dictionary Learning](https://github.com/shehper/sparse-dictionary-learning)

