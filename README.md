# Data Analyst Salary Predictor Project

 ### Project Overview:
 
Write a summary of the project here.


## Code and Resources Used 
**Python Version:** 3.9  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, xgboost

_Inspiration for this project comes from Ken Jee's video on data scientist salaries. Here is the link to his YouTube Video: https://www.youtube.com/watch?v=MpF9HENQjDo. While my project is similar, this work uses a different data set on a different position and a substantially different algorithmic, EDA, and model framework._


## Data Cleaning
There was only a small amount of data cleaning necessary for this project. In particular, for part 1, there was missing data in the reject_code column of the dim_claims_df data frame. I chose to replace the missing data with 0 using the fillna method from pandas. I chose to use zero because no reject_code meant that your pharmacy claim got approved. 


## EDA


* Box plot detailing which sector paid a higher average salary. A detailed pivot table was also given in the salary_eda.ipynb file for more explicit numbers.  

![](avg_salary_sector.jpg )

* The following graph shows the average salaries of data analyst jobs whose job descriptions indicated a PhD as a preference. Not many jobs indicating this but when they do the salaries can be significantly higher. 

![](Avg_salary_sector_phd.jpg)

* Bar chart indicating the number of available jobs in reference to the company's headquarters. As we can see, New York lead the way in terms of the number of such jobs being offered.  

![](analyst_job_by_state.jpg)

* The following is a box plot indicating the average salaries for data analyst positions whose job descriptions indicate SQL as a desired skill. It is clear that not only do positions want SQL, but it also pays a higher salary to know the language. 

![](analyst_job_by_state.jpg)

## Model Building 

**Part 1**: 
First, I transformed the categorical variables into dummy variables using a one hot encoder. I also split the data into train and tests sets with a test size of 30%.   

I used a random forest classifier for the moodel and evaluated the model using the accuracy, precision, recall, and AUC metrics. I chose a random forest classifier because of the sparsity associated with the data as well as the primary binary nature of each feature. 

A GridSearchCV was performed on the random forest model where I analyzed the max_depth hyperparameter. The GridSearchCV returned that the random forest classifier with a max_depth hyperparameter equal to 5 performed more optimally on the precision metric. I consequentely used this model for the prediction. 

## Models Used: 
*	**Lasso Regression** – Baseline for the model
*	**Ridge Regression** – To see how data performed on another non ensemble model. 
*	**Elastic Net Regression** – To see how data performed on another non ensemble model. 
*	**XGBoost** – With the sparsity and binary nature of the data, I thought this would be a good choice. 

I ultimately opted with the XGBoost due to MAE performance as well as wanting to avoid overtraining. Hyperparameter tuning using the XGBoost built in feature also allowed me to get the best MAE on the validation data from all models. 

## Model performance

**Part 1**: 
Using cross validation, we got the following explicit scores. Since hyperparameter tuning was used (using GridSearchCV and XGBoost built in tuning) for all of our models, we also give the found parameters. 

Lasso Regression Score: 
*	MAE: 15.23
- Hyperparameters: alpha=0.01

Ridge Regression Score: 
*	MAE: 15.40
- Hyperparameters: 0.11 

Elastic Net Regression Score: 
*	MAE: 17.67
- Hyperparameters: alpha=0.01 and l1_ratio=0.01

XGBoost Score: 
*	MAE: 14.83
- Hyperparameters: max_depth=7, min_child_weight=7, eta= 0.1, subsample=1
