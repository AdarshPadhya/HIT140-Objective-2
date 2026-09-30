# HIT140 – Objective 2.1: Linear Regression

## Unit Information

**Unit:** HIT140 – Foundations of Data Science  
**Assessment:** Group Project Report – Objective 2  
**Section:** Linear Regression 2.1  

**Group Members:**

**Darwin Group 29**
- Adarsh Thakorbhai Padhya – S401743
- Md Osman Syed – S400545
- Madan B K – S399582
- Aakriti B C – S400552

## Overview

This folder contains the work completed for Objective 2.1 of the HIT140 Foundations of Data Science group project.

The purpose of this analysis is to use linear regression to predict the **goal difference** of matches from the 2026 FIFA World Cup using eight pre-match explanatory variables.

The dataset contains **104 matches**, with one row representing one match.

## Target Variable

The target variable is:

**Goal Difference = Home Team Goals − Away Team Goals**

A positive goal difference indicates that the home team scored more goals, while a negative value indicates that the away team scored more goals.

## Explanatory Variables

Exactly eight explanatory variables are used:

1. **Rank_Diff** – Difference in FIFA ranking between the home and away teams.
2. **Age_Diff** – Difference in average squad age.
3. **Goals_For_Avg_Diff** – Difference in average goals previously scored.
4. **Goals_Against_Avg_Diff** – Difference in average goals previously conceded.
5. **Win_Rate_Diff** – Difference in previous tournament win rates.
6. **Draw_Rate_Diff** – Difference in previous tournament draw rates.
7. **Clean_Sheet_Rate_Diff** – Difference in previous clean-sheet rates.
8. **Last_Match_GD_Diff** – Difference in goal difference from each team's previous match.

Tournament performance variables were calculated using information available before each match to prevent data leakage.

## Data Preparation

The original match dataset was cleaned and prepared in Python.

The main preparation steps included:

- Removing empty rows.
- Cleaning team names.
- Extracting home and away goals.
- Calculating the target variable.
- Creating the eight explanatory variables.
- Calculating tournament performance variables chronologically.
- Checking missing values and data consistency.

## Model Development

Three regression models were evaluated:

- Ordinary Least Squares (OLS) Linear Regression
- Ridge Regression
- Lasso Regression

A chronological train-test split was used.

- **Training set:** First 83 matches
- **Testing set:** Final 21 matches

This approach allows the models to be evaluated using later matches that were not used during training.

## Model Evaluation

The models were evaluated using:

- **MAE (Mean Absolute Error)** – average size of prediction errors.
- **RMSE (Root Mean Squared Error)** – prediction error with larger errors receiving greater weight.
- **R² (R-squared)** – proportion of variation in goal difference explained by the model.

The analysis showed that the selected pre-match variables had limited ability to predict goal difference on unseen matches. This highlights the difficulty of predicting football match results using only pre-match information.

## Files

- `dataset 2.1.xlsx` – Original match dataset.
- `regression_2_1_processed.csv` – Cleaned and feature-engineered dataset generated through Python.
- `regression_2_1.ipynb` – Python/Jupyter Notebook containing data preparation, analysis, modelling, evaluation and visualisations.

## References

- FBref, *2026 World Cup Scores & Fixtures*: https://fbref.com/en/comps/1/schedule/schedule-Stats
- MLS Soccer, *FIFA World Rankings: Every team at the 2026 World Cup* (rankings as of 11 June 2026): https://www.mlssoccer.com/competitions/fifa-world-cup/news/fifa-world-rankings-every-team-at-the-world-cup
- FIFA, *The squads in stats*: https://www.fifa.com/en/tournaments/mens/worldcup/canadamexicousa2026/articles/numbers-squads-stats
- Pantheonic, *The Tournament of Global Unity — FIFA World Cup 2026* (official-squad age table): https://www.pantheonic.cloud/publication/PI_WC2026_Full_Document.html

## Software and Libraries

The analysis was completed in Python using:

- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Statsmodels
- Jupyter Notebook

## Reproducibility

To run the analysis, install the required Python libraries and run the Jupyter Notebook from top to bottom.

The raw dataset should be located in the same project directory expected by the notebook.

