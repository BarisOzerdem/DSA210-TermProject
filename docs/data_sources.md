# Data Sources

## Current Project Scope

The project initially considered multiple conflicts. In the current implementation, the analysis focuses on two conflict cases:

- Syrian Civil War
- Russia–Ukraine War

The goal is to compare neighboring host countries with non-neighbor major host countries across these two conflicts.

The main time window is 2010–2024.

## Processed Datasets

The project currently produces two processed datasets:

- `data/processed/syria_panel_2010_2024.csv`
- `data/processed/conflict_host_panel_2010_2024.csv`

The first dataset is the earlier Syria-only panel. The second dataset is the updated multi-conflict panel used for the May 5 machine learning milestone.

## 1. Conflict Data

Source: UCDP Battle-Related Deaths Dataset, conflict-year format

Direct link:
- https://ucdp.uu.se/downloads/brd/ucdp-brd-conf-251-csv.zip

Main raw variable used:
- `bd_best`

Constructed variable:
- `conflict_intensity`

The conflict intensity variable is used as a supporting indicator. In the multi-conflict ML notebook, `post_conflict` is used as the main conflict-period variable because it is more consistent across the Syria and Ukraine cases.

Post-conflict definitions:

- Syrian Civil War: `post_conflict = 1` for years from 2011 onward
- Russia–Ukraine War: `post_conflict = 1` for years from 2022 onward

## 2. Refugee Exposure Data

Source: UNHCR Refugee Statistics API, population endpoint

Base endpoint:
- https://api.unhcr.org/population/v1/population/

Main parameters used:

- `yearFrom=2010`
- `yearTo=2024`
- `cf_type=ISO`
- `download=true`

For the Syria case:

- origin country: Syria (`SYR`)
- host countries: Turkey, Lebanon, Jordan, Iraq, Egypt, Germany, Sweden, Austria, Netherlands

For the Ukraine case:

- origin country: Ukraine (`UKR`)
- host countries: Poland, Romania, Moldova, Hungary, Slovakia, Germany, Austria, Netherlands, Sweden, Czechia, Italy, Spain, France

Main raw variables used:

- `Refugees under UNHCR's mandate`
- `Asylum-seekers`

Constructed variables:

- `refugee_stock`
- `asylum_seekers`
- `refugees_per_1000`
- `log_refugee_stock`

## 3. Macroeconomic Indicators

Source: World Bank World Development Indicators API, version 2

Base endpoint:
- https://api.worldbank.org/v2

Indicators used:

- GDP growth: `NY.GDP.MKTP.KD.ZG`
- Inflation: `FP.CPI.TOTL.ZG`
- Unemployment: `SL.UEM.TOTL.ZS`
- Trade (% of GDP): `NE.TRD.GNFS.ZS`
- Current account balance (% of GDP): `BN.CAB.XOKA.GD.ZS`
- Population: `SP.POP.TOTL`

The World Bank indicators are collected for all host countries in the Syria and Ukraine cases for the years 2010–2024.

## Host Country Groups

Each host country is assigned to a host group.

For the Syria case:

- `neighboring_host`: Turkey, Lebanon, Jordan, Iraq
- `regional_non_neighbor_host`: Egypt
- `non_neighbor_european_host`: Germany, Sweden, Austria, Netherlands

For the Ukraine case:

- `neighboring_host`: Poland, Romania, Moldova, Hungary, Slovakia
- `non_neighbor_european_host`: Germany, Austria, Netherlands, Sweden, Czechia, Italy, Spain, France

These groups are used to compare whether economic changes are stronger in neighboring host countries than in non-neighbor major host countries.

## Merging Logic

The final panel uses these join keys:

- conflict data: `conflict_case + origin_iso + year`
- refugee data: `conflict_case + origin_iso + host_iso + year`
- macroeconomic data: `host_iso + year`

The final multi-conflict panel has the following main columns:

- `conflict_case`
- `origin_name`
- `origin_iso`
- `host_name`
- `host_iso`
- `host_group`
- `year`
- `post_conflict`
- `conflict_intensity`
- `refugee_stock`
- `asylum_seekers`
- `host_population`
- `refugees_per_1000`
- `log_refugee_stock`
- `gdp_growth`
- `inflation`
- `unemployment`
- `trade_pct_gdp`
- `current_account_pct_gdp`

## Final Output

The main dataset used for the updated machine learning analysis is:

- `data/processed/conflict_host_panel_2010_2024.csv`

This dataset contains 330 host-country-year observations before ML cleaning. After dropping rows with missing values in selected ML variables, 329 observations are used in the May 5 ML analysis.
