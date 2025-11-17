# K-Nearest_Neighbors
1) What is KNN — intuition

KNN is a simple instance-based (lazy) supervised learning method.
Classification: predict the class of a new point by looking at the classes of the k closest training points and taking a majority vote (or weighted vote).

Regression: predict the target as the average (or weighted average) of the targets of the k nearest neighbors.
Key idea: similar inputs → similar outputs.

2) Algorithm (high level)

Training: store the training set (no model fitting beyond possibly indexing).
Prediction for a query point x:
Compute distance between x and every training sample.
Select the k training points with smallest distances.
For classification: majority vote (or weighted vote). For regression: average (or weighted average).
Return prediction.

3) Choosing k

Small k (e.g., 1): low bias, high variance; can overfit/noisy.
Large k: smoother decision boundary, more bias, less variance; risk underfitting and favoring majority class.
Common approach: use cross-validation to choose k (odd k for binary classification to avoid ties). Try range (1, 3, 5, 7, … up to sqrt(n) or so).

4) Strengths & weaknesses

Strengths:
Simple, intuitive, no training time (or minimal).
Non-parametric — can model complex decision boundaries.
Works well with small datasets and well-scaled features.

Weaknesses:
Slow prediction on large datasets.
Sensitive to irrelevant/noisy features (feature selection helps).
Curse of dimensionality: in high d, distances become less meaningful, performance drops.
Imbalanced classes: majority class can dominate votes (use weighting or class priors).

5) KNN for classification vs regression

Classification: majority vote, tie-breaking strategies (choose lower-distance sum, or reduce k).
Regression: average of neighbor targets; optionally distance-weighted average.

6) Practical tips & tricks

Always scale features.
Use cross-validation to pick k and the distance metric.
Consider dimensionality reduction (PCA, feature selection) before KNN for high-dim data.
If classes imbalanced, consider stratified sampling, class weights, or smaller k.
Use KD/Ball trees for moderate dimensions, or approximate methods for large-scale tasks.
For categorical features, consider combining specialized distance measures (e.g., Gower distance) or encoding carefully.

