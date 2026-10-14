# HIT140 – Objective 2.1: Linear Regression

## Unit Information

**Unit:** HIT140 – Foundations of Data Science  
**Assessment:** Group Project Report – Objective 2  
**Section:** Linear Regression 2.1

**Group:** Darwin Group 29

**Group Members:**
- Adarsh Thakorbhai Padhya – S401743
- Md Osman Syed – S400545
- Madan B K – S399582
- Aakriti B C – S400552

## Overview

This folder contains the analysis completed for Objective 2.1 of the HIT140 Foundations of Data Science group project.

The purpose of this analysis is to use multiple linear regression to predict the **goal difference** between opposing teams in the 2026 FIFA World Cup using eight explanatory variables available before each match.

The dataset contains **104 matches**, with one row representing one match.

The analysis includes data cleaning, feature engineering, descriptive statistics, model development, prediction evaluation and regression diagnostics.

## Research Question

**How well can eight pre-match predictors explain and predict the goal difference between opposing teams in the 2026 FIFA World Cup?**

## Target Variable

The target variable is:

**Goal Difference = Home Team Goals − Away Team Goals**

- Positive values indicate that Team 1 scored more goals.
- Negative values indicate that Team 2 scored more goals.
- Zero indicates a draw.

For matches decided by penalty shoot-outs, goals scored during the shoot-out are excluded.

The Home and Away labels represent the order in which teams appear in the dataset, not necessarily the match venue.

## Explanatory Variables

Exactly eight explanatory variables are used:

1. **Past_Avg_Scored_Diff** – Difference in average goals scored in previous tournament matches.
2. **Past_Avg_Conceded_Diff** – Difference in average goals conceded in previous tournament matches.
3. **Past_Win_Rate_Diff** – Difference in previous tournament win rates.
4. **Rank_Points_Diff** – Difference in FIFA ranking points between the two teams.
5. **Past_Clean_Sheet_Rate_Diff** – Difference in previous clean-sheet rates.
6. **Last_Match_GD_Diff** – Difference in goal difference from each team's previous match.
7. **Host_Diff** – Difference in host-nation status between the teams.
8. **Knockout** – Indicates whether the match belongs to the group stage (0) or knockout stage (1).

Historical performance variables were calculated using results available before each match to avoid using future match information.

## Data Preparation

Data cleaning and preparation were completed using Python.

The main steps included:

- Loading the raw fixtures and prepared comparison datasets.
- Removing section headings and repeated header rows.
- Extracting match dates, teams and scores.
- Standardising team names.
- Removing penalty shoot-out markers from scores.
- Calculating goal difference.
- Adding the missing third-place match from the prepared dataset.
- Calculating historical performance variables chronologically.
- Incorporating FIFA ranking point differences.
- Creating host-nation and knockout-stage indicators.
- Checking missing values and data consistency.
- Comparing the rebuilt dataset against the prepared dataset.

The final dataset contains **104 matches and eight explanatory variables**, with no missing predictor values.

For the first 24 matches, historical performance differences were set to zero because neither team had played a previous match in the tournament. These zeros represent unavailable relative historical information rather than observed performance.

## Model Development

The main model uses **Ordinary Least Squares (OLS) Multiple Linear Regression**.

A chronological train-test split was applied:

- **Training set:** First 83 matches
- **Testing set:** Final 21 matches

The model was trained on earlier matches and evaluated using later matches.

The training set includes group-stage and early knockout matches, while the testing set contains only knockout-stage matches.

Two additional comparisons were included:

- **Baseline model:** Predicts the average goal difference from the training dataset.
- **Ranking-only model:** Uses only FIFA ranking point differences to predict goal difference.

These comparisons help evaluate whether the eight-predictor regression improves prediction accuracy.

## Model Evaluation

The models were evaluated using:

- **MAE (Mean Absolute Error):** Measures the average absolute prediction error.
- **RMSE (Root Mean Squared Error):** Measures prediction errors while giving greater weight to larger errors.
- **R² (R-squared):** Measures how much variation in goal difference is explained by the model.

