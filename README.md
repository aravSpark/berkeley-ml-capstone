### LoanIQ Loss Predictor

**Author**

#### Executive summary
The project aims to predict the expected financial loss on a loan, based on borrower attributes, loan characteristics, and credit behaviour in the historical Lending Club dataset. The focus is on building an explainable model that helps lenders understand which factors most strongly influence credit risk and how these factors affect expected loss.

The primary target is the expected loss. Although the modelling framework could be extended to a classification problem to predict the probability of default,
modelling the loss_amount provides the severity of the projected loss which is more actionable for lending decisions.

#### Rationale
Banks and lenders process thousands of loan applications every day, and even a small improvement in predicting default risk can make a major difference to the bottom line. The challenge is not just knowing which borrowers are risky, but also in understanding what specific factors drive that risk.

The model can be applied to new loan applications to estimate the likelihood of loss or default before a lending decision is made. This helps lenders identify potential high-risk loans early, adjust exposure, and manage their portfolios more proactively.

Modern credit platforms already use similar data-driven approaches to support lending teams with explainable insights. Rather than replacing human judgment, these models help decision-makers interpret risk clearly. For example, flagging combinations of borrower or loan features that signal a higher chance of default.

By answering this question, the model aims to demonstrate how machine learning can make lending decisions fairer, faster, and more transparent. Without such tools, lenders remain dependent on static rules or manual assessments that often miss early warning signs, increase operational costs, and lead to higher losses. Automating parts of the risk assessment process through explainable machine learning can save time, reduce cost, and improve consistency, while still leaving room for human oversight where it matters most.

#### Research Question
Can machine learning regression models predict the probability that a borrower will default, based on historical Lending Club data? And which borrower or loan factors have the biggest impact on that risk?

#### Data Sources
What data will you use to answer you question?

#### Methodology
To build and test the model, the project plans to use:

Linear, Ridge, and Lasso Regression as baseline models
Random Forest and Gradient Boosting Regressors to capture non-linear patterns
SHAP values to explain which features most influence predictions
Evaluation using R², MAE, and RMSE scores

#### Results
What did your research find?

#### Next steps
What suggestions do you have for next steps?

#### Outline of project

- [https://colab.research.google.com/drive/1f4XCgsvoZat_bSpyZS2OSka9sDhWWE7m?usp=sharing]()


##### Contact and Further Information
