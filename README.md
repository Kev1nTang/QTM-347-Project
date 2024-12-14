# QTM-347-Project
# Rain Prediction in Perth

### Abstract: This project aims to develop a model to predict whether it will rain in Perth Australia tomorrow based on today’s weather data. We tested for both parametric and non-parametric models, including logistics regression, KNN, random forest, gradient boosting, etc. Predictors in these models include temperature, sunshine, and humidity, etc.

## Introduction

Weather prediction is a complex challenge due to the non-linear interactions between atmospheric conditions. This project focuses on developing a classification model to predict whether it will rain in Perth, Australia, tomorrow using today’s weather data. Accurate rainfall predictions have significant implications in agriculture, transportation, and emergency preparedness, making this problem both practical and meaningful. Beyond immediate applications, rainfall prediction provides insights into seasonal trends and supports the understanding of climate change.

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%201.png" style="width: 100%; height: auto;">

To address this problem, we propose building and evaluating various classification models, including Logistic Regression, Decision Trees, and ensemble methods like Random Forests and Gradient Boosting. These approaches are well-suited to handling the multi-dimensional and non-linear nature of weather data, with ensemble methods particularly adept at improving prediction accuracy.

# Data Exploration

### Features Overview

| **Feature Name**       | **Description**                                      | **Type**    |
|-------------------------|------------------------------------------------------|-------------|
| `MinTemp`              | Minimum temperature of the day (°C)                  | Numeric     |
| `MaxTemp`              | Maximum temperature of the day (°C)                  | Numeric     |
| `Rainfall`             | Total rainfall for the day (mm)                      | Numeric     |
| `Evaporation`          | Evaporation for the day (mm)                         | Numeric     |
| `Sunshine`             | Total hours of sunshine                              | Numeric     |
| `WindGustSpeed`        | Maximum wind gust speed (km/h)                       | Numeric     |
| `Month`                | Month of the observation (1-12)                      | Categorical |
| `Humidity`             | Average humidity (%)                                 | Numeric     |
| `Pressure`             | Average atmospheric pressure (hPa)                   | Numeric     |
| `Cloud`                | Average cloud coverage (0-8 scale)                   | Numeric     |
| `RainToday_Yes`        | Indicator if it rained today (1 = Yes, 0 = No)       | Binary      |
| `RainTomorrow_Yes`     | Target variable: Will it rain tomorrow? (1 = Yes, 0 = No) | Binary      |

# Experimental Setup

### Computing Environment:
- **Programming Language:** Python 3.8+
- **Platform:** Jupyter Notebook
- **Libraries:** NumPy, pandas, scikit-learn, XGBoost, and Matplotlib/Seaborn for visualization.

### Problem Setup:
- **Objective:** Binary classification to predict whether it will rain tomorrow (`RainTomorrow` = `1` for rain, `0` otherwise).
- **Evaluation Metric:** Classification Error Rate.


#Models Implemented:
### 1. **Parametric Models:**
Parametric models rely on assumptions about the data distribution and aim to estimate parameters that best explain the relationship between predictors and the target variable. For our rain prediction project, we implemented logistic regression as the primary parametric method. Additionally, we used forward selection and regularization techniques to improve model performance and interpretability.

<details>
  <summary>Click to expand</summary>

##### 1.1 **Logistic Regression:** 
Logistic regression is a statistical model used for binary classification problems. It estimates the probability of a binary outcome using a logistic function, making it ideal for predicting categorical variables like "rain" or "no rain."

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%207.png" style="width: 100%; height: auto;">

The misclassification error rate of 12.26% indicates that approximately 12 out of 100 predictions were incorrect. This is a good starting point, showing that the weather variables used are informative but could benefit from refinement.

##### 1.2 **Forward Selection:** 
Forward selection is a stepwise feature selection method that iteratively adds the most significant predictors to the model. It helps identify the best subset of features that contribute most to predicting the target variable.

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%208.png" style="width: 100%; height: auto;">

