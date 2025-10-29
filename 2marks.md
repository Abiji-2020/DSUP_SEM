As a data science expert, I have meticulously analyzed the provided Continuous Internal Evaluation (CIE) papers, Model Question Papers, and Semester End Question Papers to compile a comprehensive list of all 2-mark questions (typically found in Part B) across all units, complete with detailed, source-backed answers.

---

## Unit 1: Data Preprocessing and Concept Learning (CO1)

### 1. Define Data Science
Data Science is defined in the context of the data science project life cycle. This process is a repetitive set of steps required to complete and deliver a project or product to a client.

### 2. State the difference between Data Science and Data Analytics
The sources list this as a short answer question. Data Analysis is often cited as a key step in the OSEMN framework (Explore Data), using visualization to identify significant patterns and trends.

### 3. State the need for data pre-processing
Data preprocessing, referred to as **Data Preparation** or **Data Cleaning/Wrangling**, is essential because data received is rarely homogenous and can be missing, incorrect, duplicate, corrupted, or incomplete.

**Key Needs:**
1.  **Error-Free Data:** It removes errors, wrong values, and garbage values to ensure faster and more efficient analysis. Using data with garbage values results in inaccurate results.
2.  **Model Performance:** Handling missing data prevents it from reducing the performance of machine learning models.
3.  **Consistency:** It ensures data is consistent within the same dataset or across multiple datasets.

### 4. Mention the three methods to handle missing data values
To handle missing data, which is typically represented as 'NaN', 'null', or 'None', Python libraries offer several methods:

1.  **Dropping the missing rows or columns:** Excluding rows or columns containing the missing values. This can be done using the `dropna()` function, typically with `axis=0` to exclude the whole row.
2.  **Imputation with relevant data:** Replacing missing data with the Mean, Median, or Mode of the entire column. The `sklearn.preprocessing` Library provides the `Imputer` class for this.
3.  **Filling NA Forward and Backward:** Using the `fillna(method='pad')` to carry forward previous non-null values, or using `fillna(0)` to replace NaNs with zero.

### 5. What is Concept Learning?
Concept Learning is defined as the learning task of the machine, also known as **Learning by Training Data**.

### 6. What is Vapnik-Chervonenkis dimension? (VCD)
The Vapnik-Chervonenkis (VC) dimension is a measure that characterizes the expressive power or **capacity of a hypothesis class**. It is defined as the maximum number of points that can be **shattered** by the hypothesis space $H$.

*   **Shattering:** A set of $N$ points is shattered if there are hypotheses $h$ in $H$ that can separate positive examples from negative examples in all $2^N$ possible ways.

### 7. Define PAC-learnability
Probably Approximately Correct (PAC) learning is a framework used for the mathematical analysis of machine learning.

*   **Goal:** To ensure that, with high probability (**Probable**), the selected hypothesis will have a low error (**Approximately Correct**).
*   **Formal Requirement:** For parameters $\varepsilon$ (error bound) and $\delta$ (failure probability bound), the learner $L$ must output a hypothesis $h$ such that the error is less than or equal to $\varepsilon$ with a probability of at least $(1 - \delta)$.

$$ \text{Pr}(\text{error}(h) \le \epsilon) \ge 1 - \delta \text{} $$

### 8. How will you deal with datasets consisting of variables with more than 30 percent missing values?
Although the exact method for a 30% threshold is not specified, dealing with a high percentage of missing values involves the general data handling techniques:
1.  **Drop Missing Columns:** If a column has too many missing values (like 30%+), it may be appropriate to drop that column entirely, as imputing too many values might introduce bias.
2.  **Imputation:** If the variable is critical, impute the missing data using Mean, Median, or Mode, using tools like the `Imputer` class from `sklearn.preprocessing`.
3.  **Specific Filling:** Use `fillna()` methods for customized filling strategies.

---

## Unit 2: Python Libraries (NumPy and Pandas) (CO2)

### 9. List the features of NumPy
NumPy (Numerical Python) is the **fundamental package for scientific computing with Python**.

**Key Features:**
1.  **N-dimensional Array Object:** It provides the N-dimensional array object.
2.  **Mathematical Capabilities:** It contains mathematical functions.
3.  **Core Capabilities:** It includes capabilities for linear algebra, Fourier transform, and random number generation.
4.  **Building Block:** It serves as a building block for other Python packages like SciPy.

