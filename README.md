# Monetization Strategy Analysis: Association Mining on Mobile Game In-App Purchases
**CSC172 Data Mining and Analysis Final Project** *Mindanao State University - Iligan Institute of Technology* **Student:** Louise Antondy Garbanzos, 2020-1489
**Semester:** AY 2025-2026 Sem 1

## Abstract
This project implements the Apriori algorithm for association rule mining on a **Mobile Game In-App Purchases** dataset containing over 3,000 user transaction records. The goal is to identify strong "purchase clusters" to aid in monetization strategy and store optimization. The analysis pipeline includes data preprocessing (converting transaction logs to one-hot encoded user baskets), exploratory data analysis (EDA), rule generation, and evaluation using **Support, Confidence, Lift, Conviction, and Leverage**. Business insights and actionable bundling strategies are derived from the strongest associations found in the data.

## Table of Contents
- [Abstract](#abstract)
- [1. Introduction](#1-introduction)
  - [1.1 Problem Statement](#11-problem-statement)
  - [1.2 Objectives](#12-objectives)
  - [1.3 Scope and Limitations](#13-scope-and-limitations)
- [2. Dataset Description](#2-dataset-description)
  - [2.1 Source and Acquisition](#21-source-and-acquisition)
  - [2.2 Data Structure](#22-data-structure)
  - [2.3 Sample Transactions](#23-sample-transactions)
- [3. Methodology](#3-methodology)
  - [3.1 Data Preprocessing](#31-data-preprocessing)
  - [3.2 Exploratory Data Analysis](#32-exploratory-data-analysis)
  - [3.3 Apriori Algorithm Implementation](#33-apriori-algorithm-implementation)
  - [3.4 Evaluation Metrics](#34-evaluation-metrics)
- [4. Results](#4-results)
  - [4.1 Top Association Rules](#41-top-association-rules)
  - [4.2 Key Visualizations](#42-key-visualizations)
  - [4.3 Performance Metrics](#43-performance-metrics)
- [5. Discussion](#5-discussion)
  - [5.1 Business Insights](#51-business-insights)
  - [5.2 Actionable Recommendations](#52-actionable-recommendations)
  - [5.3 Limitations](#53-limitations)
- [6. Conclusion](#6-conclusion)
- [7. Video Presentation](#7-video-presentation)
- [References](#references)
- [Appendix: Full Results](#appendix-full-results)

## 1. Introduction
### 1.1 Problem Statement
In the "Freemium" mobile gaming market, revenue depends entirely on optimizing the purchasing behavior of a small percentage of users. However, creating random bundles or store layouts without data support can lead to missed revenue opportunities. This project applies data mining to player transaction logs to statistically uncover "purchase clusters" and generate rules that predict future purchases based on initial spending habits.

### 1.2 Objectives
- Preprocess the transactional dataset to standardize item names and handle missing values.
- Implement the Apriori algorithm with parameter tuning for sparse transaction data.
- Generate and evaluate monetization association rules.
- Visualize purchase frequency heatmaps and derive actionable business strategies.

### 1.3 Scope and Limitations
**Scope:** Analysis of item co-occurrence patterns within a single mobile application ecosystem using the Apriori algorithm.  
**Limitations:** The dataset represents a static snapshot of sales history. The analysis identifies correlation (co-purchase), not necessarily causation (e.g., buying X *caused* the need for Y).

## 2. Dataset Description
### 2.1 Source and Acquisition
**Source:** [Mobile Game In-App Purchases (Kaggle)](https://www.kaggle.com/datasets/pratyushpuri/mobile-game-in-app-purchases-dataset-2025)  
**Size:** ~3,000+ to 100,000+ Transactions (User Purchase History)  
**Format:** Transaction Logs (Long Format)

### 2.2 Data Structure
**Raw format (Long):**
Rows represent individual purchases; columns represent User ID, Item Name, and Price.

**Transaction format (Processed):**
A boolean matrix where rows are unique Users and columns are available Shop Items (True/False).

### 2.3 Sample Transactions
* **User 1001:** `['Starter_Pack', 'Gem_Pack_Small']`
* **User 1002:** `['Skin_Blue_Dragon', 'Battle_Pass_S1']`
* **User 1003:** `['No_Ads', 'Gem_Pack_Large', 'Speed_Boost_7d']`

## 3. Methodology

### 3.1 Data Preprocessing
1.  **Cleaning:** Handle missing values and filter out non-revenue actions (if applicable).
2.  **Transformation:** Grouping individual transaction rows by `User_ID` to create a "basket" of items.
3.  **Encoding:** Converting item lists into a One-Hot Encoded matrix using `mlxtend.preprocessing.TransactionEncoder`.
4.  **Sparsity Handling:** The resulting matrix is sparse as most users buy only 1-2 items out of the full catalog.

### 3.2 Exploratory Data Analysis
* **Frequency Analysis:** Identifying the "Best Sellers" (highest support items).
* **Distribution:** Analyzing the average "Basket Size" (how many items the average payer buys).
* **Co-occurrence:** Generating heatmaps to visualize which items frequently appear together before running the algorithm.

### 3.3 Apriori Algorithm Implementation
**Implementation:** `mlxtend.frequent_patterns.apriori()` to find frequent itemsets followed by `association_rules()` to generate metrics.
**Parameters:** Initial tuning targets `min_support=0.02`, `min_confidence=0.4` (subject to adjustment during testing).

### 3.4 Evaluation Metrics
- **Support:** Percentage of users who bought the item set.
- **Confidence:** Probability of buying Item B if Item A is already in the cart.
- **Lift:** Strength of the association (Is the purchase pattern coincidental?).
- **Conviction:** The dependency of the consequent on the antecedent.
- **Leverage:** Difference between observed and expected co-occurrence.

## 4. Results
*[Note: Data analysis is currently in progress. Actual results will be populated after running the notebook.]*

### 4.1 Top Association Rules
| Rank | Antecedents | Consequents | Support | Confidence | Lift | Conviction | Leverage |
|------|-------------|-------------|---------|------------|------|------------|----------|
| 1 | - | - | - | - | - | - | - |
| 2 | - | - | - | - | - | - | - |
| 3 | - | - | - | - | - | - | - |

### 4.2 Key Visualizations
*[Placeholder for Heatmaps and Bar Charts generated by Matplotlib/Seaborn]*

### 4.3 Performance Metrics
**Runtime:** [ - ] seconds  
**Scalability:** [To be evaluated based on execution time vs dataset size]

## 5. Discussion
*[Note: Detailed insights will be added pending the results of Section 4.]*

### 5.1 Business Insights
1.  **Insight 1:** [Pending Analysis - e.g., Identifying the "Gateway Item" that leads to high spending]
2.  **Insight 2:** [Pending Analysis - e.g., Correlation between cosmetic skins and gameplay boosters]

### 5.2 Actionable Recommendations
1.  **Bundle Strategy:** [e.g., Create a "Weekend Bundle" containing Item A and Item B based on high lift scores.]
2.  **UI Layout:** [e.g., Place Item B immediately next to Item A in the shop interface.]

### 5.3 Limitations
- Analysis does not currently account for the time delay between purchases (e.g., buying Item A today vs next month).
- Does not account for seasonal events or temporary sales.

## 6. Conclusion
The Apriori algorithm is expected to identify key purchasing behaviors within the mobile game ecosystem. By filtering for high **Lift**, I aim to distinguish between generic popular items (like basic currency) and specific strategic purchase combinations (like specific character builds).

## 7. Video Presentation
*[Link to YouTube/Drive Demo Video will be inserted here]*

## References
1. mlxtend Documentation: https://rasbt.github.io/mlxtend/
2. Mobile Game In-App Purchases Dataset: https://www.kaggle.com/datasets/pratyushpuri/mobile-game-in-app-purchases-dataset-2025
3. [Additional Reference to be added]

## Appendix: Full Results
*[Link to full CSV output or additional tables]*
