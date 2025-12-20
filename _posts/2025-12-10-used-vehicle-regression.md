---
layout: post
title: Prediction of Used Vehicle Price
subtitle: Regression Analysis using Scikit-learn
cover-img: #/assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [pandas, scikit-learn, regression analysis]
author: Biman Mondal
---
![image](https://www.usatoday.com/gcdn/media/2018/06/14/USATODAY/usatsports/car-lot-square-e1461855298700.jpg?width=500&height=500&fit=crop&format=pjpg&auto=webp){:style="width: 60%; height: auto; display: block; margin: 0 auto;"}

### Introduction
This machine learning project tackles the challenge of predicting used car prices. The original dataset was scraped from Craigslist and Carvana in 2021, available from [Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data). This project was a capstone project part of the Springboard Data Science course. 

The motivation of this ML project was to use a real world dataset to perform all the steps involved in the data science process. A significant portion of this work focused on tidying the scraped raw data for modeling. The dataset includes 426k+ rows of values and 26 columns.

This ML project uses the *Pandas Python library* to create and modify the dataset and *Scikit-Learn* to perform the machine learning. The code segmented across four Jupyter notebooks. Craigslist is a well-known text based online platform for posting local ads. The dataset was scraped from Craigslist and also included some CarMax data mixed as well.  The freeform input that the site allows results in numerous unintended errors. There are misspellings of the model and make, irregularities in price, and general missing-ness of data. The challenges of wrangling the data were not fully appreciated until well into the project.

### Preparing the Dataset
Many of the records of the dataset are missing and require imputing or dealing with them another way. Using the MSNO package, the following shows the missing-ness of dataset. Note that the "County" column is completely empty; there is a "Region" column but a CL region is not the same as a State County.

![Missing_values]({{"/assets/post_figures/used-car-regression/missing_values.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}

Attempting to fill the dataset with missing data would require too much time. Only columns associated with the vehicle itself were, dropping location information, image, and description information. Other information regarding VIN and color did not seem important. Here is a final view of the dataset after the data wrangling process.

In the exploratory section, the dataset reveals more about the dataset. There are nearly 20k+ unique models in the directory because of Craigslist free input area. The price seems to centered around 20k and most of the vehicles were manufactured after 2000. The median odometer is around 100k miles and the common sizes of the engine is (4,6, and 8) cylinders.
![histogram]({{"/assets/post_figures/used-car-regression/histogram.png" | relative_url }}){:style="width:50%; height: auto; display: block; margin: 0 auto;"}

The top four models in the dataset all US trucks with Ford and Chevy the top makes. 
![top10]({{"/assets/post_figures/used-car-regression/top_10_model_makes.png" | relative_url }}){:style="width:50%; height: auto; display: block; margin: 0 auto;"}

The model names required standardization to simplify the modeling e.g. a model called 'silverado 1500' and 'silverado' should be equivalent. The following code snippet shows how each model names were condensed. 
    
    # Combine the f-250 model segment
    vehicles.loc[vehicles.model.str.contains('f.250.'), 'model']
    vehicles.loc[(vehicles.model.str.contains('.f*.250.')) & (vehicles.manufacturer=='ford'),'model'] = 'f-250'
    vehicles.loc[vehicles.model.str.contains('f*.250.') & (vehicles.manufacturer=='ford'),'model'] = 'f-250'
    vehicles.loc[vehicles.model.str.contains('f250') & (vehicles.manufacturer=='ford'),'model'] = 'f-250'

To simplify modeling, the final dataset included the top 60 used car models as it covers the majority of the dataset.
![unique_models]({{"/assets/post_figures/used-car-regression/unique_models_record.png" | relative_url }}){:style="width:50%; height: auto; display: block; margin: 0 auto;"}

### Modeling
The down sampled dataset reduces to ~284k rows; reducing the original dataset by nearly 40%. With a cleaned dataset, the categorical columns were transformed using *OneHotEncoding*. This increases the columns of the dataset because the each category becomes its own column. 

The numerical values in the histograms above demonstrate the different scales of each feature. The odometer is on the order of 10^5 while, year is on the order of 10^3, and the cylinders is 10^0 order. The scale of the features can affect the performance of certain models like linear regression and SVM. Below is the transformed columns into a normal distribution using *QuantileTransformer*.  
![quant_trans]({{"/assets/post_figures/used-car-regression/quant_norm_num_data.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}

Regression models: Linear Regression, Ridge Regression, K-Nearest Neighbors (KNN), and Random Forest Regression were chosen to fit the data and compare error rates. In order to minimize overfitting to the data, the model used 5-fold cross-validation. In addition to CV, for models like RF and KNN GridSearchCV was used to perform hyperparameter optimization; i.e. to find the parameter combination yielding best error results.

	# Create the parameter grid based on the results of random search 
	params = {
		'max_depth': [None],
		'min_samples_leaf': [1, 5],
		'max_features': [None]
	}
	
	rf = RandomForestRegressor(n_jobs=-1, random_state=30)
	# Grid search CV defaults to a kFold = 5
	grid_rf = GridSearchCV(estimator=rf, cv = 5, 
                        param_grid=params, 
                        n_jobs=-1, verbose=1, 
                        scoring='neg_mean_absolute_percentage_error')

It is common to use RMSE as the standard error, but mean absolute error was chosen so the error value is a decimal.

<div style="text-align: center;">

Root mean square error:  
$
\text{RMSE} = \sqrt{\frac{\sum_{i=1}^{N} (P_i - A_i)^2}{N}}
$ 
Mean absolute percent error:    
$
\text{MAPE} = \frac{1}{n} \sum_{i=1}^{n} \left| \frac{A_i - P_i}{A_i} \right| 
$
$A_i$ is actual value and $P_i$ is predicted value.
</div>    

*Note that MAPE is scaled producing relative error from 0 to 1. Although stated as percent error, sklearn MAPE requires scaling by 100 to become a percentage.*

The four models choses, produce the following errors; plotted with the error standard deviation.

![results]({{"/assets/post_figures/used-car-regression/model_results.png" | relative_url }}){:style="width:75%; height: auto; display: block; margin: 0 auto;"}

For more details regarding the analysis, refer to the [project's GitHub repository](https://github.com/biman-zen/ml_regression_used_vehicle) for the *Jupyter notebooks* and the [project report](https://github.com/biman-zen/ml_regression_used_vehicle/blob/main/CapstoneII_FinalReport_CLUsedCarDataset.pdf). All of these challenges were attempted with my know-how at the time. Looking back, I see many improvements that can be attempted. 

