---
title: My Project Page
layout: base
--- 

# Data Description

## Dataset Overview

The dataset used in this analysis is the **Titanic Passenger List**, which contains information about the passengers who were aboard the Titanic during its ill-fated voyage in 1912. The data includes various features that may have influenced a passenger's chance of survival, such as socio-economic status, gender, and age.

- **Source**: The dataset is publicly available on [Kaggle](https://www.kaggle.com/c/titanic/data).

## Data Attributes

The dataset consists of the following columns:

| Column Name       | Description                                                                                                                                                       |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PassengerId`      | Unique identifier for each passenger.                                                                                                                          |
| `Survived`         | Survival status (0 = No, 1 = Yes).                                                                                                                                 |
| `Pclass`           | Ticket class (1 = 1st, 2 = 2nd, 3 = 3rd).                                                                                                                       |
| `Name`             | Name of the passenger.                                                                                                                                          |
| `Sex`              | Gender of the passenger (male or female).                                                                                                                      |
| `Age`              | Age of the passenger in years. Some values are missing.                                                                                                          |
| `SibSp`            | Number of siblings or spouses aboard the Titanic.                                                                                                               |
| `Parch`            | Number of parents or children aboard the Titanic.                                                                                                               |
| `Ticket`           | Ticket number.                                                                                                                                                 |
| `Fare`             | Fare paid for the ticket.                                                                                                                                       |
| `Cabin`            | Cabin number where the passenger stayed. Many values are missing.                                                                                               |
| `Embarked`         | Port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton).                                                                                          |

## Handling Missing Values

- **Age**: There are several missing values in the `Age` column. We imputed these missing values with the median age of passengers in the same class (Pclass).
- **Cabin**: The `Cabin` variable has a significant number of missing values. Due to the extent of missing data, this column was excluded from the analysis.
- **Embarked**: There were two missing values in the `Embarked` column. We filled these with the mode (most common value), which is `S` (Southampton).

## Data Cleaning Steps

1. **Loading the Data**: The dataset was loaded into a Pandas DataFrame using:
   ```python
   import pandas as pd
   data = pd.read_csv('data/titanic.csv')
