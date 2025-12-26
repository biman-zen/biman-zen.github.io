---
layout: post
title: Yelp Reviews Sentiment Analysis
subtitle: Natural Language Processing using NLTK
cover-img: https://sbmi.uth.edu/blog/imgs/14-word-cloud-3-351x195.jpg
thumbnail-img: https://sbmi.uth.edu/blog/imgs/14-word-cloud-3-351x195.jpg
share-img: /assets/img/path.jpg
tags: [classification analysis, pandas, scikit-learn, nltk]
---

### Introduction
The goal of this project is to perform sentiment analysis ( to label a review is "positive", "negative", or "neutral" ) using natural language processing (NLP) on Yelp reviews dataset. Natural language processing (NLP) is the method by which computers make sense of written text. Sentiment analysis, a subfield of NLP, involves predicting the tone of a text. There are many reasons to understand the opinion expressed in text. Sentiment analysis can be useful for businesses trying to understand customer feedback, for a company launching a new product, or for determining the underlying emotion behind a stock. This project aims to apply sentiment analysis to a specific dataset and explore the nuances of its implementation.

### Dataset
The [Yelp reviews dataset](http://www.yelp.com/dataset_challenge) was developed for the 2015 Yelp Challenge and consists of reviews of businesses. The dataset is sourced from [hugging face](https://huggingface.co/datasets/Yelp/yelp_review_full). The dataset consists of two .csv files: training.csv with 650k records and test.csv. with 50k records. Although the feature engineering of the dataset was not needed, the necessary text preprocessing to normalize the data takes nearly an hour. 

### DW & EDA
There's little data wrangligng required for text based datasets for NLP in comparison to numerical and categorical datasets. For datasets with text features like this there is no need to perform in depth data wrangling or exploratory data analysis as with traditional datasets with many numerical and categorical features (e.g. car dataset).

#### Text Normalization
Normalization is the process that brings words into a standard format. These tokens can be words but can also be larger or smaller depending on the strategy. These token words can be further standardized using a method called lemmatization i.e. reducing the word to its root base form, as found in a dictionary. Standardization involves lower casing, removing stop-words, and performing lemmatization. The following is a code snippet of python code on standardizing the review text. For each review, the text is lower-cased, then the punctuations and stop words are removed, and then each word is lemmatized. 

'''python
def preprocess_text(text):
    # Tokenize the text
    tokens = word_tokenize(text.lower())

    # Remove stop words and punctuations in the tokens list
    stp_wrds_puncts = list()
    stp_wrds_puncts.append(string.punctuation)
    stp_wrds_puncts.extend(stopwords.words('english'))
    filtered_tokens = [token for token in tokens if token not in stp_wrds_puncts]
    
    # Lemmatize the tokens
    lemmatizer = WordNetLemmatizer()
    lemmatized_tokens = [lemmatizer.lemmatize(token) for token in filtered_tokens]

    # Join the tokens back into a string
    processed_text = ' '.join(lemmatized_tokens)

    return processed_text
'''

#### BOW and TF-IDF 
In the normalized tokens counted in terms of frequency is referred to as the bag of words approach. TF-IDF is a more robust method than BOW for vectorizing text as it attempts to look at how rare a word is as well as how frequent the word appears. The TF-IDF score for each word in a document is determined by multiplying its Term Frequency (TF) and its Inverse Document Frequency (IDF). The formula is:TF−IDF(t,d) = TF(t,d)×IDF(t)

### Results
Three ML models: Logistic regression, SVM, Naïve Bayes, and Random Forest machine learning models were trained on the data to perform multinomial classification. Additionally, a VADER pre-trained model was used as an “automatic” sentiment analyzer to validate against the classifier models. A comparison of the results was performed to show that logistic regression classification model performed the best outcome with an accuracy of nearly 70%.

Find the project files on the [github repository](https://github.com/biman-zen/nlp-sentiment-analysis).
