![image](https://github.com/user-attachments/assets/5966ba06-7e22-4b61-996c-6f31cd77afde)

# Anomaly Detection in Credit Card Fraud Transactions

This project implements an anomaly detection system to identify fraudulent transactions in a highly imbalanced dataset. The system is designed to flag suspicious transactions based on their deviation from the expected behavior of legitimate transactions.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Installation](#installation)
- [Project Steps](#project-steps)
  - [1. Data Preprocessing](#1-data-preprocessing)
  - [2. Feature Engineering](#2-feature-engineering)
  - [3. Data Visualization](#3-data-visualization)
  - [4. Model Building](#4-model-building)
  - [5. Threshold Tuning](#5-threshold-tuning)
  - [6. Evaluation](#6-evaluation)
- [Results](#results)
- [Conclusion](#conclusion)

---

## Project Overview

Credit card fraud detection is a critical task in financial institutions. The goal of this project is to build a system capable of identifying fraudulent transactions in a dataset where such cases are rare (0.17%). We use a multivariate normal distribution to model the probability density of legitimate transactions and classify those with lower densities as fraudulent.

---

## Dataset

The dataset used in this project contains credit card transactions made by European cardholders in September 2013. It is highly imbalanced, with only 0.172% of transactions being fraudulent.

- [Download the dataset from Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud)

---

## Installation

1. Clone this repository:

    ```bash
    git clone https://github.com/your-username/credit-card-fraud-detection.git
    cd credit-card-fraud-detection
    ```

2. Install the required libraries:

    ```bash
    pip install numpy pandas matplotlib seaborn scikit-learn tqdm psutil
    ```

3. Download the dataset from Kaggle and place it in the project directory.

---

## Project Steps

### 1. Data Preprocessing

- **Dataset Loading**: Load the dataset and split it into two main categories: legitimate transactions (`Class = 0`) and fraudulent transactions (`Class = 1`).

- **Splitting Data**: The legitimate transactions are further divided into training, validation, and testing sets. The fraudulent data is split into validation and testing sets only.

- **Merging Validation and Testing Sets**: Combine the legitimate and fraudulent data for validation and testing.

![image](https://github.com/user-attachments/assets/4b56f72b-9c21-44af-b969-9ee45bccaf50)
![image](https://github.com/user-attachments/assets/904605fb-dd07-4e19-929f-f2478b99cebb)

---

### 2. Feature Engineering

- **Time Feature Transformation**: Decompose the `Time` feature into `Day`, `Hour`, `Minute`, and `Second` to extract more meaningful patterns.

- **Amount Transformation**: Apply a log transformation to the `Amount` feature to reduce skewness and stabilize variance.

![image](https://github.com/user-attachments/assets/4034e246-da67-4361-ba8d-847cc1a18345)


![image](https://github.com/user-attachments/assets/1cbd433a-597a-4c78-b75e-cbf6c2b87725)


---

### 3. Data Visualization

- **Histogram and KDE Plots**: Visualize the distribution of key features like `Time`, `Hour`, and `Amount_transformed` to understand the underlying data patterns.

Time - Hour
![17e72dd9-5823-495b-ba5a-adf4abf7855c](https://github.com/user-attachments/assets/afd255fa-1821-4fce-a9d2-3039b05239c4)

Amount - Transformed_amount
![c4a14b27-041c-425c-90c6-38f57a8b9125](https://github.com/user-attachments/assets/853cfb84-7d2b-49ee-9c0e-b474ec3fb51c)

Features-Selection
![3b941b73-89fb-4df9-81d7-eaeece4889d2](https://github.com/user-attachments/assets/83cec821-80a1-43c5-9da4-30acac19379d)

---

### 4. Model Building

- **Multivariate Normal Distribution**: Fit a multivariate normal distribution to the training data by calculating the mean and standard deviation of each selected feature.

- **Probability Density Calculation**: Calculate the joint probability density function for the features, and classify transactions as fraudulent if their density falls below a certain threshold.

![image](https://github.com/user-attachments/assets/dbfdff98-065b-471b-8fb3-241f5b01303a)

---

### 5. Threshold Tuning

- **Tuning the Threshold**: Iterate over a range of alpha values and select the one that optimizes the F2-score, focusing on reducing false negatives due to the imbalanced dataset.

---

### 6. Evaluation

- **Confusion Matrix**: Generate the confusion matrix to visualize the model's performance in classifying transactions.

- **Performance Metrics**: Calculate accuracy, precision, recall, F1-score, F2-score, and MCC to evaluate the model.

<!-- Insert a corresponding image from the notebook here -->

![image](https://github.com/user-attachments/assets/55413c14-65f4-4a7b-a4ce-25e34b48f7e6)

![c5c32346-510c-4f1d-9348-3eb7628ab3c0](https://github.com/user-attachments/assets/b8fec8de-54ff-426b-9919-8a6455b2ac17)

![c6e6a5a0-04fa-4c22-9796-fba7f0d3f339](https://github.com/user-attachments/assets/80ecca0a-c049-4c71-84a0-f6bebd9a0794)

---

## Results

The optimal threshold value was approximately `3.87 x 10^-19`, resulting in an F2-score of **0.836** on the validation set and **0.815** on the test set. The confusion matrix illustrates the classification performance.

![42d0e4ca-a154-49d0-97da-a021e06d772a](https://github.com/user-attachments/assets/8d583e3e-7357-460c-9b03-62a050519a1a)

<!-- Insert a final evaluation image (e.g., confusion matrix) from the notebook here -->

---

## Conclusion

This anomaly detection system effectively identifies fraudulent transactions by modeling legitimate transactions using a multivariate normal distribution. Key takeaways include:

- **Feature Selection**: The choice of meaningful features significantly impacts model performance.
- **Threshold Optimization**: Proper tuning of the decision threshold is essential for handling imbalanced datasets.
- **Real-World Application**: The model achieves a high F2-score, making it suitable for deployment in real-world fraud detection systems.

---

## Credits

This project uses the credit card fraud dataset from [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud). 

Feel free to contribute to this project by submitting pull requests or suggesting improvements.

---
