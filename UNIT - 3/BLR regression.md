As a data science expert, **Bayesian Linear Regression (BLR)** is a sophisticated modeling technique that leverages probabilistic theory to estimate parameters within a linear model, crucially allowing for the quantification of uncertainty.

### Bayesian Linear Regression (BLR) Framework

Bayesian Linear Regression is a specific data modeling technique that applies the principles of **Bayesian inference** for parameter estimation within a linear model, $f(\mathbf{x}) = \theta^T \mathbf{x} + \theta_0$.

The foundational requirement for BLR, or any Bayesian method, is a **Probabilistic Model**, specified by the joint distribution $p(\mathbf{x}, \theta)$ of observed data $\mathbf{x}$ and hidden parameters $\theta$.

#### 1. Parameter Estimation via Bayesian Inference

Unlike Maximum Likelihood Estimation (MLE), which seeks a single point estimate $\theta_{ML}$ that maximizes the likelihood $p(\mathbf{x} | \theta)$, Bayesian inference aims to determine the full **posterior distribution** of the parameters after observing the data.

*   **Bayes' Theorem:** This theorem provides the principled tool to update the probability distribution of parameters $\theta$ after observing data $\mathbf{x}$. It computes the posterior distribution $p(\theta | \mathbf{x})$:

   $$p(\theta | \mathbf{x}) = \frac{p(\mathbf{x} | \theta)p(\theta)}{p(\mathbf{x})}$$

   Where:
  *   $p(\theta | \mathbf{x})$ is the **Posterior distribution** (the specific, updated knowledge about the parameters after seeing the data).
   *   $p(\mathbf{x} | \theta)$ is the **Likelihood function** (the probability of observing the data given the parameters).
   *   $p(\theta)$ is the **Prior distribution** (general knowledge about the parameters before data observation).
   *   $p(\mathbf{x})$ is the **Marginal Likelihood** (the normalization constant, important for model selection).

#### 2. Roles of Prior and Posterior Predictions in BLR

In the context of BLR, the distinction between prior and posterior refers to the knowledge regarding the model parameters ($\theta$) relative to the observed training data ($\mathbf{x}$):

| Prediction Type | Definition | Role in Inference | Source |
| :--- | :--- | :--- | :--- |
| **Prior Prediction** | The probability distribution of the model parameters ($\theta$) **before** observing or incorporating the training data. | Represents initial, general statements about the parameters. | |
| **Posterior Prediction** | The updated probability distribution of the parameters ($\theta$) **after** observing the training data ($\mathbf{x}$). | Represents the specific, updated knowledge used to make final predictions. | |

BLR uses the data to move from a general **prior** distribution to a specific **posterior** distribution. This posterior distribution is then used to make predictions on new, unseen test data.
