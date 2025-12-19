---
layout: post
title: Prediction of Used Vehicle Price
subtitle: Regression Analysis using Scikit-learn
cover-img: #/assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [pandas, scikit-learn, regression analysis]
author: #Sharon Smith and Barry Simpson
---

![image](https://www.usatoday.com/gcdn/media/2018/06/14/USATODAY/usatsports/car-lot-square-e1461855298700.jpg?width=500&height=500&fit=crop&format=pjpg&auto=webp){:style="width: 60%; height: auto; display: block; margin: 0 auto;"}

This machine learning project tackles the challenge of predicting used car prices.  The original dataset was scraped from Craigslist and Carvana in 2021, available from [Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data). 
This project was a capstone project part of the Springboard Data Science course. 

The motivation of this project was to use a real world dataset to perform all the steps involved in the data science process. A significant portion of this work focused on tidying the scraped raw data for modeling. The dataset includes 426k+ rows of values and 26 columns. 

This project uses the Pandas Python library to create and modify the dataset and Scikit-Learn to perform the machine learning. Many of the records of the dataset are missing and require imputing or dealing with them another way. Using the MSNO package, the following shows how much missing data is there in the dataset.
[Insert image of missing values]

Craigslist is a well-known text based online platform for posting local ads. The dataset was scraped from Craigslist and included some CarMax data mixed in as well. The freeform input that the site allows results in numerous unintended errors. There are misspellings of the model and make, irregularities in price, and general missing-ness of data. The challenges of wrangling the data were not fully appreciated until well into the project.

Attempting to fill the dataset with missing data would require too much time. Only columns associated with the vehicle itself were, dropping location information, image, and description information. Other information regarding VIN and color did not seem important. Here is a final view of the dataset after the data wrangling process.

In the exploratory section, the dataset reveals more about the 
The price seems to centered around 20k and most of the vehicles were manufactured after 2000. The median odometer is around 100k miles and the common sizes of the engine is (4,6, and 8) cylinders. 

There are nearly 20k+ unique models in the directory because of Craigslist free input area. 

[insert plot] 


To simplify modeling, the final dataset included the top 60 used car models. This was chosen because most of the dataset is covered by 60 models.

[ Insert plot of figure ] 

The down sampled dataset reduces to around XXXXX rows. 

With the cleaned dataset, four different machine learning algorithms: Linear Regression, Ridge Regression, K-Nearest Neighbors (KNN), and Random Forest Regression were used in conjunction with 5-fold cross-validation to determine model performance. 

GridSearchCV was used to perform hyperparameter tuning of RF and KNN models to use the optimum parameters. The top-performing model achieved a cross-validated MAPE of 0.48. 

All of these challenges were attempted with my know-how at the time. Looking back, I see many improvements that can be attempted.
For a detailed discussion of the analysis refer to the [project gihub repository](https://github.com/biman-zen/springboard_second_capstone/tree/main) and the [project report](https://github.com/biman-zen/springboard_second_capstone/blob/main/CapstoneII_FinalReport_CLUsedCarDataset.pdf).

