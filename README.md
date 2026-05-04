# DSA210 Term Project
## Economic Spillover Effects of Wars on Neighboring Countries

This project examines whether recent wars create measurable economic spillover effects on neighboring or nearby host countries through refugee inflows and related macroeconomic changes.

## Project Proposal
[Project Proposal PDF](proposal.pdf)

## Current Scope

The initial project idea included more than one conflict. However, the current version of the project focuses on the Syrian Civil War as a case study. I made this decision to keep the dataset consistent and to make the exploratory analysis, hypothesis testing, and machine learning part clearer. Other conflicts, such as the Russia–Ukraine War, can be added later as future work.

## Data Sources
- UCDP Battle-Related Deaths Dataset
- UNHCR Refugee Data Finder
- World Bank World Development Indicators

## Preliminary Findings

The preliminary results suggest that higher refugee burden is associated with lower GDP growth in the Syria host-country panel. Both correlation-based and group-difference tests support this pattern.

For inflation, the evidence is weaker and less consistent. The correlation test does not show a statistically significant monotonic relationship, although the group-difference test indicates that inflation differs between low- and high-refugee-burden observations.

These findings should be interpreted as preliminary associations, not causal effects. At this stage, the project provides a reproducible dataset, visual analysis, and initial hypothesis tests for the April 14 milestone.

## May 5 Milestone: Machine Learning Analysis

For the May 5 milestone, I applied machine learning methods to the Syria host-country panel dataset. The main task is a regression problem where the target variable is GDP growth.

The models used in this milestone are:

- Linear Regression
- Decision Tree Regressor

The input features include refugee exposure, conflict intensity, unemployment, inflation, trade as a percentage of GDP, current account balance, year, and host country.

The models were evaluated using MAE, RMSE, and R². Since the dataset contains 45 host-year observations, the ML results are interpreted as exploratory rather than strong causal evidence.

## Author
Baris Ozerdem  
DSA 210 – Introduction to Data Science  
Spring 2025–2026
