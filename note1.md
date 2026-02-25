# Methodology Summary

## 1. Data Structure Examination

The dataset was first examined using structural inspection methods to understand the number of observations, data types, and overall data completeness.

The following functions were used:

- `df.info()` to identify variable types (categorical vs numerical)
- `df.describe()` to obtain summary statistics for continuous variables
- `df.isnull().sum()` to verify the absence of missing values
- `df.duplicated().sum()` to check for duplicate records

This step ensured data quality and confirmed that all 2000 observations were complete, unique, and suitable for statistical analysis.

---

## 2. Measures of Central Tendency and Dispersion

To summarize continuous variables (`views`, `likes`, `shares`, `comments`, `engagement_rate`, `sentiment_score`), the following measures were calculated:

- Mean (average value)
- Median (middle value)
- Standard deviation (data spread)
- Minimum and maximum values
- Quartiles (25th, 50th, 75th percentiles)

Variance was computed using the sample variance formula:

Var(X) = Σ (Xi − μ)² / (n − 1)

These statistics helped assess variability in content popularity and engagement metrics, particularly identifying high dispersion due to viral posts.

---

## 3. Distribution Analysis

To understand the shape and spread of numerical variables, several visualization techniques were used:

- Histograms (`sns.histplot`) to observe distribution shape and skewness
- Boxplots (`sns.boxplot`) to detect outliers and examine interquartile range
- Violin plots (`sns.violinplot`) to analyze density and symmetry

This analysis helped determine whether variables were normally distributed or skewed, and whether extreme values influenced overall dispersion.

---

## 4. Z-Score Standardization

Because variables were measured on different scales (e.g., views in millions and sentiment scores between -1 and 1), Z-score normalization was applied using `StandardScaler` from `sklearn`.

z = (X − μ) / σ

This transformation standardized all numerical variables to:

- Mean = 0
- Standard deviation = 1

Standardization enabled fair comparison of variability across engagement metrics and improved visualization clarity.

---

## 5. Correlation Analysis (Continuous Variables)

To examine linear relationships between engagement metrics and views, Pearson correlation was computed using:

`df.corr()`

The Pearson correlation coefficient is defined as:

r = Cov(X, Y) / (σX σY)

Correlation strength was visualized using a heatmap and scatter plots.

This analysis identified which engagement metrics had the strongest association with content popularity.

---

## 6. Scatter Plot Analysis

Scatter plots were generated for:

- Likes vs Views
- Shares vs Views
- Comments vs Views

These plots visually confirmed:

- Linearity of relationships
- Strength and direction of association
- Presence of clusters or outliers

---

## 7. Group-Based Descriptive Comparison (Categorical Variables)

Categorical variables such as `platform` and `sentiment_category` were analyzed using:

- `df.groupby()` to calculate mean views per category
- Boxplots to visualize distribution differences between groups

This step provided descriptive insights into whether content popularity differed across platforms or sentiment groups before conducting formal hypothesis testing (ANOVA).

