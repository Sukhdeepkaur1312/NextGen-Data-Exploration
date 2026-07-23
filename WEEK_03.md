# Week 3 Daily Training Journal

## Day 1: Introduction to Supervised Learning & Logistic Regression
**Date:** 14 July 2026

### Core Concepts Covered

#### 1. What is Supervised Learning?
* Supervised learning is a subfield of machine learning where a model is trained using a labeled dataset—meaning it learns the mathematical relationship between input features ($X$) and their corresponding correct output targets or labels ($y$).
* **The Analogy:** Much like a teacher provides students with a set of practice problems along with their solved answers so they can learn the underlying patterns and tackle new questions on exams, a supervised algorithm learns from known inputs and outputs to make accurate predictions on unseen data.

---

#### 2. Two Main Branches of Supervised Learning
Depending on the nature of the target variable, supervised tasks are divided into classification or regression:

##### Branch A: Classification (Predicting Discrete Categories)
* **Definition:** Classification is used when the target variable is a category or discrete class. The goal is to assign new observations to one of the predefined classes.
* **Algorithm Highlight (Logistic Regression):** A fundamental classification algorithm that calculates the probability of a binary outcome (e.g., $0$ or $1$) using a logistic sigmoid function.
* **Practical Applications & Case Studies:**
  * **Student Placement Prediction:** Predicting whether a student will be `Placed (1)` or `Not Placed (0)` using metrics like `CGPA`, `Attendance`, and `Study Hours` as features. 
    * *Example:* A trained model predicts that a student profile of `[8.5 CGPA, 90% Attendance, 4 Study Hours]` maps to **Placed**, whereas a profile of `[5.0 CGPA, 40% Attendance, 4 Study Hours]` maps to **Not Placed**.
  * **Teen Mental Health Assessment:** Classifying depression risks using behavioral features such as social media usage, sleep hours, academic performance, stress levels, anxiety levels, and addiction levels.
    * *Example:* Evaluating a profile with `[3.2 Social Media Hours, 6 Sleep Hours, 4 Academic Performance, 7 Stress, 6 Anxiety, 5 Addiction]` yields a prediction of **Not Depressed** with $100\%$ model confidence (probability of depression $= 0.00$).
  * **Email Spam Detection:** Filtering whether incoming mail is `Spam` or `Not Spam`.

##### Branch B: Regression (Predicting Continuous Values)
* **Definition:** Regression is used when the target variable is a continuous numerical value rather than a category.
* **Practical Applications:**
  * **Expected Salary Package:** Predicting a graduate's starting salary (e.g., $\text{₹}6.5\text{ LPA}$).
  * **House Price Prediction:** Estimating exact market values based on physical inputs like square footage, age, and bedroom counts.

---
## Day 2: Classification Paradigms-(KNN, SVM, & Naïve Bayes)
**Date:** 15 July 2026

### Core Classification Methods Compared

#### 1. Naïve Bayes
* **Core Logic:** Operates on the principles of probabilistic inference utilizing Bayes' Theorem. It assumes strict conditional independence between every input feature relative to the class variable.
* **Performance Profile:** Extremely fast training phases with fast real-time inference predictions. It requires no feature scaling and shows moderate structural sensitivity to dataset noise.
* **Best Fit:** Excels at handling textual information, filtering spam folders, and running clinical medical diagnosis models.

#### 2. K-Nearest Neighbors (KNN)
* **Core Logic:** A non-parametric "lazy learner" that shifts computational weight entirely to the prediction phase. It determines the category of an unseen data point by finding the closest matching labeled data cluster points based on geometric distance metrics.
* **Performance Profile:** Virtually zero initialization or training speed latency, though prediction phases are slow due to step-by-step neighbor distance lookups. Requires strict feature scaling and is highly sensitive to outlier noise.
* **Best Fit:** Ideal for smaller, well-structured datasets and deploying product recommendation systems.

#### 3. Support Vector Machines (SVM)
* **Core Logic:** Focuses on boundary optimization by finding an optimal separating hyperplane that maximizes the geometric margin between data classes.
* **Performance Profile:** Moderate training speeds with fast real-time prediction performance. Requires precise input feature scaling and displays moderate resilience against noise.
* **Best Fit:** Performs exceptionally well across high-dimensional target spaces, image classifications, and facial recognition tasks.

---
## Day 3: Project Progress Presentation
**Date:** 16 July 2026

### Project Milestone: Concept Showcase & Progress Review

Today, we presented the mid-term progress and architectural framework of our capstone project to the review panel. 

#### Project Title: 
`NewsPulse: AI-Powered News Categorization & Summarization`

#### 1. Project Objective & Core Aim
With the massive influx of digital media, consuming news efficiently is challenging due to information overload and uncategorized content. The core goal of this project is to develop an automated pipeline that processes raw text articles, classifies them into specific news categories, and provides a concise summary. The entire ecosystem is deployed as an interactive web dashboard to streamline how users digest news.

---

#### 2. System Architecture & Workflow Pipeline
The application leverages a modular machine learning and NLP backend connected to a responsive frontend. The data flow operates through the following stages:

---
## Day 4: Tree-Based Models (Decision Trees & Random Forests)
**Date:** 20 July 2026

