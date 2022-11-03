# Online Education Enrollement Estimator: Project Overview 

* Created a project to predict future online education enrollement rate to based on student's feedback.
* Engineered features to convert Categorical values to Numerical Values.
* Performed  Principal Component Analysis (PCA) to reduce the dimensionality of the features.
* Compared Recall Score to evaluate baseline and reduced dimension model 
* Optimized KNN, Decision Tree, and Random Forest Regressors using GridsearchCV to reach the best model. 


## Code and Resources Used 
**Python Version:** 3.9.12 
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn

The online education system review is a structured data set with 1033 observations and 23 variables.
Variables of the dataset are: 
* Gender - Female, Male
* Home Location - Urban, Rural
* Level of Education - Post Graduate, School, Undergraduate
* Age - Years
* Number of Subjects - 1 to 20
* Device type used to attend classes - Laptop, Desktop, Mobile
* Economic status - Rich, Middle Class, Poor
* Family size - 1 to 10
* Internet facility in your locality - Number scale (Very Bad to Very Good)
* Are you involved in any sports? - Yes, No
* Do elderly people monitor you? - Yes, No
* Study time - Hours
* Sleep time - Hours
* Average marks scored before the pandemic in a traditional classroom - range
* Your interaction in online mode - Number scale (Very Bad to Very Good)
* Clearing doubts with faculties in online mode - Number scale (Very Bad to Very Good)
* Interested in? - Practical, Theory, Both
* Time spent on social media - Hours
* Interested in Gaming? - Yes, No
* Have a separate room for studying? - Yes, No
* Engaged in group studies? - Yes, No
* Performance in online - Number scale (Very Bad to Very Good)
* Your level of satisfaction in Online Education - Average, Bad, Good


## Data Cleaning
I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:
 
*Performance in online would contain Very Bad to Very Good and Level of satisfaction in Online Education would contain Average, Bad and Good description. Changed the value of Very Bad to 0, Average to 1 and Very Good to 2 and converted Gender value to Binary values. Same steps were used to change categorical values to Nominal.
*	Removed Outliers from the data

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/salary_by_job_title.PNG "Salary by Position")
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/positions_by_state.png "Job Opportunities by State")
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/correlation_visual.png "Correlations")

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I tried three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : MAE = 11.22
*	**Linear Regression**: MAE = 18.86
*	**Ridge Regression**: MAE = 19.67

## Productionization 
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary. 


