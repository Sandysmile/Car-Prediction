# What Drive the Price of a Car?

Introduction 

In the project, I analyzed a dataset comprising 3 million used cars sourced from Kaggle. 
Throughout the project, I employed the industry-standard CRISP-DM process (see below) for machine learning and data mining. 

![CRISP Model](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/CRISP%20Model.png)


DATA: Refer to the vehicles.zip file available in the repository 

Outline: Project Summary available in the repository 
https://github.com/Sandysmile/Car-Prediction/blob/main/Project%20Outline.pdf 

Detailed Analysis: Please refer to the Jupyter Notebook provided link below 

https://github.com/Sandysmile/Car-Prediction/blob/main/Car%20Price%20Prediction%20Application%20Project.ipynb 

Panda Profiling Analysis: 
https://github.com/Sandysmile/Car-Prediction/blob/main/output.html 


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
   


# Modeling/Evaluation

Pre-Modelling Work
  3.1 Spliting Data (80% of Train Data, 20% as Test Data)

  3.2 Impute Missing Values for Condition_Numeric and Cylinder_Numeric using Their respective Median Value. 

  3.4 Apply Log Transformation for Odometer

  3.5 Check Missing Value Again

  3.6 Log target variables for both train and test dataset because privous analysis of logged price are more normally distributed.

Modelling Techniques:

Using GridSearch to Search the Best Model and Try both price and logged price as the Target varible. 
Validation Methods: K-fold and holdout methods

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

3) Ridge with Polynomial
   
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


# Evaluation Summary

1. Logged Target Varibles Moedl Alreays Performance better than non-logged price varibales.
2. Visual Plots: Residuals QQ Plots and Actual and Pedicted Plots
3. Statistic Measures: MSE and R2
4. My best model so far is: Ridge with Polynomial with Logged Price Target Varibles. 

Howver, I do have a little suspiction that i might overfit the model due to large quantity of null valuable removel and feature, especially model feature removal. 


# Model Coefficents and Feature Importance

![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/1cb9bcbe-7e66-4ed3-af4e-c53d5c988182) 


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/e1b389ca-fe33-4b42-8aba-cb359937fbcf) 


![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/1aefdce5-67ac-4760-ad5d-7dca60659597) 


## Business Applications

I found that manufactuer, year, odometer, fuel, drive of  the vehicle largely decide a car's price, while the color, # of cylinders and condition are irrelevent.
Specifically, the analysis have the following business applicaiton

1. Model Performance: Polynomial features significantly enhance model accuracy. Log transformations improve data distribution for more reliable predictions.
   Non-log
   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/e4257d5c-5b11-40e3-a182-c65c9ed914ad)
  	
   Log
  ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/0ef11468-0c70-416f-b63f-72839a6c41f8)
  	

2. Key Influencers: Manufacturer, year, vehicle type, odometer, and drive are pivotal in pricing.
   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/000a9faa-9db0-43fd-8874-e11d8222f976)
  	
   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/6f372231-d930-472a-9b68-82a5e9d5fc05) 

   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/309e17a5-3ba3-48c2-900d-7972bd427fe1) 
   
   
3. Inventory Trends: Trucks and pickups maintain premium market positioning. while Toyota and sedon  
   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/a69b221e-462b-4020-a44b-bd9c337e9275)
  	
   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/413c55a5-f624-40cd-8792-a7901739006f)
  	
  	
  	
4. Consumer Preferences: High-end vehicles are favored over popular lower-end models.
   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/ab0ec3aa-b730-49e5-ac67-987e98537dbf)


5. Risk Management: Newer American vehicles with four-wheel drive are less risky. Japanese and Korean brands are preferred for their value retention in the secondary market.
   ![image](https://github.com/Sandysmile/Car-Prediction/assets/20648423/0f1d6b50-8325-443c-a6fa-cd365abd02fe) 
    
   Surprisingly, car conditions and the number of cylinders have shown to be insignificant factors in the dataset. Is it largely because the condition of the car positively correlates with its year and negatively with the odometer readings? Additionally, the 
   imputation of a significant portion of missing data (over 34%) for cylinders and car condition may explain their limited significance to some extent


# Next Step

1.	Data Collection and Cleaning: Reduced the dataset from 400,000 to less than 200,000 records by eliminating extensive missing values to enhance model performance.
2.	Feature Removal: This might cause the model overfitting issue. More business research could help. 
3.	Market Demand and Economic Factors: Plans to integrate market demand and economic data aim to refine valuations by including demand-supply dynamics.
4.	Computational Limitations: Limited computational resources curtailed extensive model testing; utilized Lasso and polynomial features.
5.	Feature Selection and Model Expansion: The initial categorization of cars into five price groups underperformed; future models will focus on granular feature selection and robust data sources to boost accuracy

