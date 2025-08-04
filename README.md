# 🚢 Titanic Survival Prediction with TensorFlow Decision Forests

## 📝 Project Overview

This project tackles the classic Kaggle Titanic survival prediction challenge. The primary goal is to build a machine learning model that accurately predicts whether a passenger survived the disaster based on features like their age, gender, and ticket class.

This implementation leverages the power of **TensorFlow Decision Forests** to build a high-performance Random Forest model. The entire workflow, from data cleaning and preprocessing to model training and evaluation, is documented within the provided Jupyter Notebook.

The model achieved a final accuracy of **90.43%** when evaluated against the `gender_submission.csv` file.

## 💡 Key Findings & Results

* **Final Accuracy:** 90.43%
* **Model Performance (OOB):** The model achieved an Out-of-Bag accuracy of **82.27%** during training, indicating strong generalization on unseen data from the training set.
* **Most Important Features:** The model identified `Sex`, `Fare`, and `Pclass` as the most significant predictors of survival. The full feature importance ranking is:
    1.  `Sex`
    2.  `Fare`
    3.  `Pclass`
    4.  `Age`
    5.  `Embarked`
    6.  `SibSp`
    7.  `Parch`

## 🛠️ Tech Stack

* **Python**
* **TensorFlow**
* **TensorFlow Decision Forests**
* **Pandas**
* **Numpy**

## ⚙️ Methodology

### 1. Data Cleaning & Preprocessing

The raw data from Kaggle was carefully processed to prepare it for training:

* **Feature Removal:** The `PassengerId`, `Name`, and `Ticket` columns were dropped as they were not considered useful for prediction. The `Cabin` column was also removed due to a high number of missing values.
* **Handling Missing Values:**
    * `Age`: Missing values were imputed using the median age of the respective dataset (train or test).
    * `Embarked`: The two missing values in the training set were filled with the mode ('S').
    * `Fare`: The single missing value in the test set was filled with the median fare.
* **Type Conversion:**
    * The `Pclass` column was converted to a string type to be treated as a categorical feature.
    * The target variable `Survived` was mapped from `0, 1` to `'no', 'yes'`.

### 2. Modeling & Training

A **Random Forest** model was built using the `tensorflow_decision_forests` library.

* **Model:** `tfdf.keras.RandomForestModel`
* **Task:** `CLASSIFICATION`
* **Hyperparameters:**
    * `num_trees`: 100
    * `max_depth`: 10
    * `min_examples`: 10
    * `categorical_algorithm`: 'CART'

The Pandas DataFrames were converted to `tf.data.Dataset` objects before being passed to the model for training.

## 🚀 How to Run the Project

To replicate this analysis, please follow these steps:

1.  **Clone the Repository**
    ```bash
    git clone [https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories)
    cd [PROJECT-FOLDER-NAME]
    ```

2.  **Create a Virtual Environment (Recommended)**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install Dependencies**
    Create a `requirements.txt` file with the content below and run:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the Jupyter Notebook**
    ```bash
    jupyter notebook model.ipynb
    ```

### `requirements.txt`
```
pandas
numpy
tensorflow
tensorflow-decision-forests
```

## 🔗 Author

* **Ygor Carvalho**
* **LinkedIn:** linkedin.com/in/ygorsmc
* **GitHub:** github.com/ygorsmc
