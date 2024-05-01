# What Drive the Price of a Car?

Introduction 

In my project, I analyzed a dataset comprising 3 million used cars sourced from Kaggle. 
Throughout the project, I employed the industry-standard CRISP-DM process (see below) for machine learning and data mining. 

![CRISP Model](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/CRISP%20Model.png)


DATA: Refer to the vehicles.zip file available in the repository 

Outline: Project Summary available in the repository

Detailed Analysis: Please refer to the Jupyter Notebook provided here 

Panda Profiling Analysis: https://github.com/Sandysmile/Car-Prediction/blob/main/output.html 


# Business Understanding/Goals

Objective:
Develop a machine learning model to accurately predict used car prices.

Data Features: 
It includes many predictors like manufacturer brand, model year, odometer readings, and condition to help estimate market prices.

Business Rationale: 
Car specifications, aesthetic factors, and condition indicators determine market prices, affecting their desirability and value.
Application: Enables car dealerships to optimize inventory and marketing strategies based on insights from the model, enhancing sales and profitability.

Goals: 

1. Identify the most effective model for price prediction.
2. Present key features that significantly impact car prices to enhance dealership decision-making.

Business Outcome: 
This analysis will help understand buyer preferences, manage car inventory risk and quality, enable targeted market segmentation,
and implement dynamic pricing strategies to maximize profitability. 

   
# Data Understanding

## Data Structure 

![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Data%20Structure.png).
 
# Data Quality Check 

1.Check Missing Values in Three Ways
   
  1.1 Variable Statistics for Percentage of Missing Values

  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/MissingValues.png). 

  1.2 Density of Missing Values Comparision (Refer to Panda Profiling Analysis)
  
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/ProfilingMissing%20Values.png). 

  1.3 Nullity Correlations among varibles (Refer to Panda Profiling Analysis)
  
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/NullityCorrelation.png). 
  
  1.4 Immediate Actions and Insights:
  
  ~ Drop 'VIN': High proportion of missing values and irrelevant for predicting car 
  prices. Concerns about data integrity prompt careful handling of missing data and 
  preprocessing. 
  
  ~ Drop 'Size': Removed due to over 70% missing values, suggesting limited utility
  for the model. 
  
  ~ Drop 'Region' and 'State': Excluded due to high cardinality and lack of demand and 
  supply data by region, which limits their predictive value. 
  
  ~ Drop 'id': Irrelevence 
  
  ~ Focus on Key Features: Emphasis on more critical factors like Manufacturer and 
  Model for further exploratory analysis, as they significantly influence second-hand 
  car prices.
  
2. Inital EDA Insights Including Profiling Analysis or Data Preparation Actions
   
   2.1 High Cardinality - Regroup Key Relevent Feature Such as Manufacturer
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Cardinality.png)
    
   2.2 Imbalance in Categoircal Values
   Take Fuel and Car Condition For Example 
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Imbalance.png) 
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/CarCondition.png)
   
   2.3 Incorrect Feature Type - Convert Cylinder Into Numerical Varible

   2.4 Car Condition Can be coded into as a Ordinarical Numberic feature

   2.5 Remove Zero Pricing Cars and Cars with Savaged and other abnormal car Conditions
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PriceOutlier.png)
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/BoxplotPrices.png)
      
  
   2.6 drop all missing values from drive, type, and paint_color
   
   The model's performance is very bad after coding all missing values as 'unknown'.
   So I decided to drop all missing values from 'drive', 'type', and 'paint_color'

   2.7 Only cylinder_numeric and condition_numeric have missing values now.
   Their missing values will be imputated using their median values after splitting the dataset into train and test dataset to avoid data leakage.
   
   2.8 Remove Numerical Outliers Using Quantile Approach to avoid the extreme skewedness.
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PricesScewedness.png)
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/yeardistribution.png)

   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/YearswithCurve.png)
   


   2.7. Log price to improve central tendency
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/LoggedPrice.png)
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/LoggedpricewithCurve.png)

   
4. Final Cleaned Data Overview and Plots

5.     
  
   
Numerical

Categorical 

Categorical to Numerical

Target Variable Price


Data Preparation

Remove Outliers

Correlations 

Prices with years, type, highlighted analysis

Modeling (4) 

Simple Linear Regression with Polynomial
Ridge 
Ridge with Polynomial
Lasso, SequentialFeatureSelector with Polynomial

Evaluation

Plot all model results

The best model is:
Ridge with Polynomial
Understand the coefficent, and importance. 


Feature analysis 
