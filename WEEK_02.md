# Week 2 Daily Training Journal

## Day 1: Advanced Feature Engineering, Mathematical Transformations, and Categorical Encoding
**Date:** 7 July 2026

### Technical Overview
The session initiated the Week 2 curriculum by focusing on advanced preprocessing techniques required to optimize raw data patterns before feeding them into machine learning models. The lab exercises covered assessing feature skewness, applying mathematical log transformations, implementing structural categorical encoding schemes (Label Encoding and One-Hot Encoding), and establishing rigorous training/testing validation partitions.

### Technical Competencies Acquired

#### 1. Outlier Removal Validation & Distribution Skewness Analysis
* **Data Cleansing Verification:** Confirmed the removal of legacy dataset outliers by plotting clean distribution curves, verifying that features like "CGPA" and "Attendance" now fit completely within valid real-world bounds ($0 \le \text{CGPA} \le 10$).
* **Asymmetric Skewness Identification:** Analyzed how specific numeric features, such as "Family Income," exhibit a heavy right-skewed (positive) distribution tail, which can destabilize parametric machine learning algorithms.

#### 2. Mathematical Feature Transformations
* **Logarithmic Skew Correction:** Implemented NumPy's natural log transformation matrix (`np.log()`) on highly skewed variables to compress extreme values and stretch tight concentrations.
* **Normal Distribution Alignment:** Verified programmatically that transforming raw dollar or currency values into logarithmic space creates a symmetrical distribution, satisfying the normality assumptions of downstream prediction models.

#### 3. Categorical-to-Numerical Encoding Vectorization
* **Label Encoding Frameworks:** Deployed `LabelEncoder` from `sklearn.preprocessing` to map ordinal or simple binary text variables (such as "Gender" or binary state attributes) into structured discrete integers ($0, 1, 2$).
* **One-Hot Encoding Vectorization:** Utilized Pandas `pd.get_dummies()` to transform nominal multi-class categorical arrays (such as "Department" or "City") into independent binary dummy column vectors. This completely avoids assigning unintended mathematical weight or hierarchy to unordered text classifications.

#### 4. Model Validation Datasets and Splitting Principles
* **Feature-Target Matrix Separation:** Structured data matrices into independent descriptive features ($X$) and the dependent predictive target vector ($y$).
* **Train-Test Evaluation Splits:** Leveraged `train_test_split` from `sklearn.model_selection` to isolate historical matrices into designated training pools ($80\%$) and blind validation sets ($20\%$). This baseline setup ensures reliable performance scoring while preventing model overfitting.

---
## Day 2: Dimensionality Reduction using PCA
**Date:** 8 July 2026

### Core Concepts Covered

#### 1. Understanding High-Dimensional Data
* Working with too many features (e.g., 16+ student metrics) leads to high computational cost, high memory usage, slower training times, and sometimes lower accuracy.
* **The Luggage Analogy:** Instead of carrying five small separate bags (Laptop, Books, Clothes, Shoes, Snacks), PCA packs everything efficiently into one single large suitcase without losing any important information.

#### 2. Principal Component Analysis (PCA) Fundamentals
* PCA is a dimensionality reduction technique that compresses many correlated features into a smaller number of new, uncorrelated artificial features called **Principal Components (PCs)**.
* It retains as much of the original data's variance (information) as possible.
* Principal Components are mathematical combinations of original features. Example:
  $$\text{PC1} = 0.6(\text{CGPA}) + 0.3(\text{Attendance}) + 0.1(\text{Study Hours})$$

#### 3. Step-by-Step Implementation
* **Feature Selection:** Isolated key continuous features (`Age`, `CGPA`, `Attendance`, `Study_Hours`, `Backlogs`) into a feature matrix $X$ and dropped missing values.
* **Data Scaling:** Scaled the features using `StandardScaler()` because PCA is highly sensitive to the scale of raw data data.
* **Component Projection:** Initialized `PCA(n_components=2)` from `sklearn.decomposition` to compress the dataset into two dimensions (`PC1` and `PC2`).
* **Variance Evaluation:** Verified performance using:
  * `pca.explained_variance_ratio_` to check the information held by each individual component.
  * `np.cumsum()` to analyze cumulative variance capture.

#### 4. Visualizing the Compressed Space
* Created a 2D scatter plot using `plt.scatter()` with the newly generated `PC1` and `PC2` coordinates.
* **Interpretation:** Every data point represents a student. Students plotted close together share highly similar multidimensional profiles, while students spaced far apart have contrasting characteristics.

#### 5. Real-World Applications of PCA
* **Face Recognition:** Compresses thousands of image pixel inputs into principal features.
* **Healthcare:** Simplifies hundreds of patient medical measurements before passing them to disease diagnostic models.
* **Finance:** Redacts dozens of financial risk indicators down to essential indices for rapid credit analysis.
* **Recommendation Systems:** Compresses user preference parameters to make matching algorithms compute faster.
