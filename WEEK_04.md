# Week 4 Daily Training Journal

## Day 1: Feature Selection Techniques & Filter Methods
**Date:** 21 July 2026

### Core Concepts Covered

#### 1. What is Feature Selection?
* **Definition:** Feature selection is the process of identifying and selecting only the most relevant, informative, and non-redundant features (columns) from a dataset while eliminating unnecessary or noisy variables prior to model training.
* **The Problem without Feature Selection:** 
  $$\text{50 Features} \longrightarrow \text{Model} \longrightarrow \text{Slow Training} \longrightarrow \text{Overfitting} \longrightarrow \text{Lower Accuracy}$$
* **The Solution with Feature Selection:** 
  $$\text{50 Features} \longrightarrow \text{10 Important Features} \longrightarrow \text{Fast Training} \longrightarrow \text{Better Accuracy} \longrightarrow \text{Easy Interpretation}$$
* **Primary Benefits:**
  * **Faster Model Training:** Smaller feature spaces reduce computational complexity.
  * **Enhanced Accuracy & Reduced Overfitting:** Eliminates misleading background noise.
  * **Memory Efficiency:** Reduces hardware overhead during dataset ingestion.
  * **Improved Interpretability:** Simplifies the underlying mathematical decision boundaries.

---

#### 2. Three Main Categories of Feature Selection
1. **Filter Methods:** Evaluate features independently of any machine learning algorithm using statistical metrics (e.g., Variance, Correlation, Chi-Square, Mutual Information, ANOVA).
2. **Wrapper Methods:** Evaluate feature subsets by iteratively training a specific machine learning model and measuring performance (e.g., Recursive Feature Elimination).
3. **Embedded Methods:** Perform feature selection internally during model training (e.g., Lasso $L_1$ Regularization, Tree-based Feature Importances).

---

#### 3. Overview of Key Statistical Filter Methods

##### Method 1: Variance Thresholding
* **Definition:** A feature selection technique that evaluates each feature independently based on its internal variance.
* **Core Logic:** Drops features whose variance falls below a designated threshold, removing variables that remain static or nearly constant across observations.
* **Practical Advantage:** Quickly eliminates uninformative features without relying on target labels.

##### Method 2: Correlation Coefficient Analysis
* **Definition:** A bivariate statistical technique that measures the strength and direction of linear relationships between numerical variables.
* **Core Logic:** Evaluates linear dependencies between numerical features and the target to assess individual predictive strength.
* **Practical Advantage:** Identifies features with strong linear signals while highlighting redundant, highly correlated pairs.

##### Method 3: Chi-Squared ($\chi^2$) Test
* **Definition:** A non-parametric hypothesis test used to analyze independence between categorical variables.
* **Core Logic:** Evaluates statistical dependency between non-negative or categorical features and target classes by comparing observed frequencies with expected outcomes.
* **Practical Advantage:** Effective for categorical feature selection and binary classification tasks.

##### Method 4: Mutual Information (MI)
* **Definition:** An information-theory metric that quantifies the amount of information obtained about one variable through another.
* **Core Logic:** Calculates how much uncertainty about the target variable is reduced by knowing a feature, capturing both linear and non-linear dependencies.
* **Practical Advantage:** Detects complex, non-linear relationships that linear correlation metrics often miss.

##### Method 5: Analysis of Variance (ANOVA F-Test)
* **Definition:** A parametric statistical test used to analyze mean differences across multiple groups.
* **Core Logic:** Computes $F$-scores and $p$-values between continuous features and categorical target classes to test whether distinct groups share significantly different mean values.
* **Practical Advantage:** Identifies highly discriminative continuous features for classification tasks.

---
