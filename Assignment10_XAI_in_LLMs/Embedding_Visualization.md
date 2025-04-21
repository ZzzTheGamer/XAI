# Visualizing Embedding Spaces: A Comparison of PCA, t-SNE, and UMAP

## Overview

This notebook demonstrates how to visualize the embedding space of a model from the MTEB leaderboard (using, for example, `sentence-transformers/all-MiniLM-L6-v2`). The primary goal is to reduce high-dimensional word embeddings to a 2D space using three different methods: PCA, t-SNE, and UMAP, and then compare their characteristics and clustering quality.

## Notebook Structure

### 1. Data Loading and Embedding Generation

- **Dataset**: We use the NLTK words dataset (~236k English words) and select the first 2000 words as a subset.
- **Embedding Model**: The notebook uses a pre-trained embedding model from the MTEB leaderboard to compute embeddings for each word.

### 2. Dimensionality Reduction and Visualization

- **PCA**: A linear technique that projects the data along the directions of maximum variance. It provides a quick global view of the data structure.
- **t-SNE**: A nonlinear method focusing on preserving local neighborhoods. It is excellent at revealing fine-grained clusters, although it may lose some global structure.
- **UMAP**: Also a nonlinear method, UMAP balances local and global structure preservation. It typically runs faster than t-SNE and, as observed in our analysis, results in slightly clearer clusters.

For each method, visualizations are generated (both 2D and 3D) with colors assigned to each word based on its Part-of-Speech (POS) tags (converted to universal POS tags for clarity).

### 3. Clustering Evaluation

- **Clustering Algorithm**: KMeans is applied to the reduced 2D data.
- **Evaluation Metric**: The Silhouette score is computed for PCA, t-SNE, and UMAP outputs.
- **Results**:
  - **PCA**: Silhouette Score ~0.332
  - **t-SNE**: Silhouette Score ~0.330
  - **UMAP**: Silhouette Score ~0.374

UMAP’s higher score shows that its 2D layout makes it easier for KMeans to form clearer clusters than PCA or t-SNE.

### 4. Semantic Relationship Analysis

An additional function, `plot_similar_words("heterogeneous", n=8)`, is provided to visualize the semantic relationships of a target word with its 8 most similar words:

- **Interpretation**: The target word is placed at the center, and lines connect it to its nearest neighbors in the embedding space. This visualization helps reveal how the model clusters semantically or morphologically related words.

## Summary of Results

- **PCA** offers a fast and globally consistent view but may miss finer nonlinear relationships.
- **t-SNE** excels at capturing local structure and revealing small clusters, although the global layout may be distorted.
- **UMAP** strikes a balance between local and global structures, leading to slightly better clustering (as measured by Silhouette scores) and a more interpretable 2D representation.

## Interesting Findings

- **POS Tags and Embedding Space**: Despite using POS tags to color the visualizations, the embeddings do not strictly cluster words by their grammatical function. This outcome is expected since the model is primarily optimized for semantic similarity.
- **Semantic vs. Morphological Similarity**: The semantic relationship analysis (e.g., for the word "heterogeneous") highlights that the model captures both meaning and morphological patterns, showing connections that may include synonyms as well as words with shared prefixes.
- **Clustering Behavior**: The moderate Silhouette scores across all methods suggest that the data might not have naturally well-separated clusters in 2D, which opens avenues for experimenting with different parameters or clustering strategies.

## How to Run

- **Platform**: This notebook is designed to run in Google Colab.
- **Dependencies**: Ensure the required packages are installed (`sentence-transformers`, `nltk`, `umap-learn`, `scikit-learn`, `matplotlib`, `plotly`, etc.).
- **Steps**:
  1. Open the notebook in Google Colab.
  2. Execute the cells sequentially.
  3. Review the generated visualizations and results in the markdown cells.

## References

- [MTEB Leaderboard](https://huggingface.co/spaces/mteb/leaderboard)
- [Sentence Transformers Documentation](https://www.sbert.net/)
- [NLTK Documentation](https://www.nltk.org/)
- [UMAP Documentation](https://umap-learn.readthedocs.io/)
- [t-SNE Overview](https://lvdmaaten.github.io/tsne/)


