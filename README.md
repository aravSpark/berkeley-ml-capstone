### LoanIQ Loss Predictor

**Aravind Sasidharan**

#### Executive summary
The project aims to predict the expected financial loss on a loan, based on borrower attributes, loan characteristics, and credit behaviour in the historical Lending Club dataset. The focus is on building an explainable model that helps lenders understand which factors most strongly influence credit risk and how these factors affect expected loss.

The primary target is the expected loss. Although the modelling framework could be extended to a classification problem to predict the probability of default,
modelling the loss_amount provides the severity of the projected loss which is more actionable for lending decisions.

#### Rationale
Banks and lenders process thousands of loan applications every day, and even a small improvement in predicting default risk can make a major difference to the bottom line. The challenge is not just knowing which borrowers are risky, but also in understanding what specific factors drive that risk.

This model helps lenders:
* **Identify high-risk loans early:** Estimate the likelihood of loss before a lending decision is made.
* **Interpret risk clearly:** Rather than replacing human judgment, the model flags combinations of features (e.g., DTI and Loan Term) that signal a higher chance of default.
* **Improve transparency:** Automating parts of the risk assessment process through explainable machine learning reduces reliance on static rules and manual assessments.

#### Research Question
Can machine learning regression models predict the loss severity of a loan at origination, based on historical Lending Club data? And which borrower or loan factors have the biggest impact on that risk?

#### Data Sources
* [Lending Club dataset on Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club)
* The dataset contains millions of records from 2007-2018. 
* Post-issuance features were removed to prevent data leakage. Only information available at the time of loan origination was retained.

#### Methodology
To build and test the model, the project uses the following approach:

**Baseline Modeling:** 

The following linear models were used to establish a baseline:

* Linear Regression
* Ridge Regression
* Lasso Regression

These models provided a reference point for performance and helped establish whether relationships between features and loss were primarily linear.  

**Advanced Modeling:** 

To capture non-linear relationships and feature interactions, a LightGBM Regressor was implemented. LightGBM was selected because it:

* Handles large datasets efficiently
* Captures complex, non-linear patterns
* Natively supports categorical features through encoding

Hyperparameter tuning was performed using GridSearchCV, and model stability was evaluated using cross-validation.

**Evaluation Metrics:**

Models were evaluated using:

* **RMSE (Root Mean Squared Error):** Prioritized to penalize large-scale prediction errors, which are more relevant to a lender than small average misses.
* **MAE (Mean Absolute Error):** Used for direct dollar-value error interpretation.
* **R² Score:** Used to measure the proportion of variance explained by the model.

#### Results

The baseline linear models (Linear Regression, Ridge, and Lasso) showed almost identical performance:
* **RMSE:** ~$5,585 | **MAE:** ~$4,054 | **R²:** ~0.50

LightGBM Model (Final) achieved substantially improved performance:
* **RMSE:** ~$4,626 | **MAE:** ~$2,808 | **R²:** ~0.66


This represents a meaningful improvement over linear baselines, indicating that non-linear effects and feature interactions play an important role in predicting loss severity.

**Model Selection**: 

Hyperparameter tuning on a 200k subset suggested a simpler model, but validation on the full 2M-row dataset confirmed that the higher-capacity initial model (800 trees, 63 leaves) was superior for capturing deep risk patterns without overfitting.

**Model Explainability:**

To ensure interpretability, the final model was analysed using SHAP (SHapley Additive exPlanations):
* Global SHAP importance identified key drivers of loss, including loan amount, interest rate, credit score, loan term, and credit utilisation
* Exposure-related features (Loan Amount, Term) have a significantly higher impact on loss severity than traditional borrower metrics (Income, DTI).
  

**Key Findings:**

* Loan size, interest rate, loan term are among the strongest drivers of expected loss
* Higher income alone does not guarantee lower loss severity
* Non-linear models significantly outperform linear baselines in explaining loss variation


**Limitations and Next Steps**

* The model predicts loss severity but does not explicitly model probability of default.
* Post-origination borrower behaviour is not available at application time, limiting predictive power.
* Future enhancements could include a joint Probability of default and Loss given default modelling and incorporation of macroeconomic factors.

#### Outline of project

- [Jupyter Notebook (Google Colab)](https://colab.research.google.com/drive/1TLVYFW1jBLabtq1brgnH-dntougZeetL?usp=sharing)


##### Contact and Further Information

Aravind Sasidharan
