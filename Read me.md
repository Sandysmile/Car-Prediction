# What Drive the Price of a Car?

Introduction 

In the project, I analyzed a dataset comprising 3 million used cars sourced from Kaggle. 
Throughout the project, I employed the industry-standard CRISP-DM process (see below) for machine learning and data mining. 

![CRISP Model](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/CRISP%20Model.png)


DATA: Refer to the vehicles.zip file available in the repository 

Outline: Project Summary available in the repository 
https://github.com/Sandysmile/Car-Prediction/blob/main/Project%20Outline.pdf 

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
  
 # Data Preparation: EDA and Profiling Analysis help me prepare Data for modelling,
   
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
   before 

   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PricesScewedness.png) 
   
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/yeardistribution.png) 
   

   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/YearswithCurve.png) 
   
   

   2.7. Log price to improve central tendency
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/LoggedPrice.png) 
   
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/LoggedpricewithCurve.png) 
   


   2.8. Correlation among Numerical Variables

   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Correlations.png) 
   
   
   
   2.9 Final Cleaned Data Overview and Selected Plots for Business Insights

   2.9.1 Number of Cylinders Distribution (Before Imputation)


   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Cylinderswith%20Price.png) 
   
   
   
   2.9.2 Car Condition Numerical Value Distribution (Before Imputation)
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/CarconditionwithPrice.png) 
   
   
   2.9.3 Median Prices and Counts by Year with Curve

   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/YearMedianPriceCounts.png) 
   

   
   2.9.4 Counts and Median Prices by Number of Cylinders
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/CylinderswithMedianPrice.png) 
   
  
   2.9.5 Counts and Median Prices by Car Condition

   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/ConditionMedianPrice.png) 
   

   2.9.6 Counts and Median Prices by Manufacturer Group

   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/ManufacturerGroupwithMedianPrice.png) 
   

   2.9.7 Counts and Median Prices by PaintColor
   
   ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PaintColorwithMedianPrice.png) 
   


# Modeling

Pre-Modelling Work
  3.1 Spliting Data (80% of Train Data, 20% as Test Data)

  3.2 Impute Missing Values for Condition_Numeric and Cylinder_Numeric using Their respective Median Value. 

  3.4 Apply Log Transformation for Odometer

  3.5 Check Missing Value Again

  3.6 Log target variables for both train and test dataset because privous analysis of logged price are more normally distributed.

Modelling Techniques:

Using GridSearch to Search the Best Model and Try both price and logged price as the Target varible. 

1) Linear Regression with Polynomial
![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/b9aba626-0ba9-449f-a472-35d77f43ea84)


Best Polynomial Degree: 4
Best Mean Squared Error: 28490846.06812954

![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/4a495b02-3e6a-4d3e-ad3d-716c70a7f4df) 


Logged Target Variable
![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/34b5fb11-ccf2-457f-87ae-66382596220e) 


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/5c54543c-210c-45aa-9b64-e8738a10a899) 


R-squared for Training Data: 0.7823
R-squared for Testing Data: 0.7805

2) Ridge
![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/f9b503f5-56ee-4060-a506-a5a34bead505)


MAE: Training= 3339.4714, Test= 3339.4714 
MSE: Training= 34936293.0479, Test= 34570674.9742 
Optimal alpha: 8.286 

![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/b5832905-3602-4369-946e-61b8bb0987fb) 


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/a4693e10-b183-4fe7-ac77-34a6491188de) 


R-squared for Training Data: 0.7670 
R-squared for Testing Data: 0.7646 


4) Ridge with Polynomial
![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/9b859b04-c2ef-4209-b582-d1a4d473c7e3)


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/fca90dc1-0a33-451a-83dd-9f742f70b340) 


Best Alpha: 0.00042919342601287783
Best Polynomial Degree: 2
Training MAE: 4343.966853167321
Training MSE: 34043273.72143958
Test MAE: 4325.153891514682
Test MSE: 33782508.83641666


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/99290015-8020-4b1c-88af-ffd94e37c58c) 


Best Alpha: 0.49417133613238384
Training MAE: 0.23050398477538958
Training MSE: 0.09573746155009595
Test MAE: 0.2321125678283298
Test MSE: 0.09641483333824302

Logged Price Targeted Varibles
R-squared for Training Data: 0.8145
R-squared for Testing Data: 0.8128

Both Simple and Folded Validation Techniques are Used. 



Evaluation

Logged Target Varibles Moedl Alreays Performance better than non-logged price varibales.

Visual Plots: Residuals QQ Plots and Actual and Pedicted Plots
Statistic Measures: MSE and R2 
and Residuals and Actual and Predicted Plots as I am more interested in penalizing large errors in my model in order for my metric to reflect the true accuracy of my model. For this search I tried using a logarithmic and non-logarithmic target variable and obtained the following results:

But I do have hesitations on if I have overfitting the model.



My best model is:
Ridge with Polynomial with Logged Price Target Varibles. 


Understand the coefficent, and importance Feature analysis 

![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/1cb9bcbe-7e66-4ed3-af4e-c53d5c988182) 


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/e1b389ca-fe33-4b42-8aba-cb359937fbcf) 


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/1aefdce5-67ac-4760-ad5d-7dca60659597) 


In the search for weights for each of the characteristics I found that the year, model, odometer, transmission and cylinders of the vehicle have a very large influence on the prediction of the values, while the color, size and condition are not so decisive when calculating the price of the vehicles. In addition, we can see that the coefficients of a model with one of the best scores (Ridge with Polynomial) have marked extremes where the year and model and the combination of year-odometer and year-cylinders predominate, giving us an indication of the weight that these characteristics have at the time of predicting the price.

