# DSA210 Term Project
## Economic Spillover Effects of Wars on Neighboring and Non-Neighbor Host Countries

This project examines whether wars create measurable economic spillover effects on neighboring and major host countries. The main focus is on refugee inflows and changes in macroeconomic indicators such as GDP growth, inflation, unemployment, trade, and current account balance.

## Project Proposal
[Project Proposal PDF](proposal.pdf)

## Current Scope

The initial project proposal considered multiple conflicts. During the data collection and modeling stage, I narrowed the current implementation to two conflict cases:

- Syrian Civil War
- Russia–Ukraine War

I made this decision to keep the dataset structure more consistent and to make the analysis easier to compare across conflicts. The current version compares neighboring host countries with non-neighbor major host countries. A third conflict can be added later as future work if comparable refugee, conflict, and macroeconomic data can be collected in the same format.

## Data Sources

The project combines data from three main sources:

- UCDP Battle-Related Deaths Dataset for conflict intensity
- UNHCR Refugee Data Finder / UNHCR Population API for refugee and asylum-seeker data
- World Bank World Development Indicators for macroeconomic indicators

## Dataset

The main processed dataset is:

`data/processed/conflict_host_panel_2010_2024.csv`

The dataset covers the years 2010–2024 and includes 330 host-country-year observations before cleaning. After removing rows with missing values in the selected machine learning variables, 329 observations were used in the ML analysis.

The main variables include:

- GDP growth
- inflation
- unemployment
- trade as percentage of GDP
- current account balance
- refugee stock
- refugees per 1,000 people
- post-conflict status
- host country group
- conflict case

The project also keeps the earlier Syria-only processed dataset:

`data/processed/syria_panel_2010_2024.csv`

## Analysis Progress

The project first created a Syria host-country panel and used it for exploratory data analysis and hypothesis testing. Later, I expanded the dataset by adding the Russia–Ukraine War and created a combined two-conflict panel.

The analysis includes:

- data collection and cleaning
- exploratory visualizations
- summary statistics
- hypothesis testing
- machine learning regression models

## May 5 Milestone: Machine Learning Analysis

For the May 5 milestone, I applied machine learning methods to the combined Syria–Ukraine conflict-host panel dataset. The machine learning task is a regression problem where the target variable is GDP growth.

The models used are:

- Linear Regression
- Decision Tree Regressor

The input features include refugee exposure, post-conflict status, host-country group, conflict case, and macroeconomic indicators.

Model performance:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 2.02 | 3.13 | 0.203 |
| Decision Tree Regressor | 2.17 | 3.19 | 0.174 |

Linear Regression performed slightly better than the Decision Tree Regressor. The results are exploratory and should not be interpreted as causal evidence.

## Repository Structure

```text
data/
  raw/
  processed/
    syria_panel_2010_2024.csv
    conflict_host_panel_2010_2024.csv

docs/
  ai_usage.md
  data_sources.md

notebooks/
  01_data_collection.ipynb
  02_eda_hypothesis_tests.ipynb
  03_ml_analysis.ipynb
  04_multi_conflict_data_collection.ipynb
  05_multi_conflict_ml_analysis.ipynb

outputs/
  figures/
  tables/
```

## Limitations

The results should be interpreted carefully because macroeconomic outcomes are affected by many factors outside the dataset. The project currently includes two conflict cases, so the findings are still exploratory. Future work can add another conflict case if comparable data can be collected with the same structure.

## Author

Baris Ozerdem  
DSA 210 – Introduction to Data Science  
Spring 2025–2026
