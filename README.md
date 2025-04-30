# Phishing Detection Project

## Overview
This project implements a machine learning model to detect phishing websites using a Multi-Layer Perceptron (MLP) neural network. The model analyzes various features extracted from URLs and website characteristics to classify them as either legitimate or phishing. The dataset used is `dataset_phishing.csv`, which contains 87 features and a binary label (`status`).

## Features
- **Dataset**: Contains features like URL length, hostname length, number of special characters, domain age, web traffic, and more.
- **Model**: A PyTorch-based MLP with three fully connected layers (87→300→100→1), ReLU activations, batch normalization, dropout (p=0.4), and sigmoid output.
- **Preprocessing**: Drops the `url` column, scales numerical features using `MinMaxScaler`, and encodes the `status` column (`legitimate` → 0, `phishing` → 1).
- **Training**: Uses Adam optimizer, binary cross-entropy loss, and a batch size of 32. Trained for 100 epochs with early stopping (patience=10).
- **Evaluation**: Achieves a validation accuracy of 96.11%. Optimal threshold (0.61) determined using F1 score, yielding an F1 score of 0.9605.
- **Metrics**: Includes ROC curve (AUC), Precision-Recall curve, and F1 score vs. threshold plots for model evaluation.

## Requirements
- Python 3.8+
- Libraries:
  ```bash
  pandas
  numpy
  scikit-learn
  torch
  matplotlib
  ```

 ## Methodology
1. **Data Loading**: Reads `dataset_phishing.csv` using pandas.
2. **Preprocessing**:
   - Drops the `url` column.
   - Encodes `status` column (legitimate: 0, phishing: 1).
   - Scales features using `MinMaxScaler`.
3. **Data Splitting**: Splits data into 80% training and 20% validation sets.
4. **Model Architecture**:
   - Input layer: 87 features.
   - Hidden layers: 300 neurons (ReLU, BatchNorm, Dropout), 100 neurons (ReLU, BatchNorm).
   - Output layer: 1 neuron (Sigmoid).
5. **Training**:
   - Uses Adam optimizer and BCE loss.
   - Implements early stopping based on validation loss.
6. **Evaluation**:
   - Computes accuracy on the validation set.
   - Generates ROC and Precision-Recall curves.
   - Determines the optimal threshold by maximizing the F1 score.

## Results
- **Validation Accuracy**: 96.11%
- **Best Threshold**: 0.61
- **Best F1 Score**: 0.9605
- **ROC AUC**: (Value not explicitly stated but plotted; typically high given the F1 score).

## Future Improvements
- Incorporate additional features (e.g., content-based analysis).
- Experiment with other models (e.g., Random Forest, XGBoost).
- Address dataset imbalance using techniques like SMOTE.
- Deploy the model as an API for real-time phishing detection.

## License
This project is licensed under the MIT License.
