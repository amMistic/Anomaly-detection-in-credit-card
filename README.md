![image](https://github.com/user-attachments/assets/5966ba06-7e22-4b61-996c-6f31cd77afde)

# Anomaly Detection in Credit Card Fraud Transactions

This project implements an anomaly detection system to identify fraudulent transactions in a highly imbalanced dataset. The system is designed to flag suspicious transactions based on their deviation from the expected behavior of legitimate transactions.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Code Explanation](#code-explanation)
  - [1. Data Preprocessing](#1-data-preprocessing)
  - [2. Feature Engineering](#2-feature-engineering)
  - [3. Model Building](#3-model-building)
  - [4. Evaluation](#4-evaluation)
- [Results](#results)
- [Conclusion](#conclusion)

## Project Overview

Credit card fraud detection is a critical task in financial institutions. The goal of this project is to build a system capable of identifying fraudulent transactions in a dataset where such cases are rare (0.17%). We use a multivariate normal distribution to model the probability density of legitimate transactions and classify those with lower densities as fraudulent.

## Dataset

The dataset used in this project contains credit card transactions made by European cardholders in September 2013. It is highly imbalanced, with only 0.172% of transactions being fraudulent.

- [Download the dataset from Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud)

## Installation

To set up the project, clone this repository and install the required dependencies.

```bash
git clone https://github.com/your-username/credit-card-fraud-detection.git
cd credit-card-fraud-detection
pip install numpy pandas matplotlib seaborn scikit-learn tqdm psutil
```
## Usage

After installation, you can run the notebook or script to execute the anomaly detection model:

```bash
jupyter notebook anomaly-detection-in-credit-card.ipynb
```

## Code Explanation

### 1. Data Preprocessing

In this section, we load the dataset and split it into two main categories: legitimate transactions (`Class = 0`) and fraudulent transactions (`Class = 1`). We then split the legitimate transactions into training, validation, and testing sets, ensuring that the rare fraudulent transactions are also separated into validation and testing sets.

![image](https://github.com/user-attachments/assets/794148da-b58a-4d66-8157-a74ef13a41ed)

### 2. Feature Engineering

The `Time` feature is decomposed into `Day`, `Hour`, `Minute`, and `Second` to better understand transaction patterns. We also apply a log transformation to the `Amount` feature to reduce skewness.

![image](https://github.com/user-attachments/assets/fbaf689f-47f1-4aff-b408-870453f01ce1)

### 3. Model Building

We fit a multivariate normal distribution to the training data and calculate the joint probability density function for the features. If a transaction's density falls below a threshold, it is classified as fraudulent.

![image](https://github.com/user-attachments/assets/3e8178cb-43aa-47fd-8706-d7bc987ce471)

### 4. Evaluation

To optimize the threshold for classification, we iterate over a range of alpha values and select the one that maximizes the F2-score. This score is chosen due to the imbalanced nature of the dataset, where minimizing false negatives is crucial.

![image](https://github.com/user-attachments/assets/26332edb-5e8c-4aec-89aa-324bd830f738)

## Results

The optimal threshold value was approximately `3.87 x 10^-19`, resulting in an F2-score of **0.836** on the validation set and **0.815** on the test set. The confusion matrix illustrates the classification performance.

![5c02f115-97d1-4867-bc9c-d6d92dafd871](https://github.com/user-attachments/assets/abfd1548-bb1b-4b92-bdeb-7f28ae96c12c)

## Conclusion

This anomaly detection system effectively identifies fraudulent transactions by modeling legitimate transactions using a multivariate normal distribution. The choice of features and the optimization of the decision threshold are key to achieving high performance.

### `requirements.txt`

```txt
numpy
pandas
matplotlib
seaborn
scikit-learn
tqdm
psutil
```
