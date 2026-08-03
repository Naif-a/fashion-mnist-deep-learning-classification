# Fashion-MNIST Classification Project

This project uses TensorFlow and Keras to classify Fashion-MNIST images into ten clothing categories. It compares a baseline Dense neural network with three controlled experiments and selects the final model using validation results only.

## Dataset

Fashion-MNIST contains 70,000 grayscale images with a size of 28x28 pixels:

- 54,000 training images
- 6,000 validation images
- 10,000 test images
- 10 balanced clothing classes

Pixel values were normalized from `[0, 255]` to `[0, 1]`. The official test set was kept separate until the final evaluation.

## Models and Experiments

| Model | Main change | Parameters | Best epoch | Validation accuracy | Validation loss |
|---|---|---:|---:|---:|---:|
| Baseline | One 128-unit hidden layer | 101,770 | 28 | 90.30% | 0.2766 |
| Experiment 1 | Hidden layers increased to 256 and 128 units | 235,146 | 24 | 90.63% | 0.2657 |
| Experiment 2 | Batch Normalization and 20% Dropout | 236,298 | 20 | **90.92%** | **0.2642** |
| Experiment 3 | Initial learning rate reduced to 0.0005 | 236,298 | 11 | 90.28% | 0.2657 |

All models used Adam, sparse categorical cross-entropy, batch size 128, early stopping, and learning-rate reduction.

## Final Results

Experiment 2 was selected because it achieved the strongest validation accuracy and loss. Its restored best weights were evaluated once on the untouched test set.

| Metric | Result |
|---|---:|
| Test accuracy | **89.76%** |
| Macro precision | 89.85% |
| Macro recall | 89.76% |
| Macro F1-score | 89.79% |

The final model exceeded the required 88% test-accuracy target by 1.76 percentage points.

## Error Analysis

Shirt was the most difficult class, with an F1-score of 72.01%. The largest confusions were:

- T-shirt/top predicted as Shirt: 132 images
- Shirt predicted as T-shirt/top: 102 images
- Pullover predicted as Shirt: 81 images

These classes share similar shapes, and small garment details are difficult to preserve in 28x28 grayscale images.

## Run the Project

```bash
pip install -r requirements.txt
jupyter notebook Fashion_MNIST_Project.ipynb
```

Run all cells in order. The notebook creates:

- `best_model.keras`
- `final_model_architecture.png`
- `comparison_table.csv`

## Repository Files

```text
Fashion_MNIST_Project.ipynb
Fashion_MNIST_Technical_Report_FINAL_UPDATED.pdf
best_model.keras
final_model_architecture.png
comparison_table.csv
README.md
requirements.txt
.gitignore
```

## Next Step

A compact convolutional neural network could improve performance by preserving spatial relationships that are lost when the images are flattened.
