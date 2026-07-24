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
## Day 3: Hyperparameter Tuning & Grid Search
**Date:** 23 July 2026

### Core Concepts Covered

#### 1. What is Hyperparameter Tuning?
* **Definition:** Hyperparameter tuning is the process of finding the optimal combination of model configuration settings prior to training to maximize predictive performance.
* **Parameters vs. Hyperparameters:**
  * **Parameters:** Learned automatically during training by the model (e.g., weights, bias). Cannot be manually set.
  * **Hyperparameters:** Configured manually by the user *before* training begins (e.g., `max_depth`, `n_estimators`, `learning_rate`).

---

#### 2. Key Model Hyperparameters

##### Decision Tree
* **`max_depth`:** Maximum depth of the tree to prevent overfitting.
* **`min_samples_split`:** Minimum number of samples required to split an internal node.
* **`min_samples_leaf`:** Minimum number of samples required at a leaf node.
* **`criterion`:** Function to measure split quality (`gini` or `entropy`).

##### Random Forest
* **`n_estimators`:** Total number of decision trees in the ensemble.
* **`max_depth`:** Maximum depth allowed for individual trees.
* **`max_features`:** Number of features to consider when looking for the best split.
* **`min_samples_leaf`:** Minimum number of samples required at a leaf node.

##### K-Nearest Neighbors (KNN)
* **`n_neighbors`:** Number of nearest neighbors to consider for prediction.
* **`metric`:** Distance metric used (`minkowski`, `euclidean`, `manhattan`).
* **`weights`:** Weight function used in prediction (`uniform` or `distance`).

##### Support Vector Machine (SVM)
* **`C`:** Regularization parameter controlling trade-off between decision boundary smoothness and correct classification.
* **`kernel`:** Kernel type (`linear`, `rbf`, `poly`).
* **`gamma`:** Kernel coefficient defining the reach of a single training instance.

---

#### 3. Tuning Techniques

##### Method 1: Grid Search (`GridSearchCV`)
* **Definition:** An exhaustive search method that evaluates all possible combinations across a specified hyperparameter grid using cross-validation.
* **Core Logic:** Constructs a full grid of candidate values and systematically fits the model on every single combination to find the exact optimal setup.
* **Practical Advantage:** Guaranteed to find the best combination within the specified parameter grid.

##### Method 2: Randomized Search (`RandomizedSearchCV`)
* **Definition:** A search approach that samples a fixed number of parameter combinations randomly from specified distributions.
* **Core Logic:** Instead of testing every possible combination, it randomly samples configurations to efficiently explore high-dimensional search spaces.
* **Practical Advantage:** Significantly faster than Grid Search while yielding comparable performance improvements.

---
## Day 4: ML Pipelines & Model Interpretability
**Date:** 24 July 2026

### Core Concepts Covered

#### 1. What is an ML Pipeline?
* **Definition:** An ML Pipeline is an end-to-end automated framework that chains together data preprocessing, feature engineering, feature selection, and model estimation into a single unified workflow.
* **Why Use Pipelines?**
  * **Prevents Data Leakage:** Ensures preprocessing transformations (like scaling or encoding) are fitted *only* on training folds during cross-validation, keeping test/validation data completely unseen.
  * **Reproducibility & Clean Code:** Replaces fragmented code blocks with a clean, single `.fit()` and `.predict()` pipeline call.
  * **Seamless Deployment:** Allows the exact sequence of data transformations to be saved and applied directly to new, incoming production data.

---

#### 2. What is Model Interpretability?
* **Definition:** Model interpretability refers to the methods and techniques used to explain *how* and *why* a machine learning model makes specific predictions.
* **The Transparency Trade-off:** Simple models (like Linear Regression or Decision Trees) are naturally interpretable but may lack complex predictive power. Complex black-box models (like Random Forests or Gradient Boosted Trees) offer high accuracy but require post-hoc interpretability tools to explain their internal decision boundaries.

---

#### 3. Key Model Interpretability Techniques

##### Approach A: Global Interpretability (Understanding Overall Model Behavior)
* **Feature Importances:** Measures how much each feature contributes to reducing impurity across all decision trees in an ensemble.
* **Permutation Feature Importance:** Evaluates feature importance by measuring the decrease in model score after randomly shuffling a specific feature's values.
* **Partial Dependence Plots (PDP):** Shows the marginal effect that one or two features have on the predicted outcome of a model.

##### Approach B: Local Interpretability (Explaining Individual Predictions)
* **SHAP (SHapley Additive exPlanations):** Grounded in game theory, SHAP computes the marginal contribution of each feature to break down individual predictions into positive or negative pushes relative to the baseline average prediction.
* **LIME (Local Interpretable Model-agnostic Explanations):** Explains individual predictions by fitting a simple, interpretable surrogate model (like a linear model) around the local neighborhood of the target prediction instance.

---
## Day 5: End-to-End NLP Application Deployment & Project Review
**Date:** 27 July 2026

#### 1. End-to-End NLP Project Architecture
* **Definition:** Building a production-ready Natural Language Processing (NLP) web application that integrates dataset cleaning, text vectorization, machine learning classification, automated summarization, and a web interface into a unified system.
* **Core Workflow Components:**
  * **Data Pipeline (`data_prep.py`):** Ingests raw JSON data (`News_Category_Dataset_v3.json`) and exports preprocessed datasets (`clean.csv`).
  * **Model Training (`train_classifier.py`):** Trains text classification models using TF-IDF vectorization and saves serialized artifacts (`classifier.joblib`, `logreg_classifier.joblib`, `tfidf_vectorizer.joblib`) into a dedicated `models/` directory.
  * **Inference Engine (`predict.py`, `summarizer.py`):** Handles incoming raw text input, performs TF-IDF transformation to predict news categories, and applies text-ranking algorithms to extract concise article summaries.
  * **Web Application (`server.py`):** Serves the model predictions and generated summaries via a Flask web application and a responsive frontend interface (`templates/index.html`).

---

#### 2. Project Features & Applied Tech Stack

##### Application Features ("NewsPulse AI")
* **Automated News Categorization:** Predicts top matching news categories (e.g., *WORLD NEWS*, *WELLNESS*, *ENTERTAINMENT*, *BUSINESS*, *POLITICS*).
* **Extractive Text Summarization:** Automatically extracts the most representative key sentences from raw article text based on user-configured sentence counts.
* **Local Inference & Privacy:** Performs all vectorization, classification, and summarization tasks locally on device without sending data to external APIs.

##### Tech Stack Breakdown
* **Language & Web Framework:** Python, Flask (
* `server.py`).
* **Machine Learning & NLP:** `scikit-learn` (TF-IDF Vectorizer + LogisticRegression).
* **Text Summarization:** TextRank / Frequency-based Extractive Summarizer (`sumy`).
* **Environment & Config:** Virtual Environment (`.venv`), `requirements.txt`, `config.toml`.

---
[Main Portfolio / README](README.md)
