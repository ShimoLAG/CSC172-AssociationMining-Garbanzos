# Project Development Progress - Mobile Game In-App Purchase Analysis

## 1. Algorithm Selection & Methodology
- **Algorithm:** Apriori Algorithm (Custom Python Implementation)
- **Data Structure:** Transactional "Baskets" of User Attributes (One-Hot Encoded)
- **Metrics Used:** Support, Confidence, Lift, Leverage, Conviction
- **Justification:** Selected Apriori for its interpretability in identifying "If-Then" rules within categorical data. Used custom implementation to allow precise control over item pairing and metric calculation without heavy external dependencies like `mlxtend`, ensuring better integration with the specific demographic/behavioral dataset.

## 2. Initial Results (Mining & EDA)
- **Exploratory Analysis:**
    - Successfully binned continuous variables (`Age` to `Age_Group`, `AverageSessionLength` to `Session_Bin`) to create discrete categories.
    - **Visualizations:** Generated Item Frequency bars, Basket Size histograms, and Co-occurrence Heatmaps showing strong correlations between *Payment Methods* and *Demographics*.
- **Rule Generation:**
    - **Strong Associations:** Discovered high-confidence rules linking **Device Type** to **Spending Habits** (e.g., iOS users showing distinct payment preferences vs. Android).
    - **Lift Metrics:** Identified rules with **Lift > 1.0**, confirming that certain user attributes (like *Age Group*) are non-random predictors of *Game Genre* preference.
    - **Performance:** Successfully processed >3,000 transaction records with optimized filtering (min_support=0.03), yielding actionable rules without memory overflow.

## 3. Development Milestones
- [x] **Environment Setup:** Configured Jupyter Notebook environment with `pandas`, `numpy`, `matplotlib`, and `seaborn`.
- [x] **Data Preprocessing:** Implemented cleaning logic to handle missing values and feature engineering to convert numerical data (Age, Session Length) into categorical bins.
- [x] **EDA Implementation:** Built visualization modules for Item Frequency, Transaction Size, and Attribute Co-occurrence Heatmaps.
- [x] **Mining Engine:** Developed the core Apriori logic to generate frequent itemsets and derive Association Rules based on user-defined thresholds.
- [x] **Evaluation Module:** Created a visualization system (Scatter Plot) to map Support vs. Confidence, colored by Lift, for easy rule interpretation.

## 4. Current Challenges & Next Steps
- **Challenge:** The dataset aggregates purchase amounts rather than listing individual item IDs (e.g., "500 Gems"), which required shifting the analysis focus from "Market Basket" to "User Attribute Profiling."
    - *Mitigation:* Treated user traits (Device, Gender, Region) as the "items" in the basket to find profiling rules instead of bundling rules.
- **Next Step:** Translate the top 10 discovered rules (by highest Lift) into concrete business recommendations (e.g., specific ad targeting strategies for "Whales") for the final report.
