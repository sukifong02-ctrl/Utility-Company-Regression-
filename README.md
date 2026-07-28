# Revenue Forecasting with Seasonal Regression

## Project Overview

This project analyzes the relationship between production activity and company revenue using multiple linear regression.

The objective was to determine whether seasonal factors improve the accuracy of revenue forecasts. I created seasonal dummy variables and interaction terms to compare how revenue responds to production during different times of the year.

This project demonstrates how accounting and finance professionals can use data analytics to:

* Forecast financial performance
* Identify seasonal revenue patterns
* Evaluate competing forecasting models
* Support budgeting and planning decisions
* Translate statistical results into business insights

## Business Question

**Can seasonal information improve revenue forecasts based on production levels?**

To answer this question, I compared two regression models:

1. A winter-based revenue model
2. A fall-based revenue model

The models were trained using historical data and evaluated using a separate testing dataset.

## Dataset

The dataset contains monthly company information, including:

* `date` — month of the observation
* `revenue` — monthly company revenue
* `production` — monthly production level
* `coolDD` — cooling degree days
* `heatDD` — heating degree days
* `type` — identifies training and testing observations

The data was divided into:

* **Training data:** used to estimate the regression models
* **Testing data:** used to evaluate forecasting accuracy

## Data Preparation

The date variable was converted into a Python datetime format so that each observation could be classified by season.

Two seasonal dummy variables were created.

### Winter Dummy Variable

The winter dummy equals:

* `1` for December, January, and February
* `0` for all other months

### Fall Dummy Variable

The fall dummy equals:

* `1` for September, October, and November
* `0` for all other months

Interaction terms were also created to determine whether the relationship between production and revenue changes during each season.

```python
winter_interaction = production × winter_DV
fall_interaction = production × fall_DV
```

## Regression Models

### Model 1: Winter Model

The winter model estimates revenue using:

* Production
* Winter dummy variable
* Winter-production interaction term

```text
Revenue = β₀ + β₁(Production) + β₂(Winter) 
          + β₃(Production × Winter) + ε
```

This model allows both the expected revenue level and the relationship between production and revenue to change during winter.

### Model 2: Fall Model

The fall model estimates revenue using:

* Production
* Fall dummy variable
* Fall-production interaction term

```text
Revenue = β₀ + β₁(Production) + β₂(Fall)
          + β₃(Production × Fall) + ε
```

This model tests whether fall months have a different revenue pattern than the rest of the year.

## Model Evaluation

The models were evaluated using:

* Mean Absolute Percentage Error
* Root Mean Squared Error
* Actual versus predicted revenue
* Regression visualizations

### Test-Data Results

| Model        |   MAPE |          RMSE |
| ------------ | -----: | ------------: |
| Winter Model | 15.90% | $2,285,842.41 |
| Fall Model   | 22.02% | $3,800,342.61 |

A production-only regression model produced a MAPE of approximately **25.42%**.

## Key Findings

* The winter model produced the lowest forecasting error.
* Adding seasonal information improved the forecast compared with using production alone.
* The winter model reduced MAPE from approximately 25.42% to 15.90%.
* Revenue appears to respond differently to production during winter months.
* The fall model performed worse than the winter model on the testing data.
* A model with a stronger training fit does not always produce more accurate out-of-sample forecasts.
* Testing a model on unseen data is important before using it for financial decisions.

## Business Interpretation

The results suggest that production alone does not fully explain changes in revenue.

Winter conditions may influence:

* Customer demand
* Product pricing
* Operating activity
* Production efficiency
* Energy consumption
* Revenue generated per unit of production

For budgeting and financial planning, management should consider including seasonal variables rather than relying only on production volume.

The winter model provided the strongest forecast among the models tested and may offer a better starting point for estimating future monthly revenue.

## Visualizations

The notebook includes visualizations comparing:

* Revenue and production
* Winter and non-winter regression lines
* Fall and non-fall regression lines
* Actual and predicted test-set revenue
* MAPE across the two seasonal models

These visualizations help communicate the regression results to users who may not have a technical background.

## Tools and Technologies

* Python
* Jupyter Notebook
* Pandas
* NumPy
* Matplotlib
* Statsmodels
* Ordinary Least Squares regression

## Skills Demonstrated

### Accounting and Finance

* Revenue forecasting
* Financial data interpretation
* Budgeting and planning analysis
* Seasonal performance analysis
* Business-focused model evaluation

### Data Analytics

* Data cleaning and preparation
* Training and testing data separation
* Dummy-variable creation
* Interaction-term analysis
* Multiple linear regression
* Predictive-model comparison
* MAPE and RMSE calculation
* Data visualization

## Repository Structure

```text
Revenue-Forecasting-Project/
│
├── Week_10quiz.ipynb
├── AICPA_regressionAnalysisData.csv
└── README.md
```

## How to Run the Project

1. Clone or download this repository.
2. Ensure that the notebook and CSV dataset are saved in the same folder.
3. Open the notebook using Jupyter Notebook, JupyterLab, or Google Colab.
4. Install the required Python libraries.
5. Run each notebook cell in order.

### Required Libraries

```bash
pip install numpy pandas matplotlib statsmodels
```

## Limitations

* The dataset contains a limited number of observations.
* The models focus mainly on production and seasonal effects.
* Other factors may also affect revenue, including pricing, customer demand, inflation, competition, and economic conditions.
* Seasonal categories simplify differences that may occur between individual months.
* Forecasting accuracy should be tested using additional periods before the model is used for major business decisions.

## Future Improvements

Future versions of this project could:

* Include cooling and heating degree days as predictors
* Add monthly dummy variables
* Examine economic and pricing information
* Test additional interaction terms
* Compare regression with time-series forecasting methods
* Conduct residual and regression-assumption testing
* Use a larger dataset
* Create an interactive financial dashboard

## About Me

I am an Accounting and Financial Management student interested in combining financial knowledge with data analytics.

My areas of interest include:

* Financial analysis
* Accounting
* Corporate finance
* Forecasting
* Business intelligence
* Data visualization
* Technology-supported decision-making

This project reflects my ability to apply Python and statistical modelling to practical accounting and finance questions.