### 10. Outline the benefits of pandas over other languages
Pandas is an open-source library that provides data structures and operations for working with relational or labeled data easily.

**Benefits:**
1.  **Labeled Data Structures:** Pandas consists of labeled array data structures (Series and DataFrame).
2.  **Integrated Group By Engine:** It includes an integrated group by engine for aggregating and transforming data sets.
3.  **Window Statistics:** It supports moving window statistics.
4.  **Efficient Data Management:** It allows for easy importing, management, and cleaning of data sets using functions like `read_csv()`, `fillna()`, and `merge()`.

### 11. How will you create a Series from a given list in Pandas?
A Pandas Series is a **one-dimensional labeled array** capable of holding data of any type.

**Python Code Snippet (Step-by-Step):**

1.  Import the Pandas library.
2.  Define a Python list.
3.  Call the `pd.Series()` constructor using the list as the argument.

```python
import pandas as pd
# 1. Define a list (Example 2)
list = 

# 2. Create Series from the list
res = pd.Series(list) 

print(res)
# Output:
# 0 1
# 1 2
# ...
# Dtype:int64
```

### 12. Mention the steps for data wrangling and data cleaning before applying machine learning algorithms.
Data wrangling (or data munging) is the process of cleaning, restructuring, and enriching raw data.

**Key Steps (before ML):**

1.  **Data Loading/Importing:** Importing the dataset and required libraries (NumPy, Pandas).
2.  **Handling Missing Data:** Using methods like `Imputer` (or `fillna`) to handle `NaN` values.
3.  **Data Cleaning:** Removing duplicates (`drop_duplicates()`), dealing with incorrect data, and handling outliers.
4.  **Encoding Categorical Data:** Converting categorical data (e.g., 'Sex') into numerical formats using `LabelEncoder` or `get_dummies`.
5.  **Splitting Data:** Separating the data set into features (X) and the dependent vector (Y).
6.  **Feature Scaling** (if required).

### 13. State the need for data wrangling.
Data wrangling (also known as data cleaning or data preparation) is required because raw data is often messy. The need stems from ensuring the data is in a format suitable for analysis and model application.

*   **Key Purpose:** To clean, restructure, and enrich raw data into a desired format for better analysis. This includes tasks like removing duplicates, handling missing values, merging datasets, and reshaping data.

### 14. What is the need of indexers in pandas? Give an example.
Pandas indexers, specifically **iloc** and **loc**, are used to access specific groups of rows and columns in a DataFrame.

*   **Need:** To select specific parts of the dataset, such as separating features (X) from the dependent variable (Y).
*   **Example (Using `iloc`):** The `iloc` indexer is used to fix the indexes for selection.

```python
# Assuming 'dataset' is a loaded Pandas DataFrame
# Select all rows (:) and all columns except the last one (:-1) for features (X)
X = dataset.iloc[:, :-1].values #

# Select all rows (:) and the column with index 3 (4th column) for the label (y)
y = dataset.iloc[:, 3].values   #
```

---

## Unit 3: Modeling and Dimensionality Reduction (CO3)

### 15. What is linear regression model in Data Science?
Linear regression is a type of supervised machine learning model. In this model, the goal is for the model to find the **best fit linear line** between the independent and dependent variables.

### 16. List the three major components of a Machine learning system?
A machine learning system is composed of three major components:

1.  **Data**.
2.  **Models**.
3.  **Learning** (or parameter estimation).

### 17. List conceptually three distinct algorithmic phases when discussing machine learning algorithms
When discussing machine learning algorithms, there are three conceptually distinct algorithmic phases:

1.  **Prediction or inference**.
2.  **Training or parameter estimation**.
3.  **Hyperparameter tuning or model selection**.

### 18. List the three cases in Model fitting?
After parameter optimization (finding the best parameters $\theta^*$), we distinguish three different cases of model fitting:

1.  **Overfitting:** The parametrized model class is too rich and fits the training data too well, potentially failing to generalize to unseen data.
2.  **Underfitting:** The model class $M_\theta$ is not rich enough to describe the dataset, meaning the model is too simple.
3.  **Fitting Well:** The model class is just rich enough to describe the dataset, meaning it neither overfits nor underfits.

