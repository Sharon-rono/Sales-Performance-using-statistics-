# Sales-Performance-using-statistics-
A Python-based exploratory data analysis (EDA) and statistical inference project using sales transaction data across regions and store types in Kenya.  
# Sales Statistics Analysis  

A Python-based exploratory data analysis (EDA) and statistical inference project using sales transaction data across regions and store types in Kenya.

---

## Dataset

**File:** `statistics_sales_project_data.csv`

**Records:** 1,200 sales transactions (2023)

| Column | Type | Description |
|---|---|---|
| `date` | datetime | Transaction date |
| `store_type` | string | Online or Physical |
| `region` | string | Sales region (Nairobi, Coast, Western, Rift Valley) |
| `marketing_campaign` | string | Whether a campaign was active (Yes/No) |
| `units_sold` | integer | Number of units sold per transaction |
| `revenue` | float | Revenue generated (KES) |

---

## Project Structure

### 1. Data Loading & Exploration
- Loads the CSV using `pandas`
- Previews the first 5 rows with `.head()`
- Generates descriptive statistics with `.describe()`
  - Mean revenue: **KES 8,271.97**
  - Median revenue: **KES 7,723.33**
  - Revenue mode: **0.0** (indicating zero-revenue transactions exist)
  - Units sold range: 0–15

### 2. Data Cleaning
- Converts the `date` column from `object` to `datetime64` using `pd.to_datetime()`

### 3. Visualizations

| Chart | Description |
|---|---|
| **Revenue Histogram** | Distribution of revenue across all transactions |
| **Revenue Over Time** | Line plot showing daily revenue trend |
| **Revenue by Store Type** | Bar chart comparing Online vs Physical store revenue |
| **Revenue by Region (Box Plot)** | Revenue spread across Nairobi, Coast, Western, and Rift Valley |
| **Sample Mean vs Sample Size** | Demonstrates the Law of Large Numbers |
| **Sampling Distribution Histogram** | 200 bootstrap samples (n=30) illustrating the Central Limit Theorem |

---

## Statistical Concepts Covered

### Population vs Sample
- **Population:** All possible company sales transactions
- **Sample:** The 1,200-record dataset drawn from that population

### Sampling Bias Discussion
- **Assumption:** Only urban stores were sampled
- **Bias identified:** Selection bias — rural stores are excluded
- **Impact:** Overestimates performance; leads to poor demand forecasting
- **Proposed fix:** Stratified random sampling by region type, sampled proportionally

### Hypothesis Testing — Marketing Campaign Effectiveness

**Question:** Does the marketing campaign significantly increase mean revenue?

| Group | Count | Mean Revenue (KES) |
|---|---|---|
| Campaign (Yes) | 447 | 8,977.58 |
| No Campaign (No) | 753 | 7,853.11 |

- **Test:** Independent samples t-test (`scipy.stats.ttest_ind`)
- **t-statistic:** 4.43
- **One-tailed p-value:** 0.000005
- **Conclusion:** p < 0.05 → **Reject the null hypothesis** — the marketing campaign significantly increases mean revenue

### Error Types
| Error | Definition | Business Impact |
|---|---|---|
| **Type I** | Rejecting a true null hypothesis | Company invests in a campaign that doesn't actually work |
| **Type II** | Failing to reject a false null hypothesis | Company abandons a campaign that does work, losing potential revenue |

---

## Requirements

```
pandas
matplotlib
seaborn
scipy
```

---
