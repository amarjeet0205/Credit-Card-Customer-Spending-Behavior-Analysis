# Credit Card Customer Segmentation & Behavioral Insights

This project focuses on understanding customer behavior from credit card usage data through **in-depth Exploratory Data Analysis (EDA)** and **unsupervised clustering techniques**. The aim is to extract meaningful insights from user behavior and then group similar customers together based on those patterns.

---

## Project Overview

Credit card companies generate massive amounts of data on how customers use their cards, repay dues, and utilize their credit limits. This project explores:
- What defines a high-value or risky customer?
- Which customers use one-off purchases vs. installments?
- Are there users consistently maxing out their limits or relying on cash advances?

After deriving such patterns using EDA and feature engineering, I applied **KMeans clustering** to segment customers into similar behavioral groups.

---

## Key Objectives

- Perform EDA to extract and understand core customer behaviors
- Engineer new, insightful features like ratios and aggregates
- Visualize relationships and detect anomalies
- Use clustering to group customers with similar financial behavior
- Interpret cluster profiles using visual tools

---

## Dataset

The dataset contains anonymized credit card data with features like:
- `PURCHASES`, `BALANCE`, `PAYMENTS`, `CREDIT_LIMIT`, `TENURE`
- Cash advances and full payment indicators
- One-off and installment purchase amounts

---

## Exploratory Data Analysis (EDA)

EDA formed the foundation of this project. I derived the following new features to better capture customer behavior:

| Feature | Description |
|--------|-------------|
| `TOTAL_PURCHASES` | Sum of one-off and installment purchases |
| `RATIO_ONEOFF_TO_TOTAL` | Share of one-off purchases out of total |
| `BALANCE_TO_LIMIT_RATIO` | Proportion of credit limit being utilized |
| `CASH_ADVANCE_RATIO` | Share of cash advances relative to credit limit |
| `PRC_FULL_PAYMENT` | Frequency of full payments made |
| `PAYMENTS` | Average payment amount made by the user |

### EDA Techniques Used:
- Distribution plots and boxplots to spot outliers and skewness
- Correlation matrix to identify feature relationships
- Value counts and aggregates to explore categorical trends
- PCA for dimensionality reduction and visualization
- Heatmaps and groupby summaries for pattern recognition

This deep dive helped identify customer types like:
- High spenders vs. low spenders
- Credit-heavy users vs. disciplined payers
- Inactive vs. risky users

---

## Clustering Approach: KMeans

Once EDA and feature engineering were completed, I applied KMeans clustering to segment customers.

### 🧪 Features Used for Clustering:
All newly engineered and normalized:
- `TOTAL_PURCHASES`
- `RATIO_ONEOFF_TO_TOTAL`
- `BALANCE_TO_LIMIT_RATIO`
- `CASH_ADVANCE_RATIO`
- `PRC_FULL_PAYMENT`
- `PAYMENTS`

### Optimal Cluster Selection:

I used a combination of methods to determine the best number of clusters (**k = 6**):

- **Elbow Method**: WCSS showed a slight elbow around **k=6**
- **Silhouette Score**:
  - Score for k=6 = **0.3545** (not the highest, but close)
- **Calinski-Harabasz Score**:
  - One of the highest score for **k=6**
- **Davies-Bouldin Score**:
  - **Lowest** value for **k=6**, indicating well-separated clusters

📌 Although k=3 had the highest silhouette score (0.3982), the **overall combination of metrics** pointed toward **k=6** as a strong and balanced choice.

### Outlier Handling:
Cluster 1 had only 1 customer — it was dropped from further analysis to avoid noise.

---

## Cluster Profiling & Visualization

After clustering, I performed:
- **PCA-based cluster visualization** to observe separation
- **Heatmaps of normalized feature means** to understand each cluster’s traits
- **Boxplots per feature per cluster** for distribution comparison

These visualizations helped interpret each segment, such as:
- Customers with high total purchases and full payments (potential premium users)
- Users relying on cash advances and low payments (possible risky accounts)
- Moderate users with balanced usage and repayments

---

## Tech Stack

- **Python**
- **Libraries**: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`
- **Clustering**: KMeans, PCA, scaling
- **Evaluation Metrics**: WCSS, Silhouette, Calinski-Harabasz, Davies-Bouldin

---

## Project Structure

