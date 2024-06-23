# Association Rule Mining on Adult Income Dataset

## Overview

This repository contains Python scripts for performing association rule mining on the Adult Income dataset using the Apriori algorithm. The dataset is preprocessed, and association rules are generated based on various metrics such as confidence, lift, interest, and conviction.

## Steps

### Data Loading and Preprocessing

The dataset (`DATA.csv`) is loaded into a pandas DataFrame, where missing values marked as ' ?' are replaced with `pd.NA` and subsequently dropped. Column names are assigned, and categorical vs. continuous variables are identified.

### One-Hot Encoding

Categorical columns are encoded using `OneHotEncoder` from `sklearn.preprocessing`, resulting in binary columns. These are then combined with continuous columns into a new DataFrame (`preprocessed_data`).

### Association Rule Mining

The Apriori algorithm (`apriori` from `mlxtend.frequent_patterns`) is applied multiple times:
- Iterating over different support, confidence, and interest values.
- Generating frequent itemsets and association rules using `association_rules`.
- Rules are evaluated and ranked based on:
  - **Confidence**: Measure of the predictability of the consequent given the antecedent.
  - **Lift**: Measure of how much more often the antecedent and consequent occur together than expected by chance.
  - **Interest**: Measure of how much more or less likely the antecedent and consequent are to occur together compared to what would be expected if they were statistically independent.
  - **Conviction**: Measure indicating the degree of dependence between antecedent and consequent.

### Output

The top 10 association rules are printed for each combination of support, confidence, and interest values. Additionally, the columns of `encoded_categorical_cols` and `preprocessed_data` are printed for verification.

## Usage

Ensure Python environment is set up with necessary libraries (`pandas`, `sklearn`, `mlxtend`). Run the script to perform association rule mining on the Adult Income dataset.

## Improvements

- Consider caching frequent itemsets to optimize performance during parameter iteration.
- Visualize association rules to facilitate interpretation and insights.
- Expand parameter tuning to explore a wider range of support, confidence, and interest values.

