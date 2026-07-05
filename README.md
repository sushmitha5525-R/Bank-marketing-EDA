# Bank-marketing-EDA
# Bank Marketing Campaign — EDA & Customer Segmentation

## Overview
This project analyzes direct marketing campaign data from a Portuguese bank to understand what drives customers to subscribe to a term deposit, and to segment customers into groups based on campaign behavior. The goal is to turn raw campaign data into clear, actionable targeting recommendations — the kind of analysis a retail banking or marketing analytics team would use to plan future campaigns.

## Dataset
- **Source:** [Bank Marketing Data Set — Kaggle](https://www.kaggle.com/datasets/ruthgn/bank-marketing-data-set) (originally from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/222/bank+marketing))
- **Size:** ~41,000 records, 20 features
- **Target:** `y` — whether the client subscribed to a term deposit (yes/no)
- Features span client demographics (age, job, marital status, education), financial status (loan/default history), campaign contact details (channel, month, number of contacts), and macroeconomic indicators (euribor rate, employment variation rate).

## Objectives
1. Explore the dataset to understand customer demographics and campaign patterns
2. Identify which features are associated with subscription success
3. Segment customers using clustering to find distinct behavioral groups
4. Translate findings into practical campaign targeting recommendations

## Approach
1. **Data overview** — checked structure, data types, and category values (dataset uses `"unknown"` instead of nulls)
2. **Univariate analysis** — examined distributions of age, contact frequency, and campaign-related fields
3. **Bivariate analysis** — compared subscription rates across demographic and campaign variables
4. **Correlation analysis** — used a correlation heatmap for numeric features and chi-square tests for categorical features against the target
5. **Customer segmentation** — applied K-Means clustering (with PCA for visualization) on contact behavior and macroeconomic context to group customers into four segments
6. **Business interpretation** — profiled each segment and translated the patterns into targeting recommendations

## Key Findings
- The dataset is imbalanced: only about 11% of customers subscribed, which is typical for cold outbound campaigns and shaped how the segmentation was interpreted.
- Customers who had been **contacted in a previous campaign converted far more often** (~27%) than first-time contacts, even with fewer total touches.
- One segment showed **heavy over-contacting** (11+ calls on average) with the **lowest** conversion rate of any group — a clear diminishing-returns pattern.
- Two segments received similar (low) contact effort but had very different outcomes (21% vs. 5% conversion), suggesting factors beyond contact volume — such as job type or timing — play a meaningful role and are worth targeting more precisely.

## Recommendations
- Prioritize re-engagement campaigns for customers with prior contact history — they convert at the highest rate with the least effort.
- Cap the number of contact attempts for cold, unresponsive leads; past a certain point, more calls appear to hurt rather than help.
- Investigate what separates high-converting cold segments from low-converting ones (job type, education, timing) to refine targeting further.

## Tools Used
- Python, Pandas, NumPy
- Matplotlib, Seaborn (visualization)
- Scikit-learn (K-Means clustering, PCA, StandardScaler)
- SciPy (chi-square tests)

## Notes / Limitations
- The `duration` feature (length of the last call) was intentionally excluded, as it is only known after a call outcome is determined and would leak information about the target.
- This is an exploratory and segmentation analysis, not a predictive model — a natural next step would be building a classifier and comparing its performance against segment-based targeting.

## Files
- `bank_marketing_eda.ipynb` — full notebook with EDA, statistical tests, and clustering
