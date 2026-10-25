# Titanic Survival Prediction
 
> Can we predict who survived the Titanic disaster based on passenger data?
 
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat&logo=python&logoColor=white)
 
---
 
## About the Project
 
On April 15, 1912, the Titanic sank after colliding with an iceberg — 1,502 out of 2,224 passengers and crew lost their lives. This project uses real passenger data to build a machine learning model that predicts whether a given passenger would have survived.
 
This is my first end-to-end machine learning project, built entirely from scratch as part of my data science learning journey. The goal was not just to get a good accuracy score, but to understand every step of the process — from raw messy data to a trained, evaluated model.
 
---
 
## Dataset
 
| | |
|---|---|
| **Source** | [Kaggle Titanic Competition](https://www.kaggle.com/c/titanic) |
| **Training samples** | 891 passengers |
| **Features used** | Pclass, Sex, Age, SibSp, Parch, Fare |
| **Target variable** | Survived (0 = Did not survive, 1 = Survived) |
 
---
 
## Workflow
 
The project follows a standard machine learning pipeline:
 
```
Load Data → Exploratory Data Analysis → Data Cleaning → Feature Engineering → Model Training → Evaluation
```
 
### 1. Exploratory Data Analysis
Before touching anything, I explored the dataset to understand its structure — number of rows and columns, data types, and basic statistics. This step helps you ask the right questions before building anything.
 
### 2. Data Cleaning
Real world data is never clean. Here is what I found and how I handled it:
 
| Column | Issue | Solution |
|---|---|---|
| `Age` | ~19% missing values | Filled with median |
| `Embarked` | 2 missing values | Filled with mode |
| `Cabin` | ~77% missing values | Dropped the column entirely |
 
I used **median** for Age instead of mean because age data can be skewed, and median is more robust to outliers.
 
### 3. Visualisation & Insights
I created four visualisations to understand what factors affected survival:
 
- **Survival count** — only 38% of passengers survived, which creates a class imbalance
- **Survival by gender** — women survived at ~74% vs men at ~19%, confirming the "women and children first" protocol
- **Survival by passenger class** — first class had ~63% survival rate vs third class at ~24%
- **Age distribution** — age alone was not a strong predictor; the distribution looked similar for survivors and non-survivors
### 4. Feature Engineering
Machine learning models only understand numbers, so I converted the `Sex` column from text to binary values (male → 1, female → 0). I then selected the six most relevant features: `Pclass`, `Sex`, `Age`, `SibSp`, `Parch`, and `Fare`.
 
### 5. Model Training
I trained two classification models and compared their performance:
 
| Model | How it works |
|---|---|
| Logistic Regression | Finds a linear boundary to separate survivors from non-survivors |
| Random Forest | Builds 100 decision trees and takes a majority vote |
 
### 6. Evaluation
I evaluated both models using accuracy score, classification report, and confusion matrix on the 20% test set.
 
---
 
## Results 📊
 
| Model | Accuracy |
|---|---|
| Logistic Regression | **81.01%** |
| Random Forest | 79.89% |
 
The simpler Logistic Regression model outperformed Random Forest — a reminder that more complexity does not always mean better performance.
 
---
 
## Key Findings
 
- Gender was by far the strongest predictor of survival
- Passenger class reflected real social inequality — wealthier passengers had better access to lifeboats
- Age alone was not a reliable predictor, though very young children had slightly better chances
- The model is better at predicting deaths than survivals due to class imbalance in the dataset
---
 
## What I Learned 🌱
 
- How to approach a machine learning problem from scratch — understanding the data before touching it
- How to identify and handle missing values using median, mode, and column dropping
- How to read and interpret visualisations — not just make them, but extract real insights from them
- The difference between precision, recall, and F1 score, and why accuracy alone can be misleading
- How to read a confusion matrix and understand where a model is making mistakes
- That simpler models sometimes outperform complex ones — and why that happens
---
 
## Project Structure
 
```
titanic-survival-prediction/
  ├── data/
  │     └── train.csv
  ├── notebooks/
  │     └── titanic_analysis.ipynb
  ├── requirements.txt
  └── README.md
```
 
---
 
## How to Run
 
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/titanic-survival-prediction
cd titanic-survival-prediction
 
# Create and activate virtual environment
python -m venv venv
venv\Scripts\activate
 
# Install dependencies
pip install -r requirements.txt
```
 
Then open `notebooks/titanic_analysis.ipynb` in VS Code and select the venv kernel.
 
---
 
*Project 1 of my data science journey — more projects coming soon.*