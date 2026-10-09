# 📊 Superstore Sales, Profit & Loss Risk

A practical retail analytics and machine learning project using Python and Jupyter Notebook.

The project explores sales and profitability, predicts profit per order line, and identifies transactions likely to make a loss.

## Project Focus

**High sales do not always mean high profit.**

This project examines which product groups generate profit, where losses occur, and whether sales information can help predict profitability.

Exploratory data analysis describes historical patterns. Machine learning extends the analysis by predicting outcomes for later transactions.

The findings are relevant to retail, e-commerce, sales analytics, and pricing teams.

## Business Questions

- Which categories and sub-categories generate the most profit?
- How do sales and profit change over time?
- How do discounts relate to profitability?
- How much profit or loss might an order line generate?
- Can we identify order lines likely to make a loss?

## Project Workflow

| Section | Purpose |
|---|---|
| Business understanding & data dictionary | Define the questions, targets, and meaning of the columns |
| Data preparation | Load the CSV and check missing values, duplicates, and dates |
| Feature engineering | Create useful predictors and the loss-classification target |
| Exploratory data analysis | Examine distributions, comparisons, trends, and relationships |
| Regression | Compare models and evaluate profit predictions |
| Classification | Compare models and evaluate loss detection |
| Business review | Interpret predictions, findings, and limitations |

## Exploratory Data Analysis

The notebook includes:

- Profit distribution
- Profit by category and sub-category
- Monthly sales and profit
- Discount and profit relationships
- Correlations between numeric features

EDA uses the training period so that the final test year does not guide model choices.

## Why Two Machine Learning Tasks?

The project solves **two different prediction problems**:

| Task | Question | Target | Practical use |
|---|---|---|---|
| Regression | How much profit or loss might an order line generate? | `Profit` | Estimate the financial outcome |
| Classification | Is an order line likely to make a loss? | `Loss_Flag`: 1 = loss, 0 = no loss | Flag transactions for review |

Regression predicts an amount. Classification predicts a class. Together, they provide two views of profitability.

Several algorithms are compared within each task rather than assuming that one model will perform best.

## Models & Evaluation

### Regression — Predict Profit

**Models:** Linear Regression, Decision Tree Regressor, and Extra Trees Regressor.

| Metric | Meaning | Better |
|---|---|---|
| MAE | Average absolute prediction error | Lower |
| MSE | Average squared prediction error | Lower |
| RMSE | Square root of MSE, expressed in profit units | Lower |
| R² | Performance relative to predicting the mean | Higher |

Models are selected by **validation MAE** and compared with a median-profit baseline.

The final evaluation includes a metric table and an **Actual vs. Predicted Profit** chart.

### Classification — Predict Loss Risk

**Models:** Decision Tree Classifier and Random Forest Classifier.

| Metric | Meaning | Better |
|---|---|---|
| Accuracy | Share of all order lines classified correctly | Higher |
| Precision | Share of loss alerts that are real losses | Higher |
| Recall | Share of actual losses detected | Higher |
| F1 | Balance between loss precision and recall | Higher |

Precision, Recall, and F1 refer to the **loss class**. Models are selected by **validation F1** and compared with a majority-class baseline.

The final evaluation includes a metric table and a **Confusion Matrix**, showing detected losses, missed losses, and false alerts.

## Training, Validation & Testing

| Period | Role |
|---|---|
| 2014–2015 | Train candidate models |
| 2016 | Compare models and select the best for each task |
| 2017 | Evaluate the selected models on later transactions |

After selection, the chosen models are refitted on **2014–2016** before predicting the **2017 test data**.

`Profit` and profit-derived columns are excluded from the input features. The final test results do not determine model selection.

Short `algo_test` functions collect the model scores in clear comparison tables.

## Business Findings & Value

Across the full dataset, **Technology generated the highest total profit**, while **Tables, Bookcases, and Supplies recorded overall losses**.

The analysis can help business teams:

- Identify product groups that need a profitability review
- Examine discounts alongside product and regional performance
- Estimate profit for later order lines
- Prioritize potential loss-making transactions for human review

Predictions support investigation and decision-making. They do not justify automatically rejecting an order.

## Tools

Python · Pandas · Matplotlib · Seaborn · Scikit-learn · Jupyter Notebook


## Limitations

- The project uses one historical dataset and one validation year.
- Some large profit prediction errors remain.
- Customers and products may appear in several years; performance on entirely new customers or products is not separately evaluated.
- Discount relationships are observational and do not establish causation.
- Results may vary slightly across library versions and do not guarantee future performance.

## Possible Next Steps

- Evaluate models across additional time periods
- Investigate large prediction errors
- Assess the business costs of missed losses and false alerts
- Explore classification thresholds using validation data
