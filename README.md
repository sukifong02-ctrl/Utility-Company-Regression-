Week 10 Quiz: Seasonal Revenue Regression Analysis

Project Overview

This project analyzes whether the relationship between production and revenue changes across seasons. Two multiple linear regression models are created and compared:

Winter model – tests whether winter affects the intercept and slope of the revenue relationship.

Fall model – tests whether fall affects the intercept and slope of the revenue relationship.

The models are trained using the observations labelled dt4training and evaluated using the observations labelled dt4testing.

Research Question

Does seasonality improve the ability to predict revenue from production, and does the effect of production on revenue differ during winter or fall?

Dataset

The notebook uses the following file:

AICPA_regressionAnalysisData.csv

The dataset includes these main variables:

Variable

Description

date

Date of the observation

production

Level of production

revenue

Revenue earned

type

Identifies training and testing observations

The type column separates the data into:

dt4training – used to estimate the regression models

dt4testing – used to evaluate model predictions

Seasonal Variables

Winter Dummy Variable

The winter dummy variable equals 1 when the observation occurs in:

December

January

February

It equals 0 during all other months.

HS_data['winter_DV'] = np.where(
    HS_data['date'].dt.month.isin([12, 1, 2]), 1, 0
)

Fall Dummy Variable

The fall dummy variable equals 1 when the observation occurs in:

September

October

November

It equals 0 during all other months.

HS_data['fall_DV'] = np.where(
    HS_data['date'].dt.month.isin([9, 10, 11]), 1, 0
)

Interaction Terms

Interaction terms are included to test whether the effect of production on revenue changes during a particular season.

Winter Interaction = Production × Winter Dummy
Fall Interaction = Production × Fall Dummy

A significant interaction term would suggest that the slope relating production to revenue is different during that season.

Regression Models

Model 1: Winter Model

Revenue = β0 + β1(Production) + β2(Winter) + β3(Production × Winter) + ε

Interpretation:

β0 represents the estimated intercept outside winter.

β1 represents the effect of production on revenue outside winter.

β2 represents the change in the intercept during winter.

β3 represents the change in the production slope during winter.

Model 2: Fall Model

Revenue = β0 + β1(Production) + β2(Fall) + β3(Production × Fall) + ε

Interpretation:

β0 represents the estimated intercept outside fall.

β1 represents the effect of production on revenue outside fall.

β2 represents the change in the intercept during fall.

β3 represents the change in the production slope during fall.

Model Evaluation

The models are evaluated on the testing data using the following measures:

Mean Absolute Percentage Error (MAPE)

MAPE measures the average prediction error as a percentage of actual revenue.

A lower MAPE indicates more accurate predictions.

It is useful for comparing prediction accuracy across models.

Root Mean Squared Error (RMSE)

RMSE measures the typical size of the model's prediction errors in revenue units.

A lower RMSE indicates better predictive performance.

Larger errors receive more weight because the errors are squared.

R-Squared

R-squared measures the proportion of variation in revenue explained by the model using the training data.

A value closer to 1 means the model explains more of the variation in revenue.

R-squared should be considered together with out-of-sample measures such as MAPE and RMSE.

Visualizations

The notebook creates the following visualizations:

Revenue versus production with separate winter and non-winter regression lines

Revenue versus production with separate fall and non-fall regression lines

Actual versus predicted revenue for both models on the testing data

Bar chart comparing the MAPE of the winter and fall models

These graphs help show whether the seasonal models produce meaningfully different regression relationships and predictions.

Technologies Used

Python

Jupyter Notebook or Google Colab

NumPy

pandas

Matplotlib

statsmodels

Installation

Install the required Python packages with:

pip install numpy pandas matplotlib statsmodels

Google Colab normally includes these packages by default.

How to Run the Project

Download or open Week_10quiz.ipynb.

Place AICPA_regressionAnalysisData.csv in the same folder as the notebook.

Open the notebook in Jupyter Notebook or Google Colab.

Run the cells in order from top to bottom.

Review the model coefficients, prediction table, evaluation measures, and graphs.

Files

Week_10quiz.ipynb
AICPA_regressionAnalysisData.csv
README.md

Conclusion

The purpose of the analysis is to determine whether including winter or fall seasonality improves revenue predictions. The preferred model is the one that produces the lower testing MAPE and RMSE while also providing a reasonable explanation of how seasonality changes the relationship between production and revenue.