### 1. Core Concepts & Theoretical Foundations

Today’s session focused on tree-based architectures, moving from single flowchart-like classifiers to ensemble methods.

#### Decision Trees
*   **Core Logic:** A supervised learning algorithm that splits a dataset into smaller subsets using conditional "if-then-else" logic to predict categories or numerical values.
*   **Splitting Criteria:**
    *   **Gini Impurity / Index:** Measures the probability of a random data point being misclassified (fast to compute; a Gini score of $0$ means a node is perfectly pure).
    *   **Entropy:** Measures the structural randomness or disorder within a node.
    *   **Information Gain:** Calculates the exact drop in entropy after a split; the algorithm naturally selects the feature yielding the highest information gain.
*   **Trade-offs:** Highly interpretable, requires minimal preprocessing, and handles mixed data types easily. However, it is prone to overfitting and highly sensitive to minor structural variations in the training data.

#### Random Forests
*   **Core Logic:** An ensemble method that constructs a collection of multiple decision trees to generate more stable and accurate predictions based on the "wisdom of the crowd" principle.
*   **Trade-offs:** Drastically reduces overfitting and remains robust against noise or missing data. The downside is increased memory consumption, slower execution speeds, and diminished interpretability compared to a single tree.

---

### 2. Practical Implementation Walkthrough (`Day 12.ipynb`)

We applied both paradigms to predict depression labels using a teen mental health dataset.

#### Data Preparation & Features
*   **Dataset:** `Teen_Mental_Health_Dataset.csv`
*   **Target Variable ($y$):** `depression_label` (Classes: *Not Depressed*, *Depressed*)
*   **Input Features ($X$):** `daily_social_media_hours`, `sleep_hours`, `academic_performance`, `stress_level`, `anxiety_level`, and `addiction_level`.
*   **Data Split:** $80\%$ Training, $20\%$ Testing (stratified split based on $y$, `random_state=42`).

#### Model 1: Decision Tree Classifier
*   **Configuration:** `DecisionTreeClassifier(criterion='gini', max_depth=4, random_state=42)`
*   **Performance:** Achieved an accuracy score of **100%** on the test set. 
*   **Visualized Tree Rules:**
    *   **Root Split:** Determined primarily by `stress_level <= 6.5`.
    *   **Subsequent Split Features:** Level 2 and 3 nodes branched based on conditional checks against `sleep_hours <= 5.85`, `anxiety_level <= 6.5`, and `daily_social_media_hours <= 4.85`.

#### Model 2: Random Forest Classifier (Ensemble)
*   **Configuration:** `RandomForestClassifier(n_estimators=100, max_depth=5, random_state=42)`
*   **Performance:** Achieved a generalized accuracy score of **97.92%** on the test partition.

---
## Day 5: Continuous Modeling & Regularization (Linear, Ridge, & Lasso Regression)
**Date:** 20 July 2026

### Core Concepts Covered

#### 1. What is Continuous Regularized Modeling?
* Continuous modeling is a subfield of supervised learning where a model is trained to predict a continuous numerical value rather than a discrete category.
* **The Regularization Extension:** When training models on data with many input features, standard algorithms can become over-sensitive to noise, leading to overfitting. Regularization introduces a mathematical penalty to the model's loss function to shrink large coefficients, keeping the model stable and generalizable.
* **The Analogy:** Imagine a student preparing for an exam who tries to memorize every tiny, irrelevant detail in the textbook word-for-word, causing them to perform poorly on real, unseen exam questions due to lack of conceptual flexibility. Regularization acts like a strict study guide that penalizes rote memorization, forcing the student to focus only on the core, most impactful concepts.

---

#### 2. Three Algorithmic Approaches to Continuous Regression
Depending on how feature weights are managed and penalized, continuous regression tasks are divided into three core architectures:

##### Approach A: Linear Regression (Unpenalized Baseline)
* **Definition:** A fundamental regression algorithm that models the relationship between input features ($X$) and a continuous target variable ($y$) by fitting a best-fit straight line.
* **Characteristics:** Uses all available features unconditionally, applies no penalty to coefficient magnitudes, and can easily overfit if many irrelevant features exist.
* **Practical Applications:** Estimating real-world continuous values such as house prices, expected salary packages, marks, or temperature trajectories.

##### Approach B: Ridge Regression ($L_2$ Regularization)
* **Definition:** An extension of linear regression that adds an $L_2$ penalty (the squared magnitude of coefficients) to the cost function to control model complexity.
* **Characteristics:** It shrinks the coefficients of less important features down close to zero, but retains every feature in the final model equations.
* **Practical Advantage:** Drastically reduces overfitting and remains highly robust when features suffer from strong multicollinearity (high correlation with each other).

##### Approach C: Lasso Regression ($L_1$ Regularization)
* **Definition:** An extension of linear regression that adds an $L_1$ penalty (the absolute magnitude of coefficients) to the cost function.
* **Characteristics:** It actively forces the coefficients of completely non-essential or highly redundant features down to exactly zero.
* **Practical Advantage:** Performs automated feature selection, yielding simpler, sparser, and much more interpretable models by completely removing unnecessary variables from the prediction path.

---
[Next: Week 4 Logs →](./WEEK_04.md)
