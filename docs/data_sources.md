# Data Sources

## Current April 14 Scope

This milestone focuses on the Syrian Civil War panel.

- Origin country: Syria (`SYR`)
- Host countries: Turkey (`TUR`), Lebanon (`LBN`), Jordan (`JOR`)
- Time window: 2010–2024
- Expected sample size: 45 host-year observations

## 1. Conflict Intensity

Source: UCDP Battle-Related Deaths Dataset (conflict-year format)

Direct link:
- https://ucdp.uu.se/downloads/brd/ucdp-brd-conf-251-csv.zip

Main variable:
- `bd_best`

Constructed variable in the project:
- `conflict_bd_best_syria`

## 2. Refugee Exposure

Source: UNHCR Refugee Statistics API, population endpoint

Base endpoint:
- https://api.unhcr.org/population/v1/population/

Main parameters used:
- `yearFrom=2010`
- `yearTo=2024`
- `coo=SYR`
- `coa=TUR,LBN,JOR`
- `cf_type=ISO`
- `download=true`

Main raw variables used:
- `Refugees under UNHCR's mandate`
- `Asylum-seekers`

Constructed variables:
- `refugee_stock`
- `asylum_seekers`
- `refugees_per_1000`
- `log_refugee_stock`

## 3. Macroeconomic Indicators

Source: World Bank World Development Indicators API (v2)

Base endpoint:
- https://api.worldbank.org/v2

Indicators used:
- GDP growth: `NY.GDP.MKTP.KD.ZG`
- Inflation: `FP.CPI.TOTL.ZG`
- Unemployment: `SL.UEM.TOTL.ZS`
- Trade (% of GDP): `NE.TRD.GNFS.ZS`
- Current account balance (% of GDP): `BN.CAB.XOKA.GD.ZS`
- Population: `SP.POP.TOTL`

Host countries:
- Turkey (`TUR`)
- Lebanon (`LBN`)
- Jordan (`JOR`)

Years:
- 2010–2024

## Merging Logic

The final processed panel uses these join keys:

- conflict data: `origin_iso + year`
- refugee data: `origin_iso + host_iso + year`
- macro data: `host_iso + year`

## Final Output

Processed dataset:
- `data/processed/syria_panel_2010_2024.csv`
