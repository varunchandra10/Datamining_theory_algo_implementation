
# Naïve Bayes Classifier

## What is Naïve Bayes?

Naive Bayes is a **probabilistic classifier** based on **Bayes’ Theorem**, assuming strong (naive) independence between features.

It calculates the probability of each class given a data point and chooses the class with the highest probability.

---

### Why it is called Naives Bayes?
The Naïve Bayes algorithm is comprised of two words Naïve and Bayes, Which can be described as:

- #### Naïve:
  It is called Naïve because it assumes that the occurrence of a certain feature is independent of the occurrence of other features. Such as if the fruit is identified on the bases of color, shape, and taste, then red, spherical, and sweet fruit is recognized as an apple. Hence each feature individually contributes to identify that it is an apple without depending on each other.
- #### Bayes:
  It is called Bayes because it depends on the principle of Bayes' Theorem.

## Bayes’ Theorem `P(A|B) = P(B|A).P(A)/P(B)`

Where:
- P(A|B) : Posterior probability (what we want to predict)
- P(B|A): Likelihood (how likely data belongs to class)
- P(A): Prior probability of the class
- P(B): Evidence (common across classes, can be ignored when comparing)

## Example Problem:
Training data:
| Rid | Age        | Income  | Student | Credit_rate     | Buys_computer(class)|
|-----|------------|---------|---------|-----------------|---------------------|
| 1   | Youth      | High    | No      | Fair            | No
| 2   | Youth      | High    | No      | Excellent       | No
| 3   | Middle Age | High    | No      | Fair            | Yes
| 4   | Senior     | Medium  | No      | Fair            | Yes
| 5   | Senior     | Low     | Yes     | Fair            | Yes
| 6   | Senior     | Low     | Yes     | Excellent       | No
| 7   | Middle Age | Low     | Yes     | Excellent       | Yes
| 8   | Youth      | Medium  | No      | Fair            | No
| 9   | Youth      | Low     | Yes     | Fair            | Yes
| 10   | Senior    | Medium  | Yes     | Fair            | Yes
| 11   | Youth     | Medium  | Yes     | Excellent       | Yes
| 12   | Middle Age | Medium | No      | Excellent       | Yes
| 13   | Middle Age | High   | Yes     | Fair            | Yes
| 14   | Senior     | Medium | No      | Excellent       | No

Test data:
x = [ Age='Youth', Income='Medium', Student='Yes', Credit_rate='Fair' ]

- Compute P ( Yes | x ) and P ( No | x )
    - P ( Yes| x ) = P ( x | Yes ) . P ( Yes ) / P ( x )
    - P ( No | x ) = P ( x | No ) . P ( No ) / P ( x )

P ( Yes ) = 9/14 and P ( No ) = 5/14
- Count of Yes = 9 in 14 Tuples
- Count of No = 5 in 14 Tuples

Denominator is same for both no it is neglected

For class Yes: ( Likelihood )
| Attribute   | Value  | Count of Yes | Likelihood |
|-------------|--------|--------------|------------|
| Age         | Youth  | 2            | 2 / 9
| Income      | Medium | 4            | 4 / 9
| Student     | Yes    | 6            | 6 / 9
| Credit_rate | Fair   | 6            | 6 / 9

P ( x | Yes ) = 2 / 9 * 4 / 9 * 6 / 9 * 6 / 9 = 0.04

P ( Buys_computer = Yes | Attribute ) = P ( x | Yes ) * P( Yes )

 = 0.04 * 9 / 14

 = 0.028   


For class No: ( Likelihood )
| Attribute   | Value  | Count of No  | Likelihood |
|-------------|--------|--------------|------------|
| Age         | Youth  | 3            | 3 / 5
| Income      | Medium | 2            | 2 / 5
| Student     | Yes    | 1            | 1 / 5
| Credit_rate | Fair   | 2            | 2 / 5

P ( x | Yes ) = 3 / 5 * 2 / 5 * 1 / 5 * 2 / 5 = 0.0192

P ( Buys_computer = No | Attribute ) = P ( x | No ) * P( No )

 = 0.0192 * 5 / 14
 
 = 0.0068

∴ 0.028 > 0.0068, so when [ Age='Youth', Income='Medium', Student='Yes', Credit_rate='Fair' ] Buys_Computer = Yes

## Types of Naive Bayes Classifiers

| Type               | Description |
|--------------------|-------------|
| Gaussian NB        | For continuous data (assumes features follow a normal distribution) |
| Multinomial NB     | For discrete counts (e.g., word frequencies in text) |
| Bernoulli NB       | For binary features (0s and 1s) |
| Categorical NB     | For categorical features (e.g., colors, weather types) – introduced in `sklearn` 0.22 |

---

## Common Use Cases

- Email spam detection
- Sentiment analysis
- Document classification
- Medical diagnosis
- Weather prediction
