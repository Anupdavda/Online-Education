# Online Education Enrollement Estimator: Project Overview 

* Created a project to predict future online education enrollement rate to based on student's feedback.
* Engineered features to convert Categorical values to Numerical Values.
* Performed  Principal Component Analysis (PCA) to reduce the dimensionality of the features.
* Compared Recall Score to evaluate baseline and reduced dimension model 
* Optimized KNN, Logistic Regression, SVM, and Random Forest Regressors using GridsearchCV to reach the best model. 


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

![alt text](https://github.com/Anupdavda/Online-Education/blob/master/picture1.jpg "Histogram of features")
![alt text](https://github.com/Anupdavda/Online-Education/blob/master/picture2.jpg "Histogram of features")
![alt text](https://github.com/Anupdavda/Online-Education/blob/master/picture3.jpg "Box Plot Showing Outliers")
![alt text](https://github.com/Anupdavda/Online-Education/blob/master/download.png "Correlation")

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried four different models and evaluated them using Root Mean Squared Error. I chose RMSE because makes predictions that are closest to the actual values from the dataset.

I tried three different models:
*	**Logistic Regression**
    * random_state = 3
*	**k-NN** 
    * n_neighbors = 3
         * Number of neighbors to use
*	**Random Forest** 
    * max_depth=3
         * The maximum depth of a tree
    * max_features = 22
         * The number of features to consider when finding the optimal split          
    * n_estimators = 100
         * The number of trees in the forest
    * random_state=0
      
*	**SVM** 
    * kernel = rbf
         * Radial Basis Function (RBF) kernel
    * gamma ='auto'
         * Uses 1 / n_features
    * probability = True
         * Enable probability estimates

## Model performance
The Random Forest model far outperformed the other approaches on the test and train sets. 
*	**Random Forest** : RSME = 0.465
*	**Linear Regression**: RSME = 0.454
*	**k-NN**: RSME = 0.572
*	**SVM**: RSME = 0.508

## Results and Discussions



