# Titanic Survival Prediction

## Overview
This project focuses on predicting the survival of passengers aboard the Titanic using machine learning techniques.  
The dataset comes from the official Kaggle competition:  
[https://www.kaggle.com/competitions/titanic/](https://www.kaggle.com/competitions/titanic/)

The workflow includes:

- Exploratory Data Analysis (EDA)
- Data cleaning & handling missing values
- Feature engineering (titles, family size, age groups, ticket encoding)
- One-hot encoding
- Training an SVM classifier
- Model evaluation (accuracy + confusion matrix)

---

## 📁 Dataset Dictionary


| Variable  | Definition            | Key                                    |
|-----------|----------------------|----------------------------------------|
| survival  | Survival             | 0 = No, 1 = Yes                        |
| pclass    | Ticket class         | 1 = 1st, 2 = 2nd, 3 = 3rd             |
| sex       | Sex                  | male / female                           |
| age       | Age in years         | fractional if <1, estimates end with .5|
| sibsp     | # siblings/spouses aboard |                                      |
| parch     | # parents/children aboard |                                      |
| ticket    | Ticket number        |                                        |
| fare      | Passenger fare       |                                        |
| cabin     | Cabin number         |                                        |
| embarked  | Port of embarkation  | C = Cherbourg, Q = Queenstown, S = Southampton |


---

## 🔍 Exploratory Data Analysis (EDA)
**Key observations:**

- Females had a much higher survival rate (≈ 74%)  
- 1st class passengers survived far more often (≈ 63%)  
- Age distribution differs significantly by class  
- Strong relation between family size and survival  

# 🛠 Data Cleaning

**Actions performed:**

- Filled missing Age using the median per class  
- Filled missing Embarked using mode  
- Replaced missing Cabin with "N", then extracted deck letter  
- Converted Ticket to numeric/binary flag  
- Removed redundant columns (Name, Cabin, Embarked, etc.)  

# 🧪 Feature Engineering

**Created new features:**

- `Family` = SibSp + Parch  
- `Title` extracted from passenger name  
- Titles grouped into 4 categories:  
  - Royal (1)  
  - Rare (2)  
  - Women (3)  
  - Men (4)  
- `Age_select` = 0 (child) / 1 (adult)  

**One-hot encoding applied to:** Pclass, Title, Age group  

# 🧼 Final Dataset

**Model uses the following features:**

- Family  
- Pclass_1  
- Pclass_2  
- Title_1  
- Title_3  
- Title_4  
- Age_select_0  

# 📊 Model Performance

| Metric            | Score |
|------------------|-------|
| Training accuracy | 0.827 |
| Test accuracy     | 0.832 |


