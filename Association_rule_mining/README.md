# Association Rule Mining

Association Rule Mining (ARM) is a data mining technique **used to discover interesting relationships, patterns, or associations among a set of items in large datasets**. 
It is widely used in market basket analysis,where the goal is to find associations between items bought together.

It finds rules of the form:

IF A THEN B or  A => B where :
- A is antecedent (left-hand side)
- B is consequent (right-hand side)

##  Algorithms in Association Rule Mining

### 1. Apriori Algorithm - github_link

**Overview:**  
- Classic bottom-up algorithm to find frequent itemsets.  
- Based on the Apriori property: all non-empty subsets of a frequent itemset must also be frequent.

**Steps:**  
1. Find frequent 1-itemsets.
2. Generate candidate 2-itemsets and prune infrequent ones.
3. Repeat until no more frequent itemsets.
4. Generate association rules from frequent itemsets.

**Pros:** Simple and easy to implement.  
**Cons:** Requires multiple database scans; slow with large datasets.

---

### 2. FP-Growth (Frequent Pattern Growth) - github_link

**Overview:**  
- More efficient than Apriori.  
- Uses a compact structure called the FP-tree.  
- No candidate generation required.

**Steps:**  
1. Scan data to find frequent items.  
2. Build the FP-tree.  
3. Recursively mine conditional FP-trees.

**Pros:** Faster, scalable for large datasets.  
**Cons:** FP-tree can be complex and memory-intensive.

---

### 3. ECLAT (Equivalence Class Clustering and bottom-up Lattice Traversal) - github_link

**Overview:**  
- Uses a vertical database layout (items → transaction ID sets).  
- Counts support by intersecting TID sets.  
- Depth-first search approach.

**Pros:** Fast for dense datasets.  
**Cons:** Not optimal for sparse data.

---

### 4. AIS Algorithm - github_link

**Overview:**  
- Early algorithm; generates candidate itemsets dynamically while scanning.  
**Cons:** Inefficient; rarely used today.

---

### 5. SETM (Set-Oriented Mining) - github_link

**Overview:**  
- Stores itemsets with transaction IDs to count support.  
**Cons:** Slower than Apriori and FP-Growth.

---

##  Comparison Table

| Algorithm  | Database Scans | Candidate Generation | Data Format | Pros                            | Cons                                 |
|------------|----------------|----------------------|-------------|----------------------------------|--------------------------------------|
| Apriori    | Multiple       | Yes                  | Horizontal  | Simple, widely studied           | Slow, many scans                     |
| FP-Growth  | 2              | No                   | Tree-based  | Faster, no candidates            | Tree can be complex in dense data   |
| ECLAT      | 1              | No                   | Vertical    | Fast, DFS, efficient             | Not great for sparse data           |
| AIS        | Many           | Yes                  | Horizontal  | Historical interest only         | Inefficient                         |
| SETM       | Many           | Yes                  | Horizontal  | Some improvements over AIS       | Still not ideal                     |


---

## 📌 Key Concepts

### 1. Support

**Definition:**  
Support tells us how frequently a particular itemset appears in the dataset.

**Formula:**  
$$
\text{Support}(A \Rightarrow B) = \frac{\text{Number of transactions containing both } A \text{ and } B}{\text{Total number of transactions}}
$$


---

### 2. Confidence

**Definition:**  
Confidence measures the reliability of the rule. It tells us the probability of item B being purchased when item A is purchased.

**Formula:**  
$$
\text{Confidence}(A \Rightarrow B) = \frac{\text{Support}(A \cup B)}{\text{Support}(A)}
$$
---

### 3. Lift

**Definition:**  
Lift tells us how much more likely item B is to be purchased when A is purchased, compared to when B is purchased independently.

**Formula:**  
$$
\text{Lift}(A \Rightarrow B) = \frac{\text{Confidence}(A \Rightarrow B)}{\text{Support}(B)}
$$

**Conditions:**  
- Lift = 1 → A and B are independent  
- Lift > 1 → Positive correlation  
- Lift < 1 → Negative correlation

---

## Summary Table

| Metric     | Meaning                                 | Formula                                              | Goal               |
|------------|------------------------------------------|------------------------------------------------------|--------------------|
| Support    | Frequency of itemset in dataset          | Support(A ∪ B) = count(A ∪ B) / total transactions   | Filter frequent sets|
| Confidence | Likelihood of B given A                  | Confidence = Support(A ∪ B) / Support(A)             | Measure reliability|
| Lift       | Strength of association between A and B  | Lift = Confidence / Support(B)                       | Measure correlation|

---

**Date Created:** 2025-04-08
