### LoanIQ Loss Predictor

**Author**

#### Executive summary
The project aims to predict the expected financial loss on a loan, based on borrower attributes, loan characteristics, and credit behaviour in the historical Lending Club dataset. The focus is on building an explainable model that helps lenders understand which factors most strongly influence credit risk and how these factors affect expected loss.

The primary target is the expected loss. Although the modelling framework could be extended to a classification problem to predict the probability of default,
modelling the loss_amount provides the severity of the projected loss which is more actionable for lending decisions.

#### Rationale
Banks and lenders process thousands of loan applications every day, and even a small improvement in predicting default risk can make a major difference to the bottom line. The challenge is not just knowing which borrowers are risky, but also in understanding what specific factors drive that risk.

This model helps lenders:
* **Identify high-risk loans early:** Estimate the likelihood of loss before a lending decision is made.
* **Interpret risk clearly:** Rather than replacing human judgment, the model flags combinations of features (e.g., DTI and Loan Term) that signal a higher chance of default.
* **Improve transparency:** Automating parts of the risk assessment process through explainable machine learning reduces reliance on static rules and manual assessments..

#### Research Question
Can machine learning regression models predict the probability that a borrower will default, based on historical Lending Club data? And which borrower or loan factors have the biggest impact on that risk?

#### Data Sources
* [Lending Club dataset on Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club)
* **Note:** The dataset contains millions of records from 2007-2018. Post-issuance features were removed to prevent data leakage.

#### Methodology
To build and test the model, the project uses the following approach:

1. **Baseline Modeling:** Linear, Ridge, and Lasso Regression were established as baselines.
2.  **Evaluation Metrics:**
    * **MAE (Mean Absolute Error):** Selected as the primary metric because it provides a direct interpretation in dollar terms (e.g., "The prediction is off by \$X on average").
    * **RMSE (Root Mean Squared Error):** Used to penalize larger errors more heavily.
    * **R² Score:** Used to measure the proportion of variance explained by the model.
3.  **Future Modeling:** Random Forest and Gradient Boosting Regressors will be used to capture non-linear patterns.

#### Results
The baseline linear models (Linear Regression, Ridge, and Lasso) showed almost identical performance:
* **RMSE:** ~$5,585
* **MAE:** ~$4,054
* **R²:** ~0.50
  
**Key Findings:**
* **Linearity:** The identical performance across regularized and non-regularized models suggests the relationship between borrower characteristics and `loss_amount` is largely linear.
* **Predictive Power:** The models explain roughly 50% of the variance in loan losses. Indicating that while borrower attributes are predictive, a significant portion of loss behavior is driven by post-origination factors or complex non-linear interactions not yet captured.
* **Income vs. Loss:** Exploratory analysis revealed that loss severity does not significantly decrease as income increases. Indicating that higher income does not always equals lower risk.

#### Next steps
* Implement non-linear tree-based models (XGBoost Regressor, Random Forest Regressor) to attempt to capture the remaining variance.
* Use SHAP values to explain feature importance at an individual loan level.

#### Outline of project

- [Jupyter Notebook (Google Colab)](https://colab.research.google.com/drive/1f4XCgsvoZat_bSpyZS2OSka9sDhWWE7m?usp=sharing)


##### Contact and Further Information
