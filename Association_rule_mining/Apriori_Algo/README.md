# Apriori Algorithm

## What is the Apriori Algorithm?
The Apriori Algorithm is a classic algorithm in data mining used to:
- Discover frequent itemsets in a transaction dataset.
- Use a "Bottom-up" (breadth-first) approach with candidate generation.
- Generate association rules based on (user-defined):
  - Minimum Support
  - Minimum Confidence

It uses the principle:  
**"All subsets of a frequent itemset must also be frequent."**

Apriori is based on the **Apriori property**: 
- if an itemset is frequent, then all of its subsets must also be frequent. This reduces the search space and improves efficiency, although it still requires multiple scans of the database. The algorithm is best suited for smaller datasets or as a learning foundation for more advanced methods like FP-Growth.

---

## 🎯 Goal of Apriori
From a list of transactions, identify strong rules like:

**If {Bread, Butter} is bought → Milk is also likely to be bought**

---

## Key Steps of the Algorithm:

1️⃣ Generate frequent 1-itemsets.  
2️⃣ Use those to generate candidate 2-itemsets.  
3️⃣ Prune candidates whose subsets are not frequent.  
4️⃣ Repeat for k-itemsets until no more candidates.  
5️⃣ Generate association rules from the frequent itemsets.

---

## 📝 Example

Consider this as an example dataset:

| TID | Items               |
|-----|---------------------|
| T1  | Milk, Bread, Butter |
| T2  | Bread, Butter       |
| T3  | Milk, Bread         |
| T4  | Milk, Butter        |
| T5  | Bread, Butter       |

Given parameters:  
**Minimum Support = 60% (3 out of 5 transactions)**  
**Minimum Confidence = 70%**

---

### 1️⃣ Step: Itemset of dataset - C1

| Itemset | 
|---------|
| Milk    |
| Bread   |
| Butter  |

---

### 2️⃣ Step: Scan the C1 to count the items

| Itemset | Count |
|---------|-------|
| Milk    | 3     |
| Bread   | 4     |
| Butter  | 4     |

---

### 3️⃣ Step: Prune based on support to get L1

| Itemset | Count | Support | Frequent? |
|---------|-------|---------|-----------|
| Milk    | 3     | 60%     | ✅        |
| Bread   | 4     | 80%     | ✅        |
| Butter  | 4     | 80%     | ✅        |

---

### 4️⃣ Step: Candidate 2-Itemsets (C2) [L1 join L1]

| Itemset         |
|-----------------|
| {Milk, Bread}   |
| {Milk, Butter}  |
| {Bread, Butter} |

---

### 5️⃣ Step: Scan the C2 to count the items

| Itemset          | Count |
|------------------|-------|
| {Milk, Bread}    |   2   |
| {Milk, Butter}   |   2   |
| {Bread, Butter}  |   3   |

---

### 6️⃣ Step: Prune based on support to get L2

| Itemset         | Count | Support | Frequent? |
|-----------------|-------|---------|-----------|
| {Milk, Bread}   |   2   | 40%     | ❌        |
| {Milk, Butter}  |   2   | 40%     | ❌        |
| {Bread, Butter} |   3   | 60%     | ✅        |

---

### 7️⃣ Step: Candidate 3-Itemsets (C3) [L2 join L2]
To form 3-itemsets, we need:
- At least 2 itemsets in L2 that can be joined.
- All subsets of size 2 of the 3-itemset must exist in L2.

Since only one itemset is frequent in L2, no 3-itemsets can be generated.

---

## ✅ Final Frequent Itemsets

| Itemset         | Support |
|-----------------|---------|
| {Bread, Butter} | 60%     |

---

## 🧾 Association Rules from {Bread, Butter} 

We will calculate Confidence for final itemset to determine the strength of association rules.

Formula:  
**Confidence (A → B) = Support_count(A ∪ B) / Support_count(A)**

1. **Bread → Butter**
   - A = Bread, B = Butter  
   - Support of {Bread, Butter} = 60%  
   - Support of Bread = 4  
   - Confidence = 3/4 = 75% ✅

2. **Butter → Bread**
   - A = Butter, B = Bread  
   - Support of {Bread, Butter} = 60%  
   - Support of Butter = 4  
   - Confidence = 3/4 = 75% ✅

**Resulting Strong Rules:**
- If a customer buys bread, they are 75% likely to also buy butter.
- If a customer buys butter, they are 75% likely to also buy bread.

---

## 📈 (Optional) Lift Metric

**Lift(A → B) = Confidence(A → B) / Support(B)**  
Lift > 1 implies a strong positive correlation.

---

## 🔚 Summary

- Apriori algorithm finds frequent itemsets using iterative (level-wise) candidate generation.
- It prunes itemsets based on the Apriori property (subset rule).
- It generates strong rules using support and confidence thresholds.
- Best for small to medium datasets; may not scale well for very large datasets.
