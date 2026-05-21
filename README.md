# Titanic - Machine Learning from Disaster 🚢

This repository contains a solution for the classic Kaggle binary classification competition: predicting passenger survival aboard the Titanic. The project is built as part of my data science portfolio.

## 🎯 Project Objective
The goal is to build a machine learning model that predicts whether a passenger survived the Titanic shipwreck based on demographic data and trip details (such as age, gender, socio-economic class, etc.).

## 🛠️ Tech Stack
* **Python**
* **Pandas** (Data manipulation and analysis)
* **NumPy** (Mathematical operations)
* **Scikit-learn** (Encoding, scaling, validation, and modeling)
* **Random Forest Classifier** (Final machine learning model)

## 📊 Repository Structure
```text
├── data/
│   ├── titanic_train.csv   # Data used for training and validation
│   └── titanic_test.csv    # Unlabeled test data from Kaggle
├── .gitignore              # Files ignored by Git (cache, checkpoints)
├── README.md               # Project documentation
├── requirements.txt        # Python package dependencies
└── titanic.ipynb           # Jupyter Notebook containing the full pipeline

Development Pipeline
To guarantee robust evaluation and completely avoid data leakage, the pipeline follows a strict workflow:

Exploratory Data Analysis & Feature Selection:

Removed non-informative features that could lead to overfitting: PassengerId, Name, Ticket, and Cabin.

Encoded the binary categorical feature Sex using LabelEncoder.

Train-Test Split:

Split the titanic_train.csv dataset into training (X_train) and validation (X_test) sets using an 80/20 ratio.

Stratification (stratify=y) was applied to maintain the target class distribution across both sets.

Data Imputation & Preprocessing:

Median values for missing data in Age and Fare were calculated strictly from the training set (X_train) and then applied to fill gaps in both subsets.

Categorical feature Embarked was transformed using OneHotEncoder(drop='first').

Continuous features were scaled using StandardScaler. The scaler was fitted exclusively on the training data (.fit_transform()), while the validation data was only transformed (.transform()).

Model Training:

Trained a Random Forest Classifier with tuned regularization parameters (max_depth=5, n_estimators=100) to prevent overfitting and ensure better generalization.

📈 Evaluation Metrics
The model demonstrates solid and stable performance on the validation (holdout) dataset:

Accuracy: ~0.81 (The model correctly predicts survival for 81% of the passengers)

F1-Score: ~0.74

ROC AUC: ~0.85

Detailed Classification Report:
Plaintext
              precision    recall  f1-score   support

           0       0.79      0.95      0.86       110
           1       0.87      0.59      0.71        69

    accuracy                           0.81       179


How to Run Locally

Clone this repository:



Bash



git clone [https://github.com/Darkibig/
Titanic-survival-prediction.git](https://github.com/Darkibig/Titanic-survival-prediction.git)

Navigate to the project folder and install the required dependencies:



Bash



pip install -r requirements.txt

Launch Jupyter Notebook / VS Code, open titanic.ipynb, and run all cells.