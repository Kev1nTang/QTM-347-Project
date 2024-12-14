# QTM-347-Project
# Rain Prediction in Perth

## Abstract: This project aims to develop a model to predict whether it will rain in Perth Australia tomorrow based on today’s weather data. We tested for both parametric and non-parametric models, including logistics regression, KNN, random forest, gradient boosting, etc. Predictors in these models include temperature, sunshine, and humidity, etc.

# Documentation

## Introduction

Weather prediction is a complex challenge due to the non-linear interactions between atmospheric conditions. This project focuses on developing a classification model to predict whether it will rain in Perth, Australia, tomorrow using today’s weather data. Accurate rainfall predictions have significant implications in agriculture, transportation, and emergency preparedness, making this problem both practical and meaningful. Beyond immediate applications, rainfall prediction provides insights into seasonal trends and supports the understanding of climate change.

To address this problem, we propose building and evaluating various classification models, including Logistic Regression, Decision Trees, and ensemble methods like Random Forests and Gradient Boosting. These approaches are well-suited to handling the multi-dimensional and non-linear nature of weather data, with ensemble methods particularly adept at improving prediction accuracy.

Previous studies have shown that statistical models often lack the flexibility to capture complex interactions, while advanced machine learning techniques excel in these scenarios. Our approach emphasizes robust feature engineering, model optimization, and thorough evaluation using metrics such as precision, recall, and F1 score.

While our solution has limitations, such as dependency on data quality and inherent weather variability, it offers a systematic method to improve rainfall prediction accuracy and contribute to practical and research advancements in weather forecasting.

## Setup: 

Dataset used

| **Variable Name**         | **Description**                                                                 | **Data Type** |
|----------------------------|---------------------------------------------------------------------------------|---------------|
| `loan_amnt`               | The total amount of the loan                                                    | Numeric       |
| `loan_term`               | The term of the loan (in months)                                                | Numeric       |
| `emp_length`              | Employment length (in years)                                                    | Categorical   |
| `home_ownership`          | The home ownership status                                                       | Categorical   |
| `income_source_verified`  | Indicator if the income source was verified                                     | Binary        |
| `income_verified`         | Indicator if the income was verified                                            | Binary        |
| `income_thou`             | Income in thousands                                                             | Numeric       |
| `debt_income`             | Debt-to-income ratio                                                            | Numeric       |
| `delinq_2yrs`             | The number of 30+ days past-due incidences of delinquency in the past 2 years    | Numeric       |
| `credit_history_length`   | Length of the borrower's credit history                                         | Numeric       |
| `FICO`                    | FICO credit score                                                              | Numeric       |
| `open_acc`                | Number of open credit lines                                                     | Numeric       |
| `derogatory_recs`         | Number of derogatory records                                                    | Numeric       |
| `revol_balance`           | Total credit revolving balance                                                  | Numeric       |
| `revol_util`              | The amount of credit the borrower is using relative to all available revolving credit | Numeric |
| `loan_rate`               | Interest rate of the loan (Our research target)                                 | Numeric       |


Describe the dataset, including its basic statistics.

Describe the experimental setup, including what models you are going to run, what parameters you plan to use, and what computing environment you will execute on.

Describe the problem setup (e.g., for neural networks, describe the network structure that you are going to use in the experiments).

## Results: Describe the results from your experiments.

Main results: Describe the main experimental results you have; this is where you highlight the most interesting findings.

Supplementary results: Describe the parameter choices you have made while running the experiments. This part goes into justifying those choices.

## Discussion: 
Discuss the results obtained above. If your results are very good, see if you could compare them with some existing approaches that you could find online. If your results are not as good as you had hoped for, make a good-faith diagnosis about what the problem is.

## Conclusion: In several sentences, summarize what you have done in this project.

## References: Put any links, papers, blog posts, or GitHub repositories that you have borrowed from/found useful here.
