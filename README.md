# Adversarial Patch Project

## Overview  
This project focuses on creating adversarial patches designed to fool a **ResNet34** model trained on a small version of **ImageNet**. The patches are tested on various images to evaluate their effectiveness in forcing misclassification. Additionally, the project incorporates **creative components**, such as disguising patches as everyday objects and encoding hidden messages.

## Requirements  

### Dependencies  
Ensure you have the following libraries installed before running the code:

```bash
pip install torch torchvision numpy matplotlib pillow
```

### Model  
We use the pre-trained **ResNet34** model from **Torchvision**:

```python
from torchvision.models import resnet34

model = resnet34(weights="IMAGENET1K_V1")
model.eval()  # Set the model to evaluation mode
```

## Adversarial Patch Methods  
The project implements the following adversarial patch techniques:

1. **Basic Patch Attack**  
   - A standard adversarial patch optimized to misclassify a given image into a specific ImageNet class.
   
2. **Disguised Patch**  
   - The patch is hidden within everyday objects such as clothing.
   
3. **Combined Patch Attack**  
   - Two patches are merged in two ways to evaluate how their adversarial effects interact.
   
4. **Secret Message Attack**  
   - A series of adversarial patches encode a hidden message in the model's predictions.

## Running the Code  
Run the Jupyter Notebook to see step-by-step results:
```bash
jupyter notebook Adversarial_Attacks.ipynb
```

## Future Improvements  
- **Improve training efficiency** by optimizing the learning rate and patch placement strategy.
- **Test against other architectures** beyond ResNet34.
- **Enhance real-world applicability** by evaluating patches under physical-world conditions.

## References
- Github resource from https://github.com/AIPI-590-XAI/Duke-AI-XAI/blob/main/adversarial-ai-example-notebooks
- Brown, et al. (2017) "Adversarial Patch" - https://arxiv.org/abs/1712.09665
- Torchvision Models - https://pytorch.org/vision/stable/models.html

