# What Drive the Price of a Car?

Introduction 

In my project, I analyzed a dataset comprising 3 million used cars sourced from Kaggle. 
Throughout the project, I employed the industry-standard CRISP-DM process (see below) for machine learning and data mining. 

![CRISP Model](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/CRISP%20Model.png)


DATA: Refer to the vehicles.zip file available in the repository 

Outline: Project Summary available in the repository

Detailed Analysis: Please refer to the Jupyter Notebook provided here


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

1. Check Missing Values in Three Ways
   
  1.1 Percentage of Missing Values for Each Variable

  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/MissingValues.png). 

  1.2 Density of Missing Values across different variables (Panda Profiling Analysis)
  
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/ProfilingMissing%20Values.png). 

  1.3 Nulllity Correlations among varibles (Panda Profiling Analysis)
  
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/NullityCorrelation.png). 
  
  Please Note:
  30% of VIN numbers are missing. which points to potential issues in data capture, data quality, or the application of privacy filters. This significant gap necessitates extensive data cleanup or imputation, 
  which could potentially skew the insights derived from predictive models

  Over 70% of Size variable values are missing. Drop the Size varible for sure. 
  
2. High Cardinality
   
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Cardinality.png) 


3. Imbalance in Categoircal Values
   
Take Fuel and Car Condition For Example 

![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Imbalance.png) 
![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/CarCondition.png) 
  
7. Incorrect Feature Type - Convert Cylinder Into Numerical Varible
8. Code Car Condition into Ordinary Numbers 


9. Remove Zero Pricing Cars and Cars with Savaged Conditions
    
![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PriceOutlier.png) 
![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/BoxplotPrices.png) 
 

11. Remove Numerical Outliers Using Quantile Approach
![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PricesScewedness.png)

    


13. Log price to improve central tendency
    
  
   
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
