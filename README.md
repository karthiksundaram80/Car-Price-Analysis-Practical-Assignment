# Car-Price-Analysis-Practical-Assignment:
## What drives the Price of a Car? Applying the CRISP-DM framework to a business problem
This project is a part of Module 11 - Practical Application - 2. This project aims to predict used car prices using various regression techniques.

### High-level data tasks:
    1) Pull the dataset into a data frame for analysis
    2) Look at the data description to understand missing values and basic statistics of each feature
    3) Transform the numeric features by standardizing them as needed
    4) Transform the numeric features into numeric data
    5) Encode the categorical features
    6) Reduce the cardinality of features having a large number of unique values
    7) Perform feature selection and regression analysis on the transformed data with price as the target variable

### Data Understanding:
    1) <b>Data Collection </b> - Data has been acquired from Kaggle (<b>Used Cars Dataset</b>). The original dataset contained information on 3 million used cars out of 
       which, we have pulled <b> only 426K records </b>.
    2) <b>Data Description </b> - There are <b>426,880 rows </b> and <b>18 columns</b> in this dataset. The format of this raw data is a <b> .csv</b> file.
       The target variable of the dataset is the column <b>"price"</b>.
    3) <b>Data Quality </b>- There are several columns missing data as observed. If more than 80 % of values are missing, the entire column will be dropped.

### Data Preparation:
    1) <b>Data Cleanup </b>: 
    a) Column "size" is missing a significant percentage of values. Since the value for this column can be inferred from column "type", we can drop 
       the column size.
    b) Also, columns <b>"VIN", "Id", and "region" </b> (can we infer region from feature <b>"state"</b>) don't provide much value for prediction.
      Therefore these columns can be dropped as well. 
    c) Finally, drop records where the value of the target feature <b>"price"</b> is <b>0</b> as it doesn't provide any
      value for prediction.

    2) <b>Remove Outliers</b>:
    a) Based on the analysis of column <b>"price"</b> for outliers by comparing the samples against Google to understand the actual real car price, it will be more 
       appropriate to take the percentile from <b>5 up to 99.7 to remove outliers and invalid car prices </b>.
    b) Considering any used car <b>mileage above 10K miles as minimum</b> and <b>below 500 K as maximum</b>, it will be more appropriate to take the <b>percentile from 6.68 
       and 99.7 </b>.

    3) <b>Handle missing values</b>:
    a) Features - <b>fuel, transmission, title_status, paint_color, and condition </b>- Replace the missing values with mode.
    b) Features - <b>year, manufacturer, and model - These features are missing only a few values. Delete records having <b>"Null"</b> values for one or more of these 
       features.
    c) Features- <b>cylinders and type </b> has a value called "other". We can use this value to replace the missing values for these features.
    d) Fill <b>Null</b> values for feature <b>drive</b> with value <b>fwd</b> as its the most common drivetrain.

    4) <b>Transform values</b>:
    a) Transform the feature <b>"Year"</b> to <b>age</b>.
    b) Use only the <b>main model</b> of the vehicle by <b>ignoring the trims</b>. Also, ignore the word <b>"cylinders"</b> in the feature cylinder.
    c) Since the <b>automatic transmission</b> is the most popular in the US, we can change the transmission having value as <b>"other" to "automatic"</b>
    d) Transform column <b>title_status</b> by moving status <b>"lien"</b> to <b>"clean"</b> and all other statuses to <b>"other"</b>.
    e) There are used cars that are <b>over 100 years old</b> in the dataset. To make the year relevant, we can eliminate used cars <b>beyond 30 years old</b> from our 
       dataset.
    f) Transform the <b>categorical variables to numeric </b> to be used for further analysis.

### Modelling:
Perform <b>Linear Regression</b>, <b>Lasso Regression</b>, and <b>Ridge Regression</b> on the resulting dataset