### 19. State the properties of probabilistic graphical models
The directed graphical model, also known as a Bayesian network, provides a visual and compact language for specifying probabilistic models.

**Key Properties:**
1.  **Visualize Structure:** They are a simple way to visualize the structure of a probabilistic model.
2.  **Design Models:** They can be used to design or motivate new kinds of statistical models.
3.  **Conditional Independence:** Inspection of the graph alone gives insight into properties such as conditional independence.
4.  **Complex Computations:** Complex computations for inference and learning can be expressed in terms of graphical manipulations.

### 20. What is principal component analysis?
Principal Component Analysis (PCA) is a dimensionality reduction technique. It is used to find orthogonal linear combinations and reduce the dimension of the data.

### 21. State the key steps in PCA.
For practical application, PCA involves the following key steps:

1.  **Mean subtraction:** Centering the data by computing the mean ($\mu$) and subtracting it from every single data point.
2.  **Standardization:** Dividing the data points by the standard deviation ($\sigma_d$) for every dimension $d$.
3.  **Eigendecomposition:** Computing the data covariance matrix and finding its eigenvalues and corresponding eigenvectors.
4.  **Projection:** Projecting the standardized data onto the principal subspace defined by the eigenvectors associated with the largest eigenvalues.

### 22. Differentiate prior predictions and posterior predictions
These terms relate to **Bayesian Linear Regression**.

