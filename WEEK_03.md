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
## Week 3, Day 3: Project Progress Presentation
**Date:** 16 July 2026

### Project Milestone: Concept Showcase & Progress Review

Today, we presented the mid-term progress and architectural framework of our capstone project to the review panel. 

#### Project Title: 
`Bug-Fixer: Automated Bug Localization and Fix Recommendation for C/C++`

#### 1. Project Objective & Core Aim
Debugging compiled languages like C and C++ is notoriously time-consuming due to cryptic compiler errors, manual stack-trace parsing, and memory management complexities. The core goal of **Bug-Fixer** is to build an intelligent, end-to-end assistant that automates software debugging. The application streamlines the debugging pipeline into an intuitive web interface, allowing programmers to instantly validate, locate, and fix syntactic or logical flaws in their source code.

---

#### 2. System Architecture & Workflow Pipeline
The application leverages an advanced AI backend coupled with a responsive frontend to handle source files through three consecutive, automated stages:

* **Stage 1: Binary Defect Classification (AI Inference Backend)**
  * The user uploads raw `.c` or `.cpp` source files directly into the portal.
  * An underlying Artificial Intelligence model parses the abstract structure of the code to run a binary prediction, determining whether the script is structurally sound or contains a software bug.

* **Stage 2: Contextual Localization & Explanation Generation**
  * If the classifier flags the code as buggy, the pipeline passes the source code to a localization engine.
  * The system highlights the most probable lines or blocks causing the execution error and automatically generates a human-readable explanation outlining *why* the bug exists (e.g., memory leaks, array out-of-bounds access, pointer misalignment).

* **Stage 3: Automated Fix Recommendation**
  * Alongside the diagnostic report, the engine generates an optimized, corrected patch file or snippet showing the exact changes required to resolve the issue.

---

#### 3. Frontend Deployment Interface
* To bring this automated pipeline into an accessible environment for everyday developer workflows, the entire system is being deployed using the **Streamlit** web framework. 
* The dashboard features a simple file-uploader utility, asynchronous parsing indicators, side-by-side split visual diffs comparing the broken input code against the recommended patch, and clear error logs.

### Next Steps & Upcoming Sprint
* Finalize training and fine-tuning datasets containing paired buggy/clean C and C++ source examples.
* Complete the structural integration between the AI classification backend script and the interactive Streamlit user interface components.

---
