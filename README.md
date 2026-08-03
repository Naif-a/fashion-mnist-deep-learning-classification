# Fashion-MNIST Classification Project

This project uses TensorFlow and Keras to classify Fashion-MNIST images into ten clothing categories. It starts with a simple Dense baseline, then tests three controlled changes to see which model performs best without creating a large training-validation gap.

## Experiments

1. Add a second hidden layer.
2. Add Batch Normalization and Dropout.
3. Lower Adam's learning rate from 0.001 to 0.0005.

The models use the same data split, batch size, and number of epochs so the comparison stays fair. The test set is used only after the final model is selected.

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook Fashion_MNIST_Project_Course_Style.ipynb
```

Open the notebook and run every cell in order. The notebook will generate:

- `best_model.keras`
- `final_model_architecture.png`
- `comparison_table.csv`

## Project Files

- `Fashion_MNIST_Project_Course_Style.ipynb`: complete workflow and explanations
- `Fashion_MNIST_Technical_Report.docx`: editable two-page report
- `Fashion_MNIST_Technical_Report.pdf`: submission copy of the report
- `best_model.keras`: saved final model, generated after running the notebook
- `final_model_architecture.png`: final architecture diagram
- `comparison_table.csv`: experiment results

## Note

The report contains a few highlighted result fields. Replace them with the values printed by your final notebook run before submitting the project.
