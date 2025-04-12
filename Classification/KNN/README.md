# KNN
KNN is a **Instance-based**, **parameterized**, **lazy learning** algorithm. It does not assume anything about the underlying data distribution and stores the entire training dataset. When a new data point needs to be classified or predicted, KNN:
- Looks at the K closest data points (neighbors) in the training set.
- For classification: It assigns the most common class among the neighbors.
- For regression: It returns the average (or weighted average) of the values of neighbors.

---
### Steps in KNN
### 1) Choose the value of K:
- K is the no.of nearest neighbours to consider
- Small k -> overfitting
- Large k -> underfittng
- Usually Odd numbers (to avoid ties)

### 2) Calulate distance
for sample, compute the distance to every point in training dataset

- **Metrics:**

   - `Euclidean Distance: d(x, y) = √[ (x₂ − x₁)² + (y₂ − y₁)² ..... ]`

   - `Manhattan Distance: d(p, q) = |(p₁ − q₁) + (p₂ − q₂) + ... + (pₙ − qₙ)|`

   - `Minskowski: d(p, q) = (∑ᵢ₌₁ⁿ |pᵢ − qᵢ|ʳ)¹⁄ʳ`

### 3)  Sort the Distances
- Sort all training examples based on their distance from the test point.
- Choose the K nearest neighbors.

### 4) Voting or Averaging
- Classification: Take a majority vote among K nearest labels.
- Regression: Take the average value of the K nearest points.

### 5) Predict the Label
- For classification: Choose the class with the highest vote.
- For regression: Return the computed average value.

### 6) Evaluate the Model - Use evaluation metrics like:
- Accuracy, Precision, Recall, F1-Score (for classification)
- MSE, RMSE, MAE (for regression)

## Example Problem:
Training data:
| Rid  | Height(cm) | Weight(Kg)  | Class
|------|------------|-------------|---------|
| 1    | 158        | 58          |  M
| 2    | 158        | 59          |  M
| 3    | 158        | 63          |  M
| 4    | 160        | 59          |  M
| 5    | 160        | 60          |  M
| 6    | 163        | 61          |  M
| 7    | 163        | 64          |  M
| 8    | 160        | 64          |  M
| 9    | 163        | 64          |  L
| 10   | 165        | 61          |  L
| 11   | 165        | 62          |  L
| 12   | 165        | 65          |  L
| 13   | 168        | 62          |  L
| 14   | 168        | 63          |  L
| 15   | 168        | 66          |  L
| 16   | 170        | 63          |  L
| 17   | 170        | 64          |  L
| 18   | 170        | 68          |  L

Test data:
x2 = 161 cm, y2 = 61kg, class=?, K=5

| Rid  | x1   | y1   | distance                                     | Class
|------|------|------|----------------------------------------------|--------
| 1    | 158  | 58   | d = √ ( 161 - 158 )² + ( 61 - 58 )² = `4.24` | M
| 2    | 158  | 59   | d = √ ( 161 - 158 )² + ( 61 - 59 )² = `3.60` | M
| 3    | 158  | 63   | d = √ ( 161 - 158 )² + ( 61 - 63 )² = `3.60` | M
| 4    | 160  | 59   | d = √ ( 161 - 160 )² + ( 61 - 59 )² = `2.23` | M
| 5    | 160  | 60   | d = √ ( 161 - 160 )² + ( 61 - 60 )² = `1.41` | M
| 6    | 163  | 61   | d = √ ( 161 - 163 )² + ( 61 - 61 )² = `2`    | M
| 7    | 163  | 64   | d = √ ( 161 - 163 )² + ( 61 - 64 )² = `3.60` | M
| 8    | 160  | 64   | d = √ ( 161 - 160 )² + ( 61 - 64 )² = `3.16` | M
| 9    | 163  | 64   | d = √ ( 161 - 163 )² + ( 61 - 64 )² = `3.60` | L
| 10   | 165  | 61   | d = √ ( 161 - 165 )² + ( 61 - 61 )² = `4`    | L
| 11   | 165  | 62   | d = √ ( 161 - 165 )² + ( 61 - 62 )² = `4.123`| L
| 12   | 165  | 65   | d = √ ( 161 - 165 )² + ( 61 - 65 )² = `5.65` | L
| 13   | 168  | 62   | d = √ ( 161 - 168 )² + ( 61 - 62 )² = `7.07` | L
| 14   | 168  | 63   | d = √ ( 161 - 168 )² + ( 61 - 63 )² = `7.28` | L
| 15   | 168  | 66   | d = √ ( 161 - 168 )² + ( 61 - 66 )² = `9.60` |  L
| 16   | 170  | 63   | d = √ ( 161 - 170 )² + ( 61 - 63 )² = `9.21` | L
| 17   | 170  | 64   | d = √ ( 161 - 170 )² + ( 61 - 64 )² = `9.481`| L
| 18   | 170  | 68   | d = √ ( 161 - 170 )² + ( 61 - 64 )² = `11.40`| L

Sort the distances and the test data will fall under 
- k = 5
  - 1.41 class - M
  -   2.23 class - M
  -   2.16 class - M
  -   3.60 class - M
  -   3.60 class - M

so 161cm and 61kg falls under class-M




