---
layout: post
title: Sales Aggregation of Fictitous Co.
subtitle: Data Analysis using Pandas
cover-img: 
thumbnail-img: /assets/11-10-analysis/Total_Revenue_bySales.png
share-img: /assets/img/path.jpg
tags: [data analysis, pandas, seaborn]
---

The following is a time-constrained data analysis problem performed for a certification test.   
### Problem  
The sales team at Pens & Printers wanted to know which sales approach drives the most revenue for their newly launched stationery line and how that revenue evolves over the first six weeks after launch. By digging into a 15,000‑row, 8‑column dataset, the goal was to surface actionable insights that could sharpen the sales strategy and lift the bottom line. 

#### Questions from Sales Team
	1. How many customers were there for each approach?
	2. What does the spread of the revenue look like overall? And for each method?
	3. Was there a difference in the revenue over time for each method?
	4. Based on the data, which method would recommend we continue to use? (some methods may take more time than the team so they may not be the best for us)
	5. How should the business monitor what they want to achieve?
    6. Estimate the initial values for the metric vased on the current data?

### Data Cleaning
The Pandas library in Python was used to evaluate the comma-delimited file. The dataframe contains 8 columns and 15000 rows. 
![Distribution Plot]({{"/assets/post_figures/11-10-analysis/dataset_figure.jpg" | relative_url}}){:style="width: 60%; height: auto; display: block; margin: 0 auto;"}

Investigating datatypes shows that 3 categorical values: sales method, customer id, and state (location) of the customer. The numerical values include the number of weeks, the number of products sold, and revenue. There were 1074 missing values from the revenue column which were imputed via a linear‑regression model that leveraged the sales‑method indicator. Duing this ensured that the final analysis wasn’t biased by naïve mean‑filling.

### Data Analysis
A kernal density (KDE) plot of the sales show that the sales methods are not distributed equally. The 'Call' method is in one end and 'Email + Call' method is on another end. The 'Email' method has higher density and narrower band.
![Distribution Plot]({{"/assets/post_figures/11-10-analysis/KDE_revenue_distribution.png" | relative_url }}){:style="width: 60%; height: auto; display: block; margin: 0 auto;"}  

A count of the sales method shows that sales by 'Email' is the primary method at 50%, 'Call' occurs at 33%, and 'E-mail + Call' is 17% of the dataset.
![Pie Chart]({{"/assets/post_figures/11-10-analysis/SalesMethod_Proportion_PieChart.png" | relative_url }}){:style="width: 60%; height: auto; display: block; margin: 0 auto;"}  

Aggregating the results show that the Email sales method generates the majority of revenue at 51%, followed by email + calling at 33% of revenue, followed by just calling at 16% of revenue.
![Revenue Chart]({{"/assets/post_figures/11-10-analysis/Total_Revenue_bysales.png" | relative_url }}){:style="width: 60%; height: auto; display: block; margin: 0 auto;"}

The total sales across the time frame seems to be steady with a low dip in the final week.
![Revenue Chart]({{"/assets/post_figures/11-10-analysis/Total_Revenue_acrossWeeks.png" | relative_url }}){:style="width: 60%; height: auto; display: block; margin: 0 auto;"}

### Recommendation
Based on the analysis above, the recommended using the 'Email' sales method as it yields a much higher average revenue than 'Call'. The metric to monitor in improving sales across weeks is 'Average Revenue/Sale'. 

Find the full [report](https://github.com/biman-zen/springboard_mini_projects/blob/main/data%20analysis/DA_Practical_Exam.ipynb) and [presentation](https://github.com/biman-zen/springboard_mini_projects/blob/main/data%20analysis/DA_Practical_Exam_Presentation.pdf) in the github repository.



