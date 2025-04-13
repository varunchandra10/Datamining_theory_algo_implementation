# EDA - Exploratory Data Analysis
EDA is the process of analyzing datasets to summarize their main characteristics, often using visual and statistical methods.

It’s like a detective work phase where you explore the data without making strong assumptions, aiming to understand its structure, distribution, and quirks. In data mining, EDA helps prepare the data for further analysis, such as pattern discovery, predictive modeling, or clustering.

**Key Objectives of EDA:**
- Understand the data’s structure and quality.
- Identify patterns, trends, and relationships.
- Detect anomalies, outliers, or missing values.
- Assess data distributions and variability.
- Generate hypotheses for further analysis.
---
**Why Do We Use EDA?**
- **Get Familiar with the Data:** Understand what the dataset contains, its variables, and their relationships.
- **Ensure Data Quality:** Identify issues like missing values, duplicates, or inconsistencies that could skew results.
- **Guide Modeling Choices:** Reveal whether data is normally distributed, skewed, or has outliers, influencing algorithm selection.
- **Uncover Insights:** Discover hidden patterns or trends that may not be obvious initially.
- **Reduce Errors:** Catch problems early to avoid flawed analyses or models.

**Why Is EDA Important?**
- **Prevents Misleading Conclusions:** Without EDA, you might miss critical issues like outliers or skewed data, leading to incorrect models.
- **Informs Feature Engineering:** Helps decide which variables to transform, combine, or drop.
- Saves Time: Early detection of data issues avoids rework in later stages.
- **Builds Intuition:** Visualizations and summaries provide a deeper understanding of the data’s story.
- **Supports Hypothesis Generation:** EDA sparks ideas for what to test in predictive or statistical modeling.
---
### Types of EDA
1) Univariate Analysis:
   - Focuses on analyzing one variable at a time.
   - A statistical method that examines a single variable in a dataset to understand its characteristics and distribution.

2) Bivariate Analysis:
   - Examines relationships between two variables.
   - Indentifies correlations, dependencies or patterns

3) Multivariate Analysis:
   - Involves analyzing more then 2 variables simultaneously
   - Used to understand complex interactions and dependencies among multiple variables.

| Analysis_Type | Variables | Statistical Measures | Visualizations |
|---------------|-----------|----------------------|----------------|
| Univariate	|1	| Mean, median, mode, variance, SD |Histogram, box plot, bar chart |
|Bivariate|	2|	Correlation (Pearson, Spearman), contingency tables, group stats|	Scatter plot, box plot, stacked bar chart|
Multivariate|	>2|	Correlation matrix, partial correlation, group stats|Heatmap, pair plot, facet grid |

### Data Types:

1) Numerical (Quantitative) Data: Measurable quantities with numbers
     - Continous: range values (height, weight, temperature).
     - Discrete: Countable values (no.of childre, order count).

2) Categorial (Qualitative) Data: Categories or Labels 
     - Nominal: No inherent order ( colors, gender, city names )
     - Ordinal: Has meaningful order ( ratings like low, medium, high )

