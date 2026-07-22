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
## Day 2: Feature Selection – Wrapper Methods
**Date:** 22 July 2026

### Core Concepts Covered

#### 1. What are Wrapper Methods?
* **Definition:** A Wrapper Method is a feature selection technique in which a machine learning algorithm is used to evaluate different subsets of features and select the combination that yields the best model performance.
* **Core Difference from Filter Methods:** Unlike Filter Methods (which rank features based purely on statistical scores independent of model architecture), Wrapper Methods train the actual machine learning model repeatedly on various feature combinations to find the optimal subset.

---

#### 2. Four Key Wrapper Method Search Strategies

##### Method 1: Forward Selection (Sequential Feature Selection)
* **Definition:** An iterative feature selection approach that starts with an empty set of features and adds variables one by one based on model performance gains.
* **Core Logic:** Starts with zero features. At each step, it evaluates every remaining feature, adds the one that provides the highest increase in model accuracy, and stops when adding more features no longer improves performance.
* **Practical Advantage:** Computationally efficient when the optimal subset size is small.

##### Method 2: Backward Elimination (Sequential Feature Elimination)
* **Definition:** An iterative feature selection approach that starts with all available features and systematically removes the least impactful variables one by one.
* **Core Logic:** Starts with all features included in the dataset. At each step, it evaluates model performance and permanently removes the feature whose removal causes the least reduction (or an improvement) in accuracy.
* **Practical Advantage:** Effective at catching complex feature interactions since it starts with the full feature space.

##### Method 3: Recursive Feature Elimination (RFE)
* **Definition:** A model-driven wrapper method that uses model coefficient weights or feature importances to recursively eliminate unimportant variables.
* **Core Logic:** Fits the model on all features, ranks features by importance, discards the least important features, and retrains the model on the remaining subset until the target number of features ($k$) is reached.
* **Practical Advantage:** Highly popular and effective for models that produce internal feature importances or weight coefficients (e.g., Linear/Logistic Regression, Decision Trees).

##### Method 4: Recursive Feature Elimination with Cross-Validation (RFECV)
* **Definition:** An advanced variant of RFE that combines recursive feature elimination with cross-validation to automatically determine the optimal number of features.
* **Core Logic:** Automatically finds the best feature subset without requiring the user to hardcode a target number of features ($k$).
* **Practical Advantage:** Eliminates guesswork by utilizing cross-validation scores to find the exact feature subset size that optimizes generalization.

---
