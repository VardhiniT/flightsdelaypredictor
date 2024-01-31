# Flight Delay Prediction - T Giri Vardhini

### Introduction About the Data :

**The dataset** The goal is to predict `delay` of flight with given details about it (Regression Analysis).

There are 8 independent variables :

* `Temperature at departure` : Temperature (°C) at the departure airport is one of the weather factors affecting the flight schedules. 
* `Temperature at arrival` : Temperature (°C) at the departure airport is one of the weather factors affecting the flight schedules. 
* `Wind at departure` : The magnitude of wind (mph) at the departure is also one of the factor affecting the flight schedules.
*`Wind at arrival` : The magnitude of wind (mph) at the arrival is also one of the factor affecting the flight schedules.
* `Precipitation` : The effect of precipitation is categorised as either 0 (no effect) or 1, depending on the type and magnitude of precipitation.
* `Delay in departure` : The delay of aircraft (min) in its previous journey which may effect its immediate take-off.
* `Aircraft maintainance` : Unexpected mechanical issues that require immediate attention may lead to delay in its next journey. 
* `Air route traffic` : Air route congestion may implement delays to manage traffic flow, such as holding patterns or ground stops.

Target variable:
* `Delay in arrival`: The delay in arrival (min) is predicted taking into account the above factors.

Dataset Source Link :
[https://www.kaggle.com/competitions/playground-series-s3e8/data?select=train.csv](https://www.kaggle.com/competitions/playground-series-s3e8/data?select=train.csv)

### It is observed that the variables in the dataset are all numerical in nature (the downloaded dataset is thoroughly pre-processed before it is released). 

# AWS Deployment Link :

AWS Elastic Beanstalk link : [http://gemstonepriceutkarshgaikwad-env.eba-7zp3wapg.ap-south-1.elasticbeanstalk.com/](http://gemstonepriceutkarshgaikwad-env.eba-7zp3wapg.ap-south-1.elasticbeanstalk.com/)

# Screenshot of UI

![HomepageUI](./Screenshots/HomepageUI.jpg)

# YouTube Video Link

Link for YouTube Video : Click the below thumbnail to open 

[![https://youtu.be/Xvk5r0t_RQw](https://i.ytimg.com/vi/Xvk5r0t_RQw/hqdefault.jpg?sqp=-oaymwEcCNACELwBSFXyq4qpAw4IARUAAIhCGAFwAcABBg==&rs=AOn4CLBbp5SouquUm3Y3t-NYfOYsg4N4oQ)](https://youtu.be/Xvk5r0t_RQw)

# AWS API Link

API Link : [http://gemstonepriceutkarshgaikwad-env.eba-7zp3wapg.ap-south-1.elasticbeanstalk.com/predictAPI](http://gemstonepriceutkarshgaikwad-env.eba-7zp3wapg.ap-south-1.elasticbeanstalk.com/predictAPI)

# Postman Testing of API :

![API Prediction](./Screenshots/APIPrediction.jpg)

# Approach for the project 

1. Data Ingestion : 
    * In Data Ingestion phase the data is first read as csv. 
    * Then the data is split into training and testing and saved as csv file.

2. Data Transformation : 
    * In this phase a ColumnTransformer Pipeline is created.
    * for Numeric Variables first SimpleImputer is applied with strategy median , then Standard Scaling is performed on numeric data.
    * for Categorical Variables SimpleImputer is applied with most frequent strategy, then ordinal encoding performed , after this data is scaled with Standard Scaler.
    * This preprocessor is saved as pickle file.

3. Model Training : 
    * In this phase base model is tested . The best model found was catboost regressor.
    * After this hyperparameter tuning is performed on catboost and knn model.
    * A final VotingRegressor is created which will combine prediction of catboost, xgboost and knn models.
    * This model is saved as pickle file.

4. Prediction Pipeline : 
    * This pipeline converts given data into dataframe and has various functions to load pickle files and predict the final results in python.

5. Flask App creation : 
    * Flask app is created with User Interface to predict the gemstone prices inside a Web Application.

# Exploratory Data Analysis Notebook

Link : [EDA Notebook](./notebook/1_EDA_Gemstone_price.ipynb)

# Model Training Approach Notebook

Link : [Model Training Notebook](./notebook/2_Model_Training_Gemstone.ipynb)

# Model Interpretation with LIME 

Link : [LIME Interpretation](./notebook/3_Explainability_with_LIME.ipynb)
