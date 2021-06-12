# Data Analyst Salary Predictor Project

 ### Project Overview:
 
Write a summary of the project here.  


## Code and Resources Used 
**Python Version:** 3.9  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn,    

## Data Cleaning
There was only a small amount of data cleaning necessary for this project. In particular, for part 1, there was missing data in the reject_code column of the dim_claims_df data frame. I chose to replace the missing data with 0 using the fillna method from pandas. I chose to use zero because no reject_code meant that your pharmacy claim got approved. 


## EDA

* Count plot showing the how many times a insurance provider approved or denied the pharmacy claim. The count plot also shows how many times (total) each drug was approved or denied a pharmacy claim. 

![](Avg_salary_sector_phd.jpg)

* Count plot visualization detailing each drug and the associated times that a reject code appeared with said drug. 

![](analyst_job_by_state.jpg)

* Count plot detailing the formulary for each insurance provider and the number of times each drug was approved or not. 

![](avg_salary_sector.jpg )



## Model Building 

**Part 1**: 
First, I transformed the categorical variables into dummy variables using a one hot encoder. I also split the data into train and tests sets with a test size of 30%.   

I used a random forest classifier for the moodel and evaluated the model using the accuracy, precision, recall, and AUC metrics. I chose a random forest classifier because of the sparsity associated with the data as well as the primary binary nature of each feature. 

A GridSearchCV was performed on the random forest model where I analyzed the max_depth hyperparameter. The GridSearchCV returned that the random forest classifier with a max_depth hyperparameter equal to 5 performed more optimally on the precision metric. I consequentely used this model for the prediction. 

## Models Used: 
*	**DecisionTreeClassifier** – Baseline for the model
*	**KNN** – To see how data performed on another non ensemble model. 
*	**Random Forest Classifier** – With the sparsity and binary nature of the data, I thought this would be a good choice. 

I ultimately opted with the RandomForestClassifier due to metric performance as well as wanting to avoid overtraining the decision tree classifier. As in part 1, a GridSearchCV was performed on the random forest model where I analyzed the max_depth parameter and n_estimators. The GridSearchCV provided a slightly better model with max_depth=5. I then used this model to make predictions. 

## Model performance

**Part 1**: 
The Random Forest Classifier far outperformed the other approaches when using baseline metrics as well as with cross validation. 

RandomForestClassifier Scores: 
*	accuracy = .935
*	precision = .900
*	recall =1
*	AUC=.922

Cross Validation Scores for the RandomForestClassifier model: 
*	mean accuracy = .94
*	mean precision = .900
*	mean recall =1

_Inspiration for this project comes from Ken Jee's video on data scientist salaries. Here is the link to his YouTube Video: https://www.youtube.com/watch?v=MpF9HENQjDo. While my project is similar, this work uses a different data set on a different position and a substantially different algorithmic, EDA, and model framework._
