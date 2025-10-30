As a data science expert, any machine learning (ML) pipeline is defined by the interaction of three fundamental components: **Data, Models, and Learning**. Understanding these components is essential, as the goal is always to find "good models" that perform well on unseen data.

### Core Components of a Machine Learning System

The three major components of a machine learning system are Data, Models, and Learning.

#### 1. Data ($\mathbf{X}$ and $\mathbf{Y}$)

Data is the foundation of the system and must be readable by a computer, typically represented adequately in a numerical and tabular format.

**Key Concepts of Data Representation:**

*   **Structure:** Data is usually tabular, where each row represents a particular instance or example ($\mathbf{x}_n$), and each column represents a feature, attribute, or covariate.
*   **Vector Representation:** Each input $\mathbf{x}_n$ is assumed to be a $D$-dimensional vector of real numbers. The table of all examples is often concatenated and written as $\mathbf{X} \in \mathbb{R}^{N \times D}$.
*   **Supervised Learning:** In supervised learning, the data consists of example-label pairs $\{(\mathbf{x}_1, \mathbf{y}_1), \dots, (\mathbf{x}_N, \mathbf{y}_N)\}$, where $\mathbf{y}_n$ is the label (also called the target or response variable) associated with each example.
*   **Preparation (Standardization):** Before proceeding, it is often necessary to shift and scale all data columns such that they have an empirical mean of 0 and an empirical variance of 1.

#### 2. Models (Predictive Structures)

Models represent the predictive structure used to map input data to an output. The sources define two major approaches to models:

**A. Models as Functions (Predictors)**
In this non-probabilistic view, the model is a predictor function $f$ that takes an input vector of features and produces an output, typically a single real-valued scalar output.

*   **Definition:** A predictor is a function $f: \mathbb{R}^D \rightarrow \mathbb{R}$, where the input vector $\mathbf{x}$ is $D$-dimensional.
*   **Example (Linear Function):** The special case of linear functions is often used, defined as:
    $f(\mathbf{x}) = \theta^T \mathbf{x} + \theta_0$
    where $\theta$ and $\theta_0$ are unknown parameters.

**B. Models as Probabilistic Distributions**
This approach views predictors as probabilistic models describing the distribution of possible functions. This framework is essential for quantifying the effect of noise and expressing uncertainty about the prediction for a particular test data point.

*   **Definition:** Probabilistic models are often viewed as multivariate probability distributions that represent the uncertain aspects of an experiment.
*   **Utility:** This model type is required when using advanced techniques like Bayesian inference.

#### 3. Learning (Finding Parameters)

Learning is the core goal of finding a model and its corresponding parameters ($\theta$) such that the resulting predictor performs well on unseen data.

The learning process is divided into three conceptually distinct algorithmic phases:

1.  **Prediction or Inference:** This phase involves using the trained predictor (where the parameters and model choice are already fixed) on previously unseen test data.
2.  **Training or Parameter Estimation:** This involves adjusting the predictive model based on the training data. Strategies include finding a **point estimate** (maximizing some measure of quality) or using **Bayesian inference**.
3.  **Hyperparameter Tuning or Model Selection:** This phase involves making high-level modeling decisions about the structure of the predictor (e.g., choosing the number of components or the class of probability distributions to consider), as this choice can significantly affect performance.

**Algorithmic Learning Workflow:**

```ascii
+-----------------+    +--------------------------+    +--------------------+
| 1. Data Input (X, Y)| -> | 2. Training/Param. Estimation| -> | 3. Hyperparameter Tuning|
+-----------------+    | (Finding optimal Theta)  |    | (Optimizing structure)|
                       +--------------------------+    +--------------------+
                                      |
                                      V
                             +--------------------+
                             | 4. Prediction/Inference|
                             | (Testing on unseen data)|
                             +--------------------+
```
