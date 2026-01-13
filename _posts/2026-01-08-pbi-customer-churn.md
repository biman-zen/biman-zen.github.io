---
layout: post
title: Analyzing Customer Churn in Power BI
subtitle: Cell Phone Service
cover-img: /assets/img/telecom.png
thumbnail-img: # 
share-img: #/assets/img/path.jpg
tags: [Power BI, customer churn]
author: Biman Mondal
---

### Introduction
What is customer churn and what are the possible culprits? In this walkthrough, we'll tackle this challenge using Power BI to uncover customer churn within a hypothetical telecom company's (Databel) dataset. The interactivity of the charts will be demonstrated with static images since PowerBI Desktop doesn't allow dashboards to be published.

### Dataset and Import
The dataset is in an Excel spreadsheet and consists of customer status, demographics, contract information, and subscription charges. Below are some important columns however not the complete dataset.

Customer Status:

| Customer ID | Churn Label | Churn Reason | Churn Category |
| :---- |:----- | :------ | :------- |
| Unique ID | 'Yes'/'No' values | Reason to end contract  | Groups multiple churn reasons together |

Demographics:

| Gender | Under 30 | Senior | Age |
| :---- |:----- | :------ | :------- |
| 'Male'/'Female' | 'Yes'/'No' values | 'Yes'/'No' values  | Age (numerical) |

Contract type:


| Contract Type | Payment Method | State | Phone Number | Group | Number of customers in a group |
| :--------------: |:------: | :------ | :------- | :------- | :------- |
| 'Month-to-Month' / 'One Year' / 'Two Year' | 'Credit'/'Debit'/'Check' | State | Phone Number | 'Yes'/'No' values  | Numerical |

The data *'Get data'* feature BI is used to import the excel file into Power BI.

The first action to verify the data is to confirm there are no duplicate customers. The following are DAX calculations to count the customer id using *'COUNT'* and *'DISTINCTCOUNT'*

![dax_count]({{"/assets/post_figures/pbi-churn/dax_count.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}

Using the card visual, we see that the two customer id count values are indeed the equal.

![count_cards]({{"/assets/post_figures/pbi-churn/count_cards.png" | relative_url }}){:style="width:15%; height: auto; display: block; margin: 0 auto;"}

### Define Churn
The churn label is a column booleans that state whether a customer has churned. This is covered to the number of churned customers using the 'IF' condition and counting the "YES" values.
![num_churn]({{"/assets/post_figures/pbi-churn/dax_num_churned.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}

Churn rate is defined as the number of customers which stop doing business. The fraction of the churned customers and total customers will be referred to as churn rate.
Churn Rate = number of churned customers / number of total customers
The dax calculation of churn rate:
![churn_rate]({{"/assets/post_figures/pbi-churn/dax_churn_rate.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}

The calculated churn rate from above is formatted as percentage format and visualized with the cards below.
![churn_rate]({{"/assets/post_figures/pbi-churn/card_count_churn_rate.png" | relative_url }}){:style="width:20%; height: auto; display: block; margin: 0 auto;"}

### Visualize Churn
The following visualizes the churn count by state to show CA being the state with the highest churn rate.
![churn_state]({{"/assets/post_figures/pbi-churn/churn_bystate.png" | relative_url }}){:style="width:50%; height: auto; display: block; margin: 0 auto;"}

The following bar chart is a collection of reasons the customer churned as a percentage of the grand total (note the first bar indicates customers not churned). The chart shows the primary cause of churn reason is "Competitor had better offer".
![churn_reason]({{"/assets/post_figures/pbi-churn/chart_churn_reason.png" | relative_url }}){:style="width:50%; height: auto; display: block; margin: 0 auto;"}

The following chart shows churn rate by age group clearly showing that senior group has a higher churn rate.
![churn_demo]({{"/assets/post_figures/pbi-churn/chart_demographics.png" | relative_url }}){:style="width:70%; height: auto; display: block; margin: 0 auto;"}

The next set of chart shows churn rate by group showing that customers that are not part of a group plan are likely to have a higher churn rate.
![churn_demo]({{"/assets/post_figures/pbi-churn/chart_contract.png" | relative_url }}){:style="width:70%; height: auto; display: block; margin: 0 auto;"}

The churn rate by data plan shows that those who have an unlimited plan and also who use less than 5 Gb of data have a higher churn rate.
![churn_demo]({{"/assets/post_figures/pbi-churn/chart_data_plan.png" | relative_url }}){:style="width:40%; height: auto; display: block; margin: 0 auto;"}

Lastly the following figure shows the churn rate by account length and the payment method. The chart exposes that churn rate steadily decreases with account length.
![churn_demo]({{"/assets/post_figures/pbi-churn/churn_rate_payment.png" | relative_url }}){:style="width:80%; height: auto; display: block; margin: 0 auto;"}

Selecting the paper check bar, updates the churn rate chart accordingly. The churn rate chart shows that, for customers that pay with check, the churn rate sharply increases after 40 months. 
![churn_demo]({{"/assets/post_figures/pbi-churn/churn_rate_payment2.png" | relative_url }}){:style="width:80%; height: auto; display: block; margin: 0 auto;"}

### Dashboard
Adding several of the charts elements from above to a single page, creates a dashboard that clearly shows the relationships between features. 
![churn_demo]({{"/assets/post_figures/pbi-churn/dashboard1.png" | relative_url }}){:style="width:60%; height: auto; display: block; margin: 0 auto;"}

As stated above, CA has the highest rate of churn. Information regarding customer behavior can be investigating by interacting with the map. TX is selected in the map chart below; note the update to the churn rate card and churn reasons bar chart.
![churn_demo]({{"/assets/post_figures/pbi-churn/dashboard2.png" | relative_url }}){:style="width:60%; height: auto; display: block; margin: 0 auto;"}

### Summary
In summary, this analysis was an introductory demonstration of basic DAX , data analysis, and dashboard development in Power BI. The Databel customer churn dataset was interrogated to determine the causes for customer churn. Demographics, group plan, and account type all play a factor of why customers stop doing business. 