# Tableau Productivity and Well-Being Analysis

This repository contains the **Tableau dashboard** and related **SQL code** for analyzing the productivity and well-being of remote vs in-office workers.

## Files
- `remote_productivity_analysis.twbx`: Tableau workbook with the dashboard and visualizations.
- `remote_productivity_data.csv`: Dataset used for analysis.
- `README.md`: This file containing project details.

## How to Run
1. Open the **Tableau workbook** (`remote_productivity_analysis.twbx`) in Tableau Desktop or Tableau Public.
2. Interact with the dashboard to explore insights into the productivity and well-being of remote vs. in-office workers.

## Key Insights
- **Remote workers tend to be more productive** than in-office employees, with an average productivity score of **73.63** compared to **63.77** for in-office workers.
- **Remote workers also have higher well-being scores**, suggesting that better work-life balance is a contributing factor.
- **Higher well-being correlates with higher productivity**, particularly for remote workers.
- **Data Analysis** is based on SQL queries to extract insights, including:
    - **Productivity distribution** by employment type.
    - **Correlation between hours worked, productivity, and well-being**.

#Process Documentation: Productivity and Well-Being Analysis
1. Project Overview
The goal of this project was to analyze the productivity and well-being of remote vs in-office workers using SQL for data analysis and Tableau for visualization. The primary objective was to understand how remote work impacts employee productivity and happiness.

2. Data Collection and Preparation
Data Source: The dataset used for analysis contains several key metrics, including:
Employment Type: Whether the employee works remotely or in the office.
Productivity Score: A metric indicating the employee's productivity.
Well-Being Score: A metric indicating the employee's happiness and well-being.
Hours Worked Per Week: The number of hours worked by the employee each week.
SQL Queries:
We wrote several SQL queries to extract insights from the data:

1. Productivity Comparison Between Remote and In-Office Workers:
This query calculates the average productivity for both remote and in-office employees, as well as other statistical metrics such as the min, max, first quartile, median, and third quartile.

SQL Queries:
We wrote several SQL queries to extract insights from the data:

1. Productivity Comparison Between Remote and In-Office Workers:
This query calculates the average productivity for both remote and in-office employees, as well as other statistical metrics such as the min, max, first quartile, median, and third quartile.

-- Compare Productivity Between Remote and In-Office Workers
SELECT 
  Employment_Type, 
  AVG(Productivity_Score) AS Avg_Productivity,
  MIN(Productivity_Score) AS Min_Productivity,
  MAX(Productivity_Score) AS Max_Productivity,
  APPROX_QUANTILES(Productivity_Score, 4)[OFFSET(1)] AS First_Quartile,
  APPROX_QUANTILES(Productivity_Score, 4)[OFFSET(2)] AS Median_Productivity,
  APPROX_QUANTILES(Productivity_Score, 4)[OFFSET(3)] AS Third_Quartile
FROM `data-analytics-learning-448713.Remote_work_portfolio.remote_work`
GROUP BY Employment_Type;

2. Hours Worked vs. Well-Being Correlation:
This query calculates the correlation between the number of hours worked per week and well-being scores to assess whether longer work hours negatively affect well-being.

-- Correlation between Hours Worked and Well-Being
SELECT 
  CORR(Hours_Worked_Per_Week, Well_Being_Score) AS Hours_WellBeing_Correlation
FROM `data-analytics-learning-448713.Remote_work_portfolio.remote_work`;

3. Productivity vs. Well-Being Correlation:
This query calculates the correlation between well-being and productivity to assess whether happier employees tend to be more productive.

-- Correlation between Well-Being and Productivity
SELECT 
  CORR(Well_Being_Score, Productivity_Score) AS WellBeing_Productivity_Correlation
FROM `data-analytics-learning-448713.Remote_work_portfolio.remote_work`;

3. Tableau Visualizations
Using Tableau, we created several visualizations to present the data insights.

4. Insights and Conclusions
Remote workers have higher productivity and well-being compared to in-office workers.
There is a strong positive correlation between well-being and productivity, especially for remote workers.
Remote work contributes to both better performance and happiness, likely due to work-life balance and flexibility.
## Technologies Used
- **SQL** for data analysis and querying.
- **Tableau** for data visualization.