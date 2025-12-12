# CSC172 Association Rule Mining Project Proposal
**Student:** Louise Antondy Garbanzos, 2020-1489
**Date:** 12/12/2025

## 1. Project Title
Monetization Strategy Analysis: Association Mining on Mobile Game In-App Purchases

## 2. Problem Statement
In the "Freemium" mobile gaming market, revenue depends entirely on a small percentage of users making microtransactions. A key challenge for developers is understanding purchasing behavior—specifically, which items are bought together or sequentially. This project analyzes player transaction logs to discover "purchase clusters" and strong association rules. This is relevant for optimizing store layouts and creating targeted bundle offers (e.g., "If a player buys X, offer Y at a discount") to maximize revenue and user retention.

## 3. Objectives
- Preprocess the raw transactional dataset to standardize item names and handle missing purchase values.
- Perform EDA with visualizations including top-selling item distributions and purchase frequency heatmaps.
- Implement the Apriori algorithm to generate monetization association rules.
- Evaluate rules using **Support, Confidence, Lift, Conviction, and Leverage** metrics to identify actionable business insights (e.g., spotting "Whale" behavior patterns).

## 4. Dataset Plan
- **Source:** [Mobile Game In-App Purchases - Kaggle](https://www.kaggle.com/datasets/pratyushpuri/mobile-game-in-app-purchases-dataset-2025)
- **Size:** ~3,000+ records (Exceeds the 500 minimum requirement).
- **Domain:** Mobile Gaming / E-commerce.
- **Scope:** The dataset represents transaction logs from a single mobile gaming application, ensuring valid associations between items within the same ecosystem.
- **Structure:** The dataset is in a transactional format where rows represent user actions/purchases and columns represent item details or amounts.
- **Sample Transactions:**

| User_ID | Item_Name | Item_Category | Price_USD | Days_Since_Install |
| :--- | :--- | :--- | :--- | :--- |
| U_1001 | Starter_Pack | Bundle | 0.99 | 1 |
| U_1001 | Gem_Pack_Small | Currency | 4.99 | 3 |
| U_1002 | Skin_Blue_Dragon | Cosmetic | 2.99 | 15 |
| U_1002 | Battle_Pass_S1 | Subscription | 9.99 | 15 |

## 5. Technical Approach
- **Preprocessing:**
  - **Cleaning:** Handle null values in item descriptions and filter out free/reward transactions (if strictly analyzing revenue).
  - **Transformation:** Group by `User_ID` to create a "basket" of items, then convert to One-Hot Encoded format using `mlxtend.preprocessing.TransactionEncoder`.
- **Algorithm:** Apriori (Initial tuning: `min_support=0.02`, `min_confidence=0.4`, `min_lift=1.1`).
- **Framework:** Python + pandas + mlxtend + matplotlib/seaborn.
- **Environment:** Jupyter Notebook / Google Colab.

## 6. Expected Challenges & Mitigations
- **Challenge:** Data Imbalance (Most players buy nothing or very few items, while "Whales" buy hundreds).
  - **Solution:** I may segment the data (e.g., run analysis specifically on "Paying Users Only") to avoid the dataset being dominated by non-spenders.

- **Challenge:** Redundant Rules (e.g., `{100 Gems} -> {500 Gems}` might just mean they like currency).
  - **Solution:** Filter results by **Lift > 1.2** and focus on cross-category rules (e.g., `{Skin} -> {Battle Pass}`) which offer more strategic value than same-category rules.

- **Challenge:** High Cardinality (Too many unique item names like "Skin_Red_1", "Skin_Red_2").
  - **Solution:** Generalize item names during preprocessing (e.g., map all specific skins to a generic "Cosmetic_Skin" category) if the matrix becomes too sparse.
