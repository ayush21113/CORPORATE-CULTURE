# Risk Analysis

This directory contains notebooks for analyzing **Risk Factors** (Item 1A) extracted from SEC 10-K filings.

## Overview

The goal of these notebooks is to quantify and visualize the evolution of various risk types over time using **TF-IDF (Term Frequency-Inverse Document Frequency)**. The analysis is based on predefined dictionaries of keywords associated with specific risk categories.

## Notebooks

### 1. `5_Risk_factors.ipynb`
- **Objective**: Analyzes risk across **5 broad categories**.
- **Risk Categories**:
  - `Financial`
  - `Legal & Regulatory`
  - `Tax`
  - `Other-Idiosyncratic` (Company-specific risks)
  - `Other-Systematic` (Market-wide risks)
- **Methodology**:
  - Preprocesses text (lowercasing, punctuation removal, stopword removal).
  - Calculates TF-IDF scores for the document.
  - Sums the TF-IDF scores of keywords belonging to each of the 5 categories.
  - Plots the trend of these 5 risk types over years.

### 2. `30_Risk_factors.ipynb`
- **Objective**: Performs a granular analysis using **30 specific risk categories**.
- **Risk Categories** (Partial List):
  - `Catastrophe`, `Corporate_Governance`, `Country`, `Customer_Concentration`
  - `Economic_Conditions`, `Energy_Sector`, `Financing` (I, II, III)
  - `Healthcare_Spending`, `Human_Capital`, `Information_Systems`
  - `Intellectual_Property`, `Product_Defects`, `Supply_Chain`, `Tax_Uncertainty`
  - ...and more.
- **Methodology**:
  - Similar to the 5-factor notebook but provides a much more detailed breakdown of risk exposure.
  - Outputs a CSV file (`30_risk_factors_s&p_500.csv`) containing the computed risk scores for each company and year.

##  How to Run
1.  Ensure you have the parsed Item 1A data (CSV files with `Extracted 1A` and `Ticker` columns).
2.  Update the `dataset_path` variable in the `__main__` block to point to your data directory.
3.  Run the cells to generate the TF-IDF scores and visualization plots.

##  Dependencies
- `pandas`
- `numpy`
- `nltk` (for stopwords)
- `scikit-learn` (for TfidfVectorizer)
- `matplotlib` (for plotting)
