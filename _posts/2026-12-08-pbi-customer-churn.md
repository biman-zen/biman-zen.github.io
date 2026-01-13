---
layout: post
title: Analyzing Customer Churn in Power BI
subtitle: Cell Phone Service
cover-img: #
thumbnail-img: # 
share-img: /assets/img/path.jpg
tags: [Power BI, Customer Churn]
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

The data 'Get data' feature BI is used to import the excel file into Power BI.

The first action to verify the data is to confirm there are no duplicate customers. The following are DAX calculations to count the customer id using *'COUNT'* and *'DISTINCTCOUNT'*

![dax_count]({{"/assets/post_figures/pbi_churn/dax_count.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}

Using the card visual, we see that the two customer id count values are indeed the equal.

![count_cards]({{"/assets/post_figures/pbi_churn/count_cards.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}