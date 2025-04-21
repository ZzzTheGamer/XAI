# Perturbation and Counterfactual Analysis

## Objective
This project applies Explainable AI (XAI) techniques to analyze the behavior of large language models (LLMs) by exploring how prompt perturbations and counterfactual modifications affect model outputs. The goal is to identify the key components of prompts—symbols, patterns, and context—and understand their impact on generated responses.

## Methodology

### Model Selection
- **Model**: GPT-2 (small)
- **Platform**: Hugging Face Transformers
- **Reason for Selection**: GPT-2 is accessible, lightweight, and suitable for experimentation in prompt engineering and XAI tasks.

### Perturbation Types
The study introduces three types of perturbations to the base prompt, along with counterfactual modifications:

1. **Symbols Perturbation**: Substitution of key entities and objects.
   - Example: Replacing "knight" with "wizard" or "dragon" with "demon".
2. **Patterns Perturbation**: Altering sentence structure without changing the core semantics.
   - Example: Switching from active to passive voice.
3. **Text Perturbation**: Modifying the context and theme of the prompt entirely.
   - Example: Changing a medieval battle to a futuristic robot fight or a cooking competition.
4. **Counterfactual Prompts**: Introducing minimal changes that reverse or alter the outcome of the scenario.
   - Example: Changing "the knight won" to "the knight lost".

### Workflow
1. **Base Prompt**: A baseline prompt is selected for reference.
   - "The knight fought the dragon with a sword. The knight won because"
2. **Response Generation**: GPT-2 generates responses for the base prompt and each perturbed/counterfactual prompt using deterministic settings to ensure reproducibility.
3. **Embedding and Similarity Calculation**:
   - Sentence embeddings are generated using the `all-MiniLM-L6-v2` model from Sentence Transformers.
   - Cosine similarity is computed between the base response and each perturbed response.
4. **Visualization**:
   - Results are visualized using bar charts to show the impact of each perturbation type on output similarity.

## Results Summary
| Perturbation Type | Cosine Similarity |
|-------------------|-------------------|
| Symbols           | 0.68              |
| Patterns          | 0.90              |
| Text              | 0.29              |
| Counterfactual    | 0.90              |

### Observations
- **Text Perturbation**: Yields the lowest similarity. Context shifts result in entirely different outputs, demonstrating the model's sensitivity to topic changes.
- **Symbols Perturbation**: Moderate impact. While entities change, the model preserves the narrative structure.
- **Patterns Perturbation**: Minimal effect. Changes in sentence structure do not significantly alter the core semantics.
- **Counterfactual Prompts**: High similarity. Despite changes in outcome, the underlying scenario remains constant.

## Interesting Findings
- GPT-2 displays high sensitivity to contextual changes, which leads to significant semantic divergence.
- Altering syntactic patterns (active/passive voice) has little effect on the generated meaning.
- Small, targeted counterfactual edits (e.g., win → lose) cause limited divergence, highlighting the importance of key tokens in prompt design.

## Limitations and Future Improvements
- **Model Size**: Larger models may yield richer insights.
- **Perturbation Diversity**: Automating perturbation generation could enhance analysis depth.
- **Similarity Metrics**: Exploring other evaluation metrics (BLEU, ROUGE, etc.) may provide additional perspectives.
- **Explainability Techniques**: Incorporating saliency scores or attention analysis could further interpret model behavior.

## Conclusion
This study demonstrates how perturbations and counterfactuals reveal critical insights into prompt engineering and model behavior. By understanding the sensitivity of LLMs to different prompt components, practitioners can design more effective prompts and better interpret model decisions.

## References
- Hugging Face Transformers Library
- Sentence Transformers (all-MiniLM-L6-v2)
- XAI in NLP: https://arxiv.org/abs/2012.10807

