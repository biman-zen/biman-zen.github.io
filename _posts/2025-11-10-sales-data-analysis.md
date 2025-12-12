---
layout: post
title: Sales Aggregation of Fictitous Co.
subtitle: Data Analysis using Pandas
cover-img: 
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [data analysis, pandas, seaborn]
---

### Introduction
The sales team at Pens & Printers wanted to know which sales approach drives the most revenue for their newly launched stationery line and how that revenue evolves over the first six weeks after launch. By digging into a 15,000‑row, eight‑column dataset, the goal was to surface actionable insights that could sharpen the sales strategy and lift the bottom line. 

#### Questions from Sales Team
	1. How many customers were there for each approach?
	2. What does the spread of the revenue look like overall? And for each method?
	3. Was there a difference in the revenue over time for each method?
	4. Based on the data, which method would recommend we continue to use? (some methods may take more time than the team so they may not be the best for us)
	5. How should the business monitor what they want to achieve?
    6. Estimate the initial values for the metric vased on the current data?

### Data Cleaning
The Pandas library in Python was used to evaluate the comma-delimited file. The dataframe contains 8 columns and 15000 rows. The columns are: | week | sales_method | customer_id | nb_sold | revenue |'years_as_customer'|'nb_site_visits'|'state'. Investigating datatypes shows that 3 categorical values: sales method, customer id, and state (location) of the customer. The numerical values include the number of weeks, the number of products sold, and revenue. There were 1074 missing values from the revenue column which were imputed via a linear‑regression model that leveraged the sales‑method indicator. Duing this ensured that the final analysis wasn’t biased by naïve mean‑filling.

### Exploratory Data Analysis
The revenue is grouped by the sales method and plotted in the following bar chart. The results show that the Email sales method generates the majority of revenue at 51%, followed by email + calling at 33% of revenue, followed by just calling at 16% of revenue.

![Sales Chart]({{"_posts/post_figures/nov_data_analysis/KDE_revenue_distribution.png" | relative_url }})
![Revenue Chart]({{"/assets/post_figures/11-10-analysis/Revenue_by_sales_method_box.png" | relative_url }})

### Recommendation 
	1. Measure both volume and value—the biggest revenue bucket isn’t always the most profitable per sale.
	2. Layer outreach—start cheap and scalable (email), then add a high‑touch element (call) for the most promising leads.

Find the full [report](https://github.com/biman-zen/springboard_mini_projects/blob/main/data%20analysis/DA_Practical_Exam.ipynb) and [presentation](https://github.com/biman-zen/springboard_mini_projects/blob/main/data%20analysis/DA_Practical_Exam_Presentation.pdf) in my github repository.



