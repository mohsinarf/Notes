# Kalman Filter

## Data Fusion
Data funsion is the process of integrating multiple data sources to form useful information that is more accurate and consistent than original data sources.
 
## What is the Kalman Filter?
- Recursive estimator that solves the 'linear-quadratic-estimation-problem'.

### Variance

The variance of a random variable \( X \) is denoted as \( \text{Var}(X) \) and is calculated as:

\[ \text{Var}(X) = \frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2 \]

Where:
- \( x_i \) represents each individual observation in the dataset.
- \( \mu \) is the mean of the dataset.
- \( n \) is the number of observations.

### Covariance

The covariance between two random variables \( X \) and \( Y \) is denoted as \( \text{Cov}(X, Y) \) and is calculated as:

\[ \text{Cov}(X, Y) = \frac{1}{n} \sum_{i=1}^{n} (x_i - \bar{X})(y_i - \bar{Y}) \]

Where:
- \( x_i \) and \( y_i \) are individual observations in the datasets of \( X \) and \( Y \), respectively.
- \( \bar{X} \) and \( \bar{Y} \) are the means of \( X \) and \( Y \), respectively.
- \( n \) is the number of observations.

### Covariance Matrix

The covariance matrix, denoted as \( \Sigma \), for a set of \( p \) random variables \( X_1, X_2, ..., X_p \) is an \( p \times p \) matrix where the diagonal elements are the variances of each variable, and the off-diagonal elements are the covariances between each pair of variables. It can be represented as:

\[ \Sigma = \begin{bmatrix}
\text{Var}(X_1) & \text{Cov}(X_1, X_2) & \cdots & \text{Cov}(X_1, X_p) \\
\text{Cov}(X_2, X_1) & \text{Var}(X_2) & \cdots & \text{Cov}(X_2, X_p) \\
\vdots & \vdots & \ddots & \vdots \\
\text{Cov}(X_p, X_1) & \text{Cov}(X_p, X_2) & \cdots & \text{Var}(X_p)
\end{bmatrix} \]