| Concept | Description |
| :--- | :--- |
| **Prior Prediction** | Prediction made based on the prior knowledge about the distribution of the parameters $\theta$ before observing the training data. |
| **Posterior Prediction** | Prediction made based on the **posterior distribution** $p(\theta|x)$, which is the updated knowledge about the parameters after observing the data $x$ (computed using Bayes' theorem). |

### 23. State the idea behind the Maximum Likelihood Estimation (MLE) in parameter estimation with necessary notation.
Maximum Likelihood Estimation (MLE) is a widely used approach for finding the desired parameters $\theta_{\text{ML}}$ in parameter estimation.

*   **Idea:** The idea is to define a function of the parameters that allows us to find a model that fits the data well, specifically by maximizing the **likelihood function** (or minimizing its negative logarithm). Maximizing the likelihood means maximizing the predictive distribution of the training data given the model parameters.
*   **Notation:** For data $x$ and a family of probability densities $p(x | \theta)$ parametrized by $\theta$, the MLE parameters $\theta_{\text{ML}}$ maximize the likelihood function.

### 24. What is a directed graphical model?
A directed graphical model (or Bayesian network) is a graphical language used for specifying a probabilistic model.

*   **Structure:** It provides a compact and succinct way to specify probabilistic models, allowing the dependencies between random variables to be visually parsed.
*   **Mechanism:** Directed links (arrows) between two nodes (random variables) indicate conditional probabilities.

---

## Unit 4: Data Visualization (CO4)

### 25. Define Task abstraction
Task abstraction is the process of simplifying complex tasks by breaking them down into more manageable sub-tasks or generalized concepts. It encourages reasoning about similarities and differences between tasks by transforming descriptions from domain-specific language into an abstract form.

### 26. Mention the four levels of validation.
Visualization design validation occurs across four hierarchical levels:

1.  **Domain Situation:** The specific context, constraints, and requirements of the application domain.
2.  **What–Why Abstraction:** Mapping domain problems and data into abstract tasks and data types, independent of the domain.
3.  **How Level (Idiom):** Designing the specific visual encoding and interaction methods.
4.  **Algorithm:** The step-by-step computational procedure or formula used to instantiate the idiom.

### 27. List the scalar visualization techniques.
Scalar visualization represents data consisting of single values (scalars) across different points in space.

**Popular Scalar Visualization Techniques:**
1.  **Color Mapping**.
2.  **Contouring**.
3.  **Height plots** (or elevation/carpet plots).

### 28. What is a color map and state its types?
A colormap specifies a mapping between colors and data values, serving as a visual encoding with color. Color mapping maps scalar data to colors, typically by indexing into a Color Look-up Table (CLUT).

**Types of Colormaps:**
1.  **Categorical (Qualitative) Colormap:** Uses color to encode categories and groupings.
2.  **Ordered Colormap:** Appropriate for encoding ordinal or quantitative attributes.
    *   *Sequential:* Ranges from a minimum to a maximum value.
    *   *Diverging:* Has two hues at the endpoints and a neutral color (e.g., white, gray) as a midpoint.
3.  **Bivariate Colormap:** Encodes two separate attributes simultaneously.

### 29. Define contouring
Contouring is a technique for visualizing scalar data. A contour line $C$ is defined as all points $p$ in a dataset $D$ that share the same scalar value, or **isovalue** $x$.

*   **Formula:** $C(x) = \{p \in D | s(p) = x\}$.
*   **Dimensionality:** For a 2D dataset, it creates an **isoline**; for a 3D dataset, it creates a 2D **isosurface**.

### 30. What is a tree in data visualization?
A tree is a specialized type of network visualization. Trees are networks with a **hierarchical structure** that do not have cycles.

*   **Structure:** Each child node has only one parent node pointing to it.
*   **Example:** An organizational chart showing reporting structure.

### 31. Differentiate box plot and histogram visualization
| Feature | Histogram | Box Plot |
| :--- | :--- | :--- |
| **Purpose** | Shows the Probability Density Function (PDF) and the empirical Cumulative Distribution Function (CDF) of data distribution. | Shows summary statistics of data distribution (median, quartiles, range, outliers). |
| **Visualization** | Uses vertical bars where height corresponds to frequency/density. | Uses a box (showing IQR) and whiskers (showing range). |
| **Complexity** | Shows detailed shape and modality of the distribution. | Provides a concise overview, easier for comparing multiple samples. |

### 32. Classify the types of fields in semantics of data abstraction.
Fields represent attribute values associated with cells in a continuous domain. Classification based on attribute semantics includes:

1.  **Scalar Fields:** Unilabiate, with a single value attribute at each point in space (e.g., temperature in a room).
2.  **Vector Fields:** Multivariate, with a list of multiple attribute values at each point, representing both direction and magnitude (like an arrow).
3.  **Tensor Fields:** Have an array of attributes at each point, representing a more complex multivariate mathematical structure than a vector.

### 33. What is a vector glyph?
Vector visualization represents vectors (entities with magnitude and direction). Vector glyphs are **graphical symbols** used to represent these vectors in visualization, often in a compact and interpretable manner.

**Common Glyphs:**
*   **Arrow Glyphs:** Show direction and magnitude.
*   **Bar Glyphs:** Length indicates magnitude and orientation indicates direction.
*   **Cone Glyphs:** Used in 3D, with the tip pointing in the vector direction.

### 34. List the vector properties.
Vectors are entities with two primary properties:

1.  **Magnitude:** The length or size of the vector, calculated using the Euclidean norm.
    *   *Formula (2D):* $|\mathbf{v}| = \sqrt{v_x^2 + v_y^2}$.
2.  **Direction:** The orientation in which the vector points.
    *   *Formula (2D):* $\theta = \tan^{-1}(\frac{v_y}{v_x})$.

---

## Unit 5: Data Analytics Tools and Applications (CO5)

### 35. Write the benefits of Jupyter data analytic tool.
Jupyter Notebook is an open-source web application providing an interactive computational environment for data analysis.

**Key Benefits:**
1.  **Combined Outputs:** It produces documents (notebooks) that combine inputs (code) and outputs (visualizations, equations, statistical modeling, narrative text, and other rich media) into a single file.
2.  **Interactive Computing:** It offers a flexible platform for quick development and iterative analysis.
3.  **Statistical Modeling:** It supports statistical modeling tasks.
4.  **Reproducibility:** The combination of narrative text and executable code allows for reproducible workflows.

### 36. Identify the various Knowledge Discovery-Based Solutions for Identifying Fraud in Healthcare
The provided sources list this as a key topic in Unit 5. Knowledge discovery solutions in healthcare apply data analytics and modeling to large, integrated datasets, enabling applications such as:

*   **Clinical Decision Support Systems (CDSS):** Assisting providers in diagnosing or treatment planning by utilizing patient data.
*   **Pervasive Fraud Detection:** Illustrating the application of data analytics for detecting fraud patterns.

### 37. Enumerate the data types supported in Tableau.
The source lists this as a question, but does not provide the exhaustive list of Tableau field data types. Tableau is generally mentioned as a business intelligence tool used for data visualization.