### Test Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Eight-Predictor Linear Regression | 1.214 | 1.530 | 0.002 |
| Baseline Model | 1.426 | 1.747 | -0.302 |
| Ranking-Only Regression | 1.173 | 1.466 | 0.084 |

The eight-predictor model produced lower prediction errors than the baseline model.

However, its test R² was approximately 0.002, indicating very limited predictive performance on unseen matches.

The ranking-only model performed slightly better than the eight-predictor model on the same test set.

## Statistical Analysis

The OLS regression summary was examined to understand the relationships between the predictors and goal difference.

The main training results were:

- **Training R²:** 0.495
- **Adjusted R²:** 0.441
- **Overall F-test p-value:** Approximately 1.33 × 10⁻⁸

FIFA ranking point difference was the only individual predictor statistically significant at the 5% level.

The other predictors did not show statistically significant individual associations after accounting for the remaining variables.

## Regression Diagnostics

Additional diagnostic checks were performed to assess the regression model.

These included:

- **Variance Inflation Factor (VIF):** Checked multicollinearity among predictors.
- **Residual Plot:** Examined prediction errors and possible patterns.
- **Normal Q-Q Plot:** Examined the distribution of residuals.
- **Jarque–Bera Test:** Assessed residual normality.
- **Breusch–Pagan Test:** Examined constant error variance.
- **Durbin–Watson Statistic:** Examined residual autocorrelation.

All predictor VIF values were below 5, suggesting no severe multicollinearity under this common guideline.

The Jarque–Bera test (p = 0.522) and Breusch–Pagan test (p = 0.195) did not provide sufficient evidence to reject residual normality or constant variance at the 5% significance level.

However, these tests do not prove that all regression assumptions are satisfied.

## Visualisations

The Jupyter Notebook includes visualisations for understanding the dataset and evaluating the model.

These include:

- Exploratory data visualisations.
- Actual versus predicted goal differences.
- Training residual plot.
- Normal Q-Q plot.

These visualisations help identify relationships, prediction errors and possible violations of regression assumptions.

## Conclusion

The eight-predictor linear regression model explained approximately **49.5% of the variation in training goal difference**.

However, performance was substantially weaker on the testing dataset, with an R² of 0.002.

The model performed better than the baseline in terms of MAE and RMSE, but the ranking-only model achieved slightly better results.

FIFA ranking point difference was the strongest statistically supported individual predictor in the main regression.

Overall, the findings suggest that predicting football goal differences using only pre-match information is difficult.

The analysis is limited by the small testing dataset, short tournament histories and differences between group-stage and knockout-stage matches.

## Files

- `World_Cup_2026_Match_Data.csv` – Raw FIFA World Cup 2026 fixtures and match results.
- `Regression_2_1_Dataset.csv` – Prepared comparison dataset containing ranking point differences and match-level variables.
- `Linear_Regression_2_1_ready.ipynb` – Jupyter Notebook containing data preparation, feature engineering, descriptive statistics, regression modelling, evaluation, visualisations and statistical diagnostics.

## Software and Libraries

The analysis was completed in Python using:

- Pandas
- NumPy
- Matplotlib
- SciPy
- Scikit-learn
- Statsmodels
- Jupyter Notebook

## Reproducibility

To reproduce the analysis:

1. Download the Jupyter Notebook and both CSV input files.
2. Keep all three files in the same folder.
3. Install the required Python libraries.
4. Open the notebook in Jupyter Notebook or Visual Studio Code.
5. Select an appropriate Python environment.
6. Run all notebook cells from top to bottom.

The notebook automatically checks whether the required input files are available and performs data cleaning, feature engineering, model training, evaluation and diagnostic analysis.

## References

- FBref. *2026 World Cup scores & fixtures*. https://fbref.com/en/comps/1/schedule/schedule-Stats
- The Stats Don't Lie. *World Cup 2026*. https://www.thestatsdontlie.com/football/world-cup-2026/
- FIFA. (2026). *FIFA/Coca-Cola Men's World Ranking*. https://inside.fifa.com/fifa-rankings/world-ranking/men