![ad4ccdc8-b8a4-40b9-91c2-c1b200e0410e](https://github.com/user-attachments/assets/8b5d4d43-06eb-44bb-8dca-88cd92457d57)

## EDA PLOTS AND VISUALIZATIONS
#### 1) Histogram:
   - **Purpose:** Visualize the distribution of a numerical variable (e.g., to check for normality or skewness).
   - **When to Use:** Univariate analysis of continuous data.
   - **Example:** Distribution of “age” in a dataset.
  ```bash
    import pandas as pd
    import matplotlib.pyplot as plt

    # Sample dataset
    data = pd.read_csv('sample_data.csv')  # Replace with your dataset
    plt.hist(data['age'], bins=20, edgecolor='black')
    plt.title('Histogram of Age')
    plt.xlabel('Age')
    plt.ylabel('Frequency')
    plt.show()
  ```
#### 2) Histogram:
   - **Purpose:** Show the spread, central tendency, and outliers of a numerical variable.
   - **When to Use:** Univariate analysis to detect outliers or compare distributions.
   - **Example:** Checking for outliers in “income.”
  ```bash
    import seaborn as sns

    # Box plot
    sns.boxplot(y=data['income'])
    plt.title('Box Plot of Income')
    plt.show()
  ```
#### 3) Bar chart:
   - **Purpose:** Display frequency counts of categorical variables.
   - **When to Use:** Univariate analysis of nominal or ordinal data.
   - **Example:** Count of customers by “region.”
  ```bash
    # Bar chart
    data['region'].value_counts().plot(kind='bar')
    plt.title('Bar Chart of Region')
    plt.xlabel('Region')
    plt.ylabel('Count')
    plt.show()
  ```
#### 4) Pie chart:
   - **Purpose:** Show the proportion of categories in a categorical variable.
   - **When to Use:** Univariate analysis for nominal data (use sparingly, as bar charts are often clearer).
   - **Example:** Proportion of “product types.”
  ```bash
    # Pie chart
    data['product_type'].value_counts().plot(kind='pie', autopct='%1.1f%%')
    plt.title('Pie Chart of Product Types')
    plt.ylabel('')  # Remove y-label for clarity
    plt.show()
  ```
#### 5) Scatter Plot:
   - **Purpose:** Explore relationships between two numerical variables.
   - **When to Use:** Bivariate analysis to check correlations or trends.
   - **Example:** Relationship between “hours studied” and “exam scores.”
  ```bash
    # Scatter plot
    plt.scatter(data['hours_studied'], data['exam_scores'])
    plt.title('Scatter Plot of Hours Studied vs. Exam Scores')
    plt.xlabel('Hours Studied')
    plt.ylabel('Exam Scores')
    plt.show()
  ```
#### 6) Correlation Heatmap:
   - **Purpose:** Visualize correlations between multiple numerical variables.
   - **When to Use:** Multivariate analysis to identify relationships.
   - **Example:** Correlation among “age,” “income,” and “spending.”
  ```bash
    # Correlation heatmap
    corr = data[['age', 'income', 'spending']].corr()
    sns.heatmap(corr, annot=True, cmap='coolwarm')
    plt.title('Correlation Heatmap')
    plt.show()
  ```
#### 7) Pair Plot:
   - **Purpose:** Show pairwise relationships and distributions for multiple numerical variables.
   - **When to Use:** Multivariate analysis for a quick overview.
   - **Example:** Relationships among “age,” “income,” and “spending.”
  ```bash
    # Pair plot
    sns.pairplot(data[['age', 'income', 'spending']])
    plt.show()
  ```
#### 8) Violin Plot:
   - **Purpose:** Combine box plot and density plot to show distribution and probability density.
   - **When to Use:** Univariate or bivariate analysis for numerical data.
   - **Example:** Distribution of “income” across “gender.”
  ```bash
    # Violin plot
    sns.violinplot(x='gender', y='income', data=data)
    plt.title('Violin Plot of Income by Gender')
    plt.show()
  ```
#### 9) Time Series Plot:
   - **Purpose:** Visualize trends or patterns in temporal data.
   - **When to Use:** Univariate or bivariate analysis of time-based data.
   - **Example:** “Sales” over time.
  ```bash
    # Time series plot
    data['date'] = pd.to_datetime(data['date'])  # Ensure date column is datetime
    plt.plot(data['date'], data['sales'])
    plt.title('Time Series Plot of Sales')
    plt.xlabel('Date')
    plt.ylabel('Sales')
    plt.xticks(rotation=45)
    plt.show()
  ```
#### 10) Stacked Bar Plot:
   - **Purpose:** Display the composition of categorical variables across multiple groups, showing how different subcategories contribute to the total within each category.
   - **When to Use:** Bivariate analysis to compare the distribution of one categorical variable across another categorical variable, emphasizing proportions or counts.
   - **Example:** Visualizing the number of employees in different departments, broken down by gender.
  ```bash
    # Sample data preparation (cross-tabulation for stacked bar plot)
    data = pd.crosstab(data['department'], data['gender'])

    # Stacked bar plot
    data.plot(kind='bar', stacked=True, figsize=(8, 6))
    plt.title('Employee Distribution by Department and Gender')
    plt.xlabel('Department')
    plt.ylabel('Count')
    plt.legend(title='Gender')
    plt.show()
  ```
# Table: Analysis, Data Category and Plot Usage

| Analysis Type | Data Category | Recommended Plot | Purpose |
|---------------|---------------|------------------|---------|
| Univariate    | Numerical (Continuous) | Histogram, Box Plot, Violin Plot | Understand distribution, spread, and outliers. |
| Univariate    | Numerical (Discrete) | Histogram, Bar Plot | Visualize frequency or counts. |
| Univariate    | Categorical (Nominal) | Bar Plot, Pie Chart | Show category frequencies or proportions. |
| Univariate    | Categorical (Ordinal) | Bar Plot | Display ordered category counts. |
| Univariate    | Temporal | Line Plot | Identify trends or seasonality. |
| Bivariate     | Numerical vs Numerical | Scatter Plot, Pair Plot, Correlation Heatmap | Explore relationships or correlations. |
| Bivariate     | Numerical vs Categorical | Box Plot, Violin Plot | Compare distributions across categories. |
| Bivariate     | Categorical vs Categorical | Stacked Bar Plot, Heatmap | Analyze co-occurrence or contingency. |
| Multivariate  | Numerical | Pair Plot, Correlation Heatmap | Understand interactions among multiple variables. |
