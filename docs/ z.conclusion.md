---
layout: default   # This tells Jekyll to use the default layout (from the theme)
title: "Conclusion" # Title of the page
---

# Conclusion

## Summary of Findings

This project aimed to analyze the factors that influenced passenger survival on the Titanic using various statistical models. Through our analysis, we uncovered several key insights:

1. **Gender**: 
   - Women had a significantly higher chance of survival than men. This aligns with the "women and children first" evacuation protocol that was reportedly followed during the disaster.
   - Logistic regression showed that being female increased the odds of survival by nearly five times compared to males.

2. **Passenger Class**:
   - Passengers in 1st class had a much higher survival rate compared to those in 2nd and 3rd class. This reflects the unequal access to lifeboats during the evacuation, where wealthier passengers in first class were more likely to escape.
   - Random forest models revealed that `Pclass` was the second most important predictor of survival after gender.

3. **Age**:
   - Younger passengers had slightly better survival odds, although the impact was less pronounced than gender or class. This could indicate that children were given some priority in lifeboat access, but the effect was not as strong as expected.

4. **Model Comparison**:
   - Among the models tested (logistic regression, decision tree, random forest), the **random forest** model performed the best, with an accuracy of 84% and the highest AUC (0.89).
   - Random forest also had the lowest number of false negatives, making it the most effective model for predicting survivors.

---

## Limitations

While the analysis provided valuable insights, several limitations should be noted:

1. **Imbalanced Dataset**:
   - The dataset had a higher number of non-survivors compared to survivors. This class imbalance may have affected the model's ability to generalize, particularly in identifying survivors.
   
2. **Missing Data**:
   - Several variables, most notably `Age`, had missing values that were imputed using median values. While this approach allowed us to retain more data, the imputation introduces some uncertainty into the results.
   - The `Cabin` variable was excluded due to the large number of missing values, potentially leaving out information that could improve the models.

3. **Simplification of Variables**:
   - Some variables, such as `Fare`, were treated as continuous, which may oversimplify their effect on survival. Additionally, the exclusion of more granular information (like specific cabin numbers or deck levels) may have limited the depth of the analysis.

4. **Model Complexity**:
   - The random forest model, while accurate, can be more difficult to interpret compared to logistic regression. Though it outperformed simpler models, the trade-off between interpretability and performance is an important consideration for practical applications.

---

## Future Work

Based on the insights gained from this analysis, several avenues for future work could be pursued:

1. **Hyperparameter Tuning**:
   - Fine-tuning the parameters of the random forest model (such as the number of trees or maximum tree depth) could potentially improve the accuracy and robustness of the predictions.

2. **Exploring Additional Features**:
   - Further analysis could involve including more detailed variables, such as cabin locations or even interactions between variables (e.g., gender and class). Features like `Ticket` or `Cabin`, while omitted here due to missing values, may provide deeper insights with more advanced imputation techniques.

3. **Alternative Models**:
   - Other advanced machine learning techniques, such as gradient boosting (XGBoost) or support vector machines, could be explored to further improve the prediction accuracy.
   
4. **Imbalanced Data Handling**:
   - Techniques like SMOTE (Synthetic Minority Over-sampling Technique) could be applied to address the class imbalance, potentially improving the model’s ability to correctly identify survivors.

---

## Final Thoughts

This project provided a detailed analysis of the factors affecting survival on the Titanic, using statistical methods to reveal the significance of gender, class, and age in predicting outcomes. While the random forest model demonstrated strong predictive power, the trade-offs between interpretability and complexity should be considered when selecting models for similar analyses. 

By exploring additional variables and employing advanced techniques, future analyses could further refine these findings and potentially uncover deeper patterns in the data.

---

**Thank you for exploring this analysis! Feel free to check out the [GitHub repository](https://github.com/username/titanic-analysis) for code, data, and further details.**
