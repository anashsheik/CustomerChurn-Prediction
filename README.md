# Customer Churn Prediction for a Telecom Company

This project involves an analysis of a customer churn dataset to identify key factors that predict customer attrition. The analysis employs Exploratory Data Analysis (EDA), logistic regression with forward stepwise selection using AIC, and a Random Forest model for comparison. The final goal is to develop an interpretable model with strong predictive power to help a telecom company reduce customer churn.

---

### Table of Contents
1.  [Prerequisites](#prerequisites)
2.  [Dataset](#dataset)
3.  [Methodology](#methodology)
4.  [Results](#results)
5.  [Conclusion](#conclusion)

---

### Prerequisites
To run the Jupyter notebook and reproduce this analysis, the following Python libraries are required:

- `pandas`
- `numpy`
- `matplotlib`
- `statsmodels`
- `scikit-learn`
- `random`

These can be installed using `pip`:
```bash pip install pandas numpy matplotlib statsmodels scikit-learn```

---
### Dataset
The analysis is based on the `CustomerChurn.csv` dataset. The dataset contains 3,150 observations and 14 columns with no missing values.

The target variable is **`Churn`**, indicating whether a customer has left (1) or not (0). The features used include:
* `Status`
* `Complains`
* `Frequency of use`
* `Seconds of Use`
* `Customer Value`
* `Charge Amount`
* `Subscription Length`
* `Age Group`

---
### Methodology
The project follows a structured approach from data analysis to model evaluation.

1.  **Exploratory Data Analysis (EDA)**:
    * Initial analysis included generating descriptive statistics for all variables.
    * Visualizations, such as histograms and scatter plots, were used to understand the distribution of variables and identify trends. For example, a scatter plot of `Charge Amount` vs. `Seconds of Use` was created to visualize groupings between churned and non-churned customers.

2.  **Modeling Strategy**:
    * **Baseline Models**: Simple logistic regression models were first fitted for each individual explanatory variable to assess their standalone predictive power based on p-values and AIC.
    * **Forward Stepwise Selection**: A logistic regression model was built iteratively using a forward stepwise selection process. In each step, the variable that most reduced the Akaike Information Criterion (AIC) was added to the model. This resulted in a final model with nine explanatory variables, including `Status`, `Complains`, `Customer Value`, and `Frequency of use`.
    * **Random Forest**: As an alternative, a Random Forest Classifier was also trained and evaluated to compare its performance against the logistic regression model.

3.  **Model Evaluation**:
    * The final logistic regression model's fit was assessed using its **pseudo R-squared** value.
    * **Residual analysis** was performed using a histogram and a QQ-plot to check for significant deviations, even though this is not a strict requirement for logistic regression.
    * The predictive performance of the final models was evaluated on a test set using **Accuracy** and **Area Under the ROC Curve (AUC)** metrics. To handle convergence warnings, the maximum number of iterations for the solver was increased (`max_iter=5000`).

---
### Results
* **Key Predictors**: Initial single-variable analysis showed that `Status`, `Complains`, `Frequency of use`, and `Seconds of Use` were among the most significant predictors of churn. The scatter plot indicated that lower churn probabilities tended to correlate with higher usage levels.

* **Final Logistic Regression Model**:
    * The stepwise selection resulted in a final model with a **pseudo R-squared of approximately 0.49**, indicating a significant improvement over the null model.
    * On the test set, this model achieved an **Accuracy of 0.880** and an **AUC of 0.923**.

* **Random Forest Model**:
    * The Random Forest model performed even better than the logistic regression model on the test set.
    * It achieved an **Accuracy of 0.935** and an **AUC of 0.975**.

---
### Conclusion
The analysis successfully identified key drivers of customer churn, with factors like customer **status**, **complaints**, and **usage frequency** being highly significant.

The forward stepwise logistic regression model provided a good balance between interpretability and predictive power, achieving an AUC of 0.923. The superior performance of the Random Forest model (AUC of 0.975) validates the findings and demonstrates the presence of more complex, non-linear relationships in the data.

Overall, this analysis provides a strong foundation for the telecom company to implement targeted strategies aimed at reducing customer churn.
