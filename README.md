# MSCS 634 – Lab 6: Association Rule Mining with Apriori and FP-Growth

## Overview
This lab explores association rule mining techniques using the Apriori and FP-Growth algorithms on a real-world transactional dataset. The goal of the lab is to identify frequent itemsets, generate association rules, and use visualizations to uncover meaningful purchasing patterns within retail data.

## Dataset
- **Name:** Online Retail Dataset (UCI Machine Learning Repository)
- **Description:** Contains transactional data for a UK-based online retailer, including invoice numbers, product descriptions, quantities, prices, customer IDs, and country information.
- **Preprocessing Steps:**
  - Removed missing invoice numbers and product descriptions.
  - Excluded credit or refund invoices and negative quantities.
  - Kept only positive priced items and filtered to the United Kingdom.
  - Aggregated data into a transaction–item matrix for market basket analysis.
  - Limited items to those appearing at least 50 times to reduce sparsity.

## Methods
- Frequent itemset mining using:
  - **Apriori** (`mlxtend.frequent_patterns.apriori`)
  - **FP-Growth** (`mlxtend.frequent_patterns.fpgrowth`)
- Association rule generation using:
  - `mlxtend.frequent_patterns.association_rules` with confidence and lift metrics.
- Visualizations created with Seaborn and Matplotlib:
  - Barplots of most frequent items.
  - Heatmap of item co-occurrence.
  - Barplots of the top frequent itemsets.
  - Scatter plot of confidence vs. lift for association rules.

## Key Insights
- Both Apriori and FP-Growth identified similar high-support itemsets involving commonly purchased home décor, gift items, and stationery sets.
- Association rules revealed strong co-purchase behavior among certain product groups. Rules with high lift values showed meaningful relationships that occur more often than random chance.
- Scatter plot analysis highlighted clear clusters of strong rules with high confidence and lift, providing useful insights for potential cross-selling or product bundling strategies.

## Comparative Analysis: Apriori vs FP-Growth
- FP-Growth ran faster than Apriori due to its tree-based structure, which avoids repeated full-dataset scans.
- Apriori required more computation time because it generates candidate itemsets level by level.
- Both algorithms produced similar top frequent itemsets and association rules when using the same support and confidence thresholds.
- FP-Growth generated more itemsets overall, especially at deeper levels, due to superior scalability.

## Challenges and Decisions
- Installation issues occurred with mlxtend and openpyxl packages, which were resolved by installing missing dependencies.
- The dataset size caused high memory usage, which was handled by filtering to frequent items and a single country.
- Initial support and confidence thresholds produced either too few or too many rules, so values were tuned to achieve a balanced output.
- Sparse matrix structure required careful filtering to ensure meaningful and computationally manageable patterns.


