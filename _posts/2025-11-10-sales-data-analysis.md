---
layout: post
title: Sales Aggregation of Fictitous Co.
subtitle: Data Analysis using Pandas
cover-img: 
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [data analysis, pandas, seaborn]
---

## Introduction
The sales team at Pens & Printers wanted to know which sales approach drives the most revenue for their newly launched stationery line and how that revenue evolves over the first six weeks after launch. By digging into a 15 000‑row, eight‑column dataset, the goal was to surface actionable insights that could sharpen the sales strategy and lift the bottom line.

### Questions from Sales Team
	1. How many customers were there for each approach?
	2. What does the spread of the revenue look like overall? And for each method?
	3. Was there a difference in the revenue over time for each method?
	4. Based on the data, which method would recommend we continue to use? (some methods may take more time than the team so they may not be the best for us) We don't know anything between the customers in each group.

## Analysis
Technical note: Missing revenue values (≈ 7 % of rows) were imputed via a linear‑regression model that leveraged the sales‑method indicator, ensuring the final analysis wasn’t biased by naïve mean‑filling.

## Recommendation 
	1. Measure both volume and value—the biggest revenue bucket isn’t always the most profitable per sale.
	2. Layer outreach—start cheap and scalable (email), then add a high‑touch element (call) for the most promising leads.
Let the data speak—even a modest‑size dataset can reveal nuanced patterns that reshape your go‑to‑market playbook.

Find the full [report](https://github.com/biman-zen/springboard_mini_projects/blob/main/data%20analysis/DA_Practical_Exam.ipynb) and [presentation](https://github.com/biman-zen/springboard_mini_projects/blob/main/data%20analysis/DA_Practical_Exam_Presentation.pdf) in my github repository.

