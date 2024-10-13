---
title: My Project Page
layout: template
--- 

# Methodology

## 1. Data Preprocessing

Before performing any statistical analysis, the data needed to be cleaned and preprocessed. The following steps were taken to prepare the dataset for analysis:

- **Handling Missing Values**: 
  - The `Age` variable had several missing values. We imputed these using the median age by passenger class.
  - The `Cabin` variable was mostly missing, so it was excluded from the analysis.
  - The `Embarked` variable had two missing values, which were filled with the most common port of embarkation.
  
- **Encoding Categorical Variables**:
  - The categorical variables `Sex` and `Embarked` were converted into binary and one-hot encoded features, respectively.
  - `Pclass` (Passenger Class) was treated as a categorical variable, even though it is numeric (1, 2, 3).

- **Feature Engineering**:
  - Created a new variable `FamilySize` by combining the `SibSp` (siblings/spouses aboard) and `Parch` (parents/children aboard) variables.
  - Created an indicator variable for whether a passenger was traveling alone (`IsAlone`).

## 2. Exploratory Data Analysis (EDA)

We conducted an Exploratory Data Analysis (EDA) to understand the relationships between different variables and survival. Key steps included:

- **Univariate Analysis**:
  - Frequency distributions of categorical variables (e.g., `Pclass`, `Sex`, `Embarked`).
  - Histograms for continuous variables (e.g., `Age`, `Fare`).

- **Bivariate Analysis**:
  - Bar plots and box plots to explore the relationships between independent variables and the dependent variable (`Survived`).
  - Notable insights:
    - Women had a significantly higher survival rate than men.
    - Passengers in first class had a higher chance of survival than those in second or third class.

- **Correlation Matrix**:
  - Computed a correlation matrix to check for multicollinearity between variables. No significant multicollinearity was observed.

## 3. Statistical Models

We employed multiple statistical models to analyze and predict survival on the Titanic. These models were chosen to balance interpretability and prediction accuracy.

### a. Logistic Regression

- **Goal**: To estimate the probability of survival as a function of the predictor variables.
- **Implementation**: 
  - The logistic regression model was built using `Survived` as the dependent variable and `Pclass`, `Sex`, `Age`, `Fare`, and `Embarked` as independent variables.
  - The model was fit using **maximum likelihood estimation**.
  
- **Results**:
  - **Odds Ratios**: Women had an odds ratio of survival much higher than men.
  - **P-values**: Variables like `Pclass` and `Sex` were statistically significant predictors of survival.

### b. Decision Tree

- **Goal**: To create a tree-based model that predicts survival based on a series of binary decisions (splits).
- **Implementation**:
  - Built a decision tree using `rpart` in R. The depth of the tree was controlled to avoid overfitting.
  - Variables like `Pclass`, `Sex`, `Age`, and `FamilySize` were used as predictors.

- **Results**:
  - The decision tree performed well on the training set but had some overfitting on the test set. Pruning the tree reduced the overfitting.

### c. Random Forest

- **Goal**: To improve the predictive performance by using an ensemble of decision trees (random forest).
- **Implementation**:
  - A random forest model was built using 100 decision trees.
  - The model was trained on 80% of the dataset and tested on the remaining 20%.
  
- **Results**:
  - **Feature Importance**: `Sex`, `Pclass`, and `Age` were the most important variables in determining survival.
  - The random forest achieved higher accuracy compared to logistic regression and the single decision tree.

## 4. Model Evaluation

Each model was evaluated using the following performance metrics:

- **Accuracy**: Percentage of correct predictions out of total predictions.
  - Logistic Regression: 79%
  - Decision Tree: 81%
  - Random Forest: 84%

- **Confusion Matrix**: Provided insights into the false positives and false negatives.
  - Random Forest had the lowest number of false negatives, meaning it was best at predicting survivors.

- **ROC Curve and AUC**:
  - The ROC curve was plotted for each model, and the Area Under the Curve (AUC) was calculated.
  - The random forest had the highest AUC, indicating strong performance across thresholds.

## 5. Limitations

- **Imbalanced Classes**: The dataset is slightly imbalanced, with more non-survivors than survivors. This could have affected the model performance.
- **Data Imputation**: The imputation of missing values (especially for `Age`) introduces some uncertainty in the model.
- **Overfitting**: Although we used techniques like cross-validation and pruning, there is always a risk of overfitting with more complex models like the random forest.

---

## Next Steps

- **Hyperparameter Tuning**: Further fine-tuning of the random forest could improve accuracy.
- **Additional Features**: More features (e.g., cabin location or ticket number) could potentially improve the model's predictive power.
- **Model Interpretation**: Consider using SHAP (Shapley Additive Explanations) values to better understand the contributions of each feature in the random forest model.

---
