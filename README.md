# DSA210 Term Project

## Economic Spillover Effects of Wars on Neighboring and Non-Neighbor Host Countries

This project examines whether wars create measurable economic spillover effects on neighboring and major host countries. The main focus is on refugee inflows and changes in macroeconomic indicators such as GDP growth, inflation, unemployment, trade, and current account balance.

## Project Proposal

[Project Proposal PDF](proposal.pdf)

## Current Scope

The project initially considered multiple conflict cases. During data collection and modeling, the implementation was narrowed to two conflict cases in order to keep the data structure consistent and comparable:

- Syrian Civil War
- Russia–Ukraine War

The current version compares neighboring host countries with non-neighbor major host countries. The unit of observation is a host-country-year.

## Research Question

Do wars create measurable economic spillover effects on neighboring and major host countries, especially through refugee exposure and changes in macroeconomic indicators?

## Data Sources

The project combines data from three main sources:

- UCDP Battle-Related Deaths Dataset for conflict intensity
- UNHCR Refugee Data Finder / UNHCR Population API for refugee and asylum-seeker data
- World Bank World Development Indicators for macroeconomic indicators

More details are available in:

```text
docs/data_sources.md
```

## Dataset

The main processed dataset is:

```text
data/processed/conflict_host_panel_2010_2024.csv
```

The dataset covers the years **2010–2024** and includes **330 host-country-year observations** before machine learning cleaning. After removing rows with missing values in the selected machine learning variables, **329 observations** are used in the GDP growth prediction task.

The project also keeps the earlier Syria-only processed dataset:

```text
data/processed/syria_panel_2010_2024.csv
```

## Methodology

The project builds a country-year panel dataset by combining conflict intensity, refugee exposure, and macroeconomic indicators. The analysis first compares pre-conflict and post-conflict periods for each host-country group. Then, exploratory statistical tests are used to examine whether refugee exposure is associated with macroeconomic outcomes. Finally, two regression models are trained to predict GDP growth using conflict, refugee, and macroeconomic variables.

The statistical analysis includes Spearman correlation tests and Mann–Whitney U tests. Spearman correlation is used because the relationships may not be linear. Mann–Whitney U tests are used to compare neighboring host countries with other host groups during post-conflict periods.

The machine learning part is treated as an exploratory regression task rather than a causal model.

## Main Variables

The final combined dataset includes:

- conflict case
- origin country
- host country
- host-country group
- year
- post-conflict indicator
- conflict intensity
- refugee stock
- asylum seekers
- host population
- refugees per 1,000 host-country population
- log refugee stock
- GDP growth
- inflation
- unemployment
- trade as percentage of GDP
- current account balance as percentage of GDP

## Analysis Progress

The project includes:

- data collection and cleaning
- exploratory data analysis
- summary statistics
- hypothesis testing
- machine learning regression models
- ethics and limitations discussion
- final checkpoint report

## May 5 Milestone: Machine Learning Analysis

For the May 5 milestone, I applied machine learning methods to the combined Syria–Ukraine conflict-host panel dataset. The machine learning task is a regression problem where the target variable is GDP growth.

The models used are:

- Linear Regression
- Decision Tree Regressor

Model performance:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 2.02 | 3.13 | 0.203 |
| Decision Tree Regressor | 2.17 | 3.19 | 0.174 |

Linear Regression performed slightly better than the Decision Tree Regressor. The results are exploratory and should not be interpreted as causal evidence.

## Final Checkpoint

For the final checkpoint, I consolidated the project into a final report-style notebook and added final tables, figures, interpretation, limitations, and ethics discussion.

Main final checkpoint files:

```text
notebooks/06_final_report.ipynb
docs/final_report.md
docs/submission_checklist.md
```

Main new output tables:

```text
outputs/tables/final_descriptive_summary.csv
outputs/tables/final_prepost_changes.csv
outputs/tables/final_hypothesis_tests.csv
outputs/tables/final_ml_results.csv
outputs/tables/final_tree_feature_importance.csv
outputs/tables/final_missing_summary.csv
```

Main new output figures:

```text
outputs/figures/final_refugee_exposure_by_group.png
outputs/figures/final_gdp_growth_by_group.png
outputs/figures/final_inflation_by_group.png
outputs/figures/final_actual_vs_predicted_gdp_growth.png
outputs/figures/final_tree_feature_importance.png
```

## Final Findings

The strongest finding is that neighboring host countries experience much higher refugee exposure after conflict onset. This is especially clear in the Syrian Civil War case and also visible in the Russia–Ukraine case.

Inflation tends to be higher in post-conflict periods, especially for neighboring host groups. GDP growth often declines after conflict onset, but the GDP relationship is weaker and harder to interpret because many other macroeconomic shocks affect growth.

The safest final conclusion is:

> The project finds evidence of measurable economic spillover patterns around major conflicts, especially through refugee exposure and inflation differences, but the results should be interpreted as exploratory associations rather than causal effects.

## Limitations

The results should be interpreted carefully because macroeconomic outcomes are affected by many factors outside the dataset. The project currently includes two conflict cases, so the findings are exploratory. The analysis does not prove causality.

Important limitations:

- conflict cases differ in timing, geography, and international response
- country-year data hides local and regional variation
- refugee data may reflect registration and reporting differences
- macroeconomic outcomes are affected by many external shocks
- using contemporaneous macroeconomic variables in the ML model makes the model explanatory rather than a clean forecasting model

## Ethics Note

This project uses public, country-year level data. It does not use individual-level refugee records, personal identifiers, or private information.

The project should not frame refugees as the cause of economic problems. Refugee exposure is treated as one possible channel of wartime spillover, while recognizing that displaced people are themselves affected by war.

More details are available in:

```text
docs/final_report.md
docs/ai_usage.md
```

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
  final_report.md
  submission_checklist.md

notebooks/
  01_data_collection.ipynb
  02_eda_hypothesis_tests.ipynb
  03_ml_analysis.ipynb
  04_multi_conflict_data_collection.ipynb
  05_multi_conflict_ml_analysis.ipynb
  06_final_report.ipynb

outputs/
  figures/
  tables/
```

## How to Run

Install the required packages:

```bash
pip install -r requirements.txt
```

Run the notebooks in this order:

```text
01_data_collection.ipynb
02_eda_hypothesis_tests.ipynb
03_ml_analysis.ipynb
04_multi_conflict_data_collection.ipynb
05_multi_conflict_ml_analysis.ipynb
06_final_report.ipynb
```

The main final checkpoint notebook is:

```text
notebooks/06_final_report.ipynb
```

## Author

Baris Ozerdem  
DSA 210 – Introduction to Data Science  
Spring 2025–2026
