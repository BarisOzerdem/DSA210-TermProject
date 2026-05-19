# Final Checkpoint Report

## Project title

**Economic Spillover Effects of Wars on Neighboring and Non-Neighbor Host Countries**

## Research question

Do wars create measurable economic spillover effects on neighboring and major host countries, especially through refugee exposure and changes in macroeconomic indicators?

## Scope

The current version focuses on two conflict cases to keep the project scope manageable:

1. Syrian Civil War
2. Russia–Ukraine War

The unit of observation is a **host-country-year**. The final combined dataset covers **2010–2024** and contains **330 observations** before model cleaning. After dropping rows with missing values in the selected machine learning variables, **329 observations** are used for the GDP growth prediction task.

## Data sources

The project combines three types of data:

- **Conflict data:** UCDP Battle-Related Deaths Dataset
- **Refugee data:** UNHCR Refugee Statistics / Population API
- **Macroeconomic data:** World Bank World Development Indicators

The main processed dataset is:

```text
data/processed/conflict_host_panel_2010_2024.csv
```

## Main variables

The final dataset includes:

- conflict case
- origin country
- host country
- host group
- year
- post-conflict indicator
- conflict intensity
- refugee stock
- asylum seekers
- refugees per 1,000 host-country population
- log refugee stock
- GDP growth
- inflation
- unemployment
- trade as percentage of GDP
- current account balance as percentage of GDP

## Descriptive findings

The clearest descriptive pattern is that neighboring host countries receive much higher refugee exposure after conflict onset.

Examples from the final descriptive table:

| Conflict case | Host group | Period | Mean refugees per 1,000 | Mean GDP growth | Mean inflation |
|---|---|---:|---:|---:|---:|
| Russia–Ukraine War | neighboring_host | pre-conflict | 0.005 | 3.150 | 3.043 |
| Russia–Ukraine War | neighboring_host | post-conflict | 21.666 | 1.406 | 11.200 |
| Russia–Ukraine War | non_neighbor_european_host | pre-conflict | 0.027 | 1.314 | 1.449 |
| Russia–Ukraine War | non_neighbor_european_host | post-conflict | 9.709 | 1.664 | 5.880 |
| Syrian Civil War | neighboring_host | pre-conflict | 0.012 | 6.309 | 5.068 |
| Syrian Civil War | neighboring_host | post-conflict | 56.276 | 2.454 | 19.030 |
| Syrian Civil War | non_neighbor_european_host | pre-conflict | 0.096 | 3.253 | 1.338 |
| Syrian Civil War | non_neighbor_european_host | post-conflict | 4.486 | 1.403 | 2.487 |

This supports the basic project mechanism: wars do not only affect origin countries; they also create measurable exposure for host countries, especially neighboring hosts.

## Hypothesis test summary

The project uses exploratory statistical tests:

- Spearman correlation between refugee exposure and macroeconomic outcomes
- Mann–Whitney U tests comparing neighboring hosts with other host groups during post-conflict periods

Important results:

| Scope | Test | Outcome | Statistic | p-value | Interpretation |
|---|---|---:|---:|---:|---|
| All cases | Spearman correlation | inflation | 0.277 | 0.00000032 | Higher refugee exposure is associated with higher inflation in the combined dataset. |
| All cases | Mann–Whitney U | refugees_per_1000 | 5582.000 | 0.00000000000015 | Neighboring hosts have significantly higher refugee exposure after conflict onset. |
| All cases | Mann–Whitney U | inflation | 4095.000 | 0.0127 | Neighboring hosts and other host groups differ in post-conflict inflation. |
| Syria | Spearman correlation | GDP growth | -0.177 | 0.0408 | Higher refugee exposure is weakly associated with lower GDP growth in the Syria-only panel. |

These results are not causal. They show association and group differences only.

## Machine learning summary

The machine learning task predicts **GDP growth**.

Models used:

1. Linear Regression
2. Decision Tree Regressor

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 2.018 | 3.130 | 0.203 |
| Decision Tree Regressor | 2.165 | 3.186 | 0.174 |

Linear Regression performs slightly better than the Decision Tree Regressor. The model captures some signal, but the predictive power is limited. This is acceptable because the project is exploratory and not designed as a high-accuracy economic forecasting system.

## Main conclusion

The project finds evidence of measurable wartime spillover patterns. The strongest finding is that neighboring host countries experience much higher refugee exposure after conflict onset. Inflation differences are also visible, especially in post-conflict periods. GDP growth patterns are weaker and more difficult to interpret because many other macroeconomic forces affect growth.

The safest final claim is:

> The project finds evidence of measurable economic spillover patterns around major conflicts, especially through refugee exposure and inflation differences, but the results should be interpreted as exploratory associations rather than causal effects.

## Limitations

The main limitations are:

- The project cannot prove causality.
- The dataset includes only two conflict cases.
- Macroeconomic outcomes are affected by many other shocks.
- Country-year data hides local and regional variation.
- Refugee data may reflect registration capacity and reporting rules.
- Syria and Ukraine are useful but imperfect comparison cases because their conflicts differ in timing, geography, international response, and regional economic context.

## Ethics note

The project uses public, country-year level data. It does not use individual-level refugee records, personal identifiers, or private information.

The ethical framing is important. Refugees should not be presented as the cause of economic problems. The correct framing is that refugee exposure is one possible channel through which wars create regional spillover effects. Displaced people are themselves victims of conflict, and the project should avoid language that blames them for macroeconomic outcomes.

## Files added for the final checkpoint

Main notebook:

```text
notebooks/06_final_report.ipynb
```

Main report:

```text
docs/final_report.md
```

New tables:

```text
outputs/tables/final_descriptive_summary.csv
outputs/tables/final_prepost_changes.csv
outputs/tables/final_hypothesis_tests.csv
outputs/tables/final_ml_results.csv
outputs/tables/final_tree_feature_importance.csv
outputs/tables/final_missing_summary.csv
```

New figures:

```text
outputs/figures/final_refugee_exposure_by_group.png
outputs/figures/final_gdp_growth_by_group.png
outputs/figures/final_inflation_by_group.png
outputs/figures/final_actual_vs_predicted_gdp_growth.png
outputs/figures/final_tree_feature_importance.png
```