Forward selection selects the 7 most influential predictors based on their contribution to improving the model's log-likelihood. This refinement reduced the misclassification error rate to 11.64%, the best performance among parametric models. The chosen predictors provide the most information about rain likelihood. For instance, variables like humidity or pressure may dominate due to their direct physical connection to precipitation. A reduction of error rate from 12.26% to 11.64% indicates that including fewer but more relevant predictors improves model efficiency and accuracy. The model selected is demonstrated in the following figure.

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%209.png" style="width: 100%; height: auto;">

##### 1.3 **Principal Component Analysis (PCA) / Partial Least Squares (PLS):** 
PCA is a dimensionality reduction technique that transforms the data into principal components, capturing the most variance in fewer dimensions. PLS, on the other hand, maximizes the covariance between predictors and the target variable, making it suitable for highly correlated features.

**PCA:**

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%2010.png" style="width: 100%; height: auto;">

PCA transformed the predictors into 6 uncorrelated components while retaining as much variance as possible. The misclassification error rate remained at 11.95%, slightly worse than forward selection. PCA effectively addressed multicollinearity among predictors by transforming correlated variables into orthogonal components. However, due to the small number of predictors in our dataset, PCA was less impactful.

**PLS:**

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%2011.png" style="width: 100%; height: auto;">

PLS selected 2 components by maximizing the covariance between predictors and the target variable. However, the misclassification error rate of 12.26% was identical to the full logistic regression model. Like PCA, PLS is more suitable for datasets with a higher number of predictors.

##### 1.4 **Ridge and Lasso Regression:** 
Ridge and Lasso are regularization techniques that add penalties to the regression model to reduce overfitting. Ridge minimizes the sum of squared coefficients, while Lasso encourages sparsity by shrinking coefficients of less important features to zero.

**Ridge:**

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%2012.png" style="width: 100%; height: auto;">

The misclassification error rate of 11.95% indicates that this approach effectively stabilized the model but did not outperform forward selection. Ridge regression provides better generalization by shrinking large coefficients and retaining all predictors. While it controls overfitting, the inclusion of less relevant predictors can dilute the model’s predictive power.

**Lasso:**

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%2013.png" style="width: 100%; height: auto;">

Lasso regression model has a misclassification error rate of 12.42%, the highest among regularization techniques. Lasso’s feature selection is valuable for simplifying models in high-dimensional datasets. In this case, Lasso likely eliminated some predictors that contribute small but meaningful information, leading to a loss in predictive accuracy.

The following figure demonstrates a summary of the misclassification errors derived using different parametric models.

<img src="https://raw.githubusercontent.com/Kev1nTang/QTM-347-Project/main/Figure/Figure%2014.png" style="width: 100%; height: auto;">

Comment:

</details>

### 2.  **Non-parametric Models:**

<details>
  <summary>Click to expand</summary>

##### 2.1 **K-Nearest Neighbors (KNN):**  
an instance-based learning algorithm that classifies a data point based on the majority class of its k-nearest neighbors. It is simple and effective for datasets with distinct clusters but may struggle with high-dimensional data.

##### 2.2 **Classification Trees:**  
partition data into subsets based on feature values, forming a tree-like structure. They are easy to interpret and effective for capturing non-linear relationships in the data.

##### 2.3 **Random Forest:**  
an ensemble learning method that builds multiple decision trees and combines their predictions for improved accuracy. It reduces overfitting and works well with complex datasets with many features.

##### 2.4 **Gradient Boosting:**  
a powerful ensemble method that builds trees sequentially, optimizing for errors made by previous trees. XGBoost, an implementation of Gradient Boosting, is known for its speed and high predictive performance, especially in structured data problems.

</details>

# Results: Describe the results from your experiments.

Main results: Describe the main experimental results you have; this is where you highlight the most interesting findings.

Supplementary results: Describe the parameter choices you have made while running the experiments. This part goes into justifying those choices.

# Discussion: 
Discuss the results obtained above. If your results are very good, see if you could compare them with some existing approaches that you could find online. If your results are not as good as you had hoped for, make a good-faith diagnosis about what the problem is.

## Conclusion: In several sentences, summarize what you have done in this project.

## References: Put any links, papers, blog posts, or GitHub repositories that you have borrowed from/found useful here.
