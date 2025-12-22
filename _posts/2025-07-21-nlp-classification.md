---
layout: post
title: Yelp Reviews Sentiment Analysis
subtitle: Natural Language Processing using NLTK
cover-img: 
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [classification analysis, pandas, scikit-learn, nltk]
---
The goal of this project is to perform sentiment analysis ( to label a review is "positive", "negative", or "neutral" ) using natural language processing (NLP) on Yelp reviews dataset.

The [Yelp reviews dataset](http://www.yelp.com/dataset_challenge) was developed for the 2015 Yelp Challenge and consists of reviews of businesses. The dataset is sourced from [hugging face](https://huggingface.co/datasets/Yelp/yelp_review_full). The dataset consists of two .csv files: training.csv with 650k records and test.csv. with 50k records. Although the feature engineering of the dataset was not needed, the necessary text preprocessing to normalize the data takes nearly an hour. To prevent duplicating preprocessing efforts, the dataframe was written to a local binary file (pickled). The binary files are not included in this repository but can be downloaded from this Google drive [link](https://drive.google.com/file/d/1WKdlvj4rsKd-qf5IMxrmHtfQd6Gcw7UE/view?usp=drive_link). Note that the .csv files must be present in the repository to run the jupyter notebooks. 

Three ML models: Logistic regression, SVM, Naïve Bayes, and Random Forest machine learning models were trained on the data to perform multinomial classification. Additionally, a VADER pre-trained model was used as an “automatic” sentiment analyzer to validate against the classifier models. A comparison of the results was performed to show that logistic regression classification model performed the best outcome with an accuracy of nearly 70%.

