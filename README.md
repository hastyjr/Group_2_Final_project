# :cop: Austin Crime Data Final Project

## Contributors

### Group Members / Roles

- 🔵 Laura Brown, Database Manager
- 🔺 Madison Schimmel, Machine Learning Lead
- 🟧 Joana Hasty, Github Repository Manager
- ❎ Jacob Sandoval, Technology Manager

## ✔️ Communication Protocols

Our group utilized Slack to communicate with each other and a shared Google doc to consolidate ideas and outline steps of the analysis. We met twice a week to go over our progress, discuss and resolve any questions, and plan different stages of the project.

---

# Project Overview

## :heavy_check_mark: Reasoning for Project

We chose this topic because we are all from Austin and we wanted to learn more about the city we live in. In doing so, we wanted to learn more about the crime data in Austin and how we can use data from previous years to predict the propensity of crime in the future. Our team are true believers in the fact that in order to prevent crime, we need to be able to predict crime. We believe this project will help us to better understand the crime data in Austin and how we can use it to predict crime in the future.

## :heavy_check_mark: Predictions we hope to answer with the data

We hope to answer the following questions with our data predictions:

- What type of crime is most likely to occur in Austin?
- What time of day is most likely to have a crime occur?
- What day of the week is most likely to have a crime occur?
- What month of the year is most likely to have a crime occur?
- What is the most likely location for a crime to occur?

## :heavy_check_mark: Data Source

The data source we chose is the Austin Crime Data from 2017-2022. This data set for this timeframe contains 200,000+ rows of data and 27 columns. This dataset contains a record of incidents where the Austin Police Department responded to calls for police service where a report was written. The data set contains information about the type of crime, the date and time of the crime, the location of the crime, and the address of the crime to name some of the columns.  

Initial data source: <https://data.austintexas.gov/Public-Safety/Crime-Reports/fdj4-gpfu>

## :heavy_check_mark: Database

The database is comprised of 1 `crime` table. The `crime` table contains 27 columns and 200,000+ rows of data. The data was loaded in from the CSV file using Pandas. It was also cleaned and transformed using Pandas. The data was then loaded into the database and queried using SQLAlchemy. Once loaded into the database, it was then hosted locally on Postgres.

A description of our data exploration and analysis phase of our project can be found [here](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy/Data%20Exploration.pdf).

## ✔️ Machine Learning Model

> :bulb: Purpose: To create a machine learning model that can predict family violence incidents in Austin and help us determine if the Covid-19 pandemic affected the rate of family violence incidents in Austin

### Phase One: Data Exploration and Mockup

![Machine Learning Model Mockup](https://github.com/hastyjr/Group_2_Final_project/blob/main/Resources/Images/machine_learning_flowchart.png)

<sub>Machine Learning Model Mockup</sub>

In this phase, we determined we would use three machine learning models to find patterns in crime reports of family violence incidents in Austin. Three simple models were created:

- A logistic regression model
- A random forest model
- A deep-learning neural network

In this phase, the preliminary Austin crime data was imported, cleaned, and preprocessed for the machine learning models. An overview of the data preprocessing, feature engineering, and explanation of model choices can be found [here](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Crime%20Report%20Data/ML_Description.md).

In future stages, each model will be evaluated and a single model will be chosen to make predictions on the Austin crime dataset.

### Phase Two: Data Analysis

In this phase of the project, the three models were trained and tested using the preprocessed and split Austin crime datasets. Each model's performance was evaluated using sklearn's accuracy_score, confusion_matrix, and classification_report. The following is an overview of each model's performance:

![Logistic Regression Model Evaluation](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Logistic_Regression_Evaluation.png)

<sub>Logistic Regression Model Evaluation</sub>

- The logistic regression model had an accuracy score of 96.6%, but a precision, recall, and F1-score of 0.00 for predicting family violence incidents. This is most likely attributed to some class imbalance in the training and testing sets and will be addressed in future versions of the model.

![Random Forest Classifier Evaluation](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Random_Forest_Classifier_Evaluation.png)

<sub>Random Forest Classifier Evaluation</sub>

- The random forest classifier model had an accuracy score of 98.7%, a precision of 0.88, a recall of 0.72, and an F1-score of 0.80 for predicting family violence incidents. The random forest classifier was also used to calculate and rank feature importance, and it was found that the time that the incident occurred and the UCR Category 220 had the highest weight when determining if an indecent will be family violence or not.

![Deep Learning Neural Network Evaluation](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Neural_Network_Evaluation.png)

<sub>Deep Learning Neural Network Evaluation</sub>

- The deep learning neural network utilizes 2 hidden layers and an output layer and was trained on 100 epochs. The hidden layers use the relu activation function, the output layer uses the sigmoid function, and the loss function is binary_crossentropy and uses the Adam optimizer. The accuracy of the neural network model was 96.6% with a loss of 25.2%.

### Phase Three: Model Optimization

This phase of the project addresses the class imbalance discovered in the previous phase. Each model was resampled using one of five resampling techniques:

- Random Oversampler
- SMOTE
- Random Undersampler
- Cluster Centroids
- SMOTEENN

The performance of each resampling method on each model can be found [here](https://github.com/hastyjr/Group_2_Final_project/blob/main/Resources/Resampling_Evaluations.xlsx)

After some deliberation, we chose to use the Random Forest Classifier as our final model because it had the most stable evaluation metrics and the highest F1-score. We also wanted to use the Random Forest Classifiers feature importances method to rank features and determine any relationship between features and the target variable.

### Phase Four: Model Implementation and Results

Our final machine learning model uses a Random Forest Classifier to predict incidents of family violence in Austin. The model takes in data from our pgAdmin PostgreSQL server, preprocesses and encodes the data, splits the data into features and target arrays, addresses any class imbalance with SMOTEENN, and scales the features array. The model was trained and tested on the fully preprocessed dataset and produced the following performance metrics:

![Final Model Performance](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Final_Model_Evaluation.png)

Using the Random Forest Classifier to rank the feature importances, it was found that the UCR Category 220 (burglary) and the incident occurred time had the most weight when predicting a family violence incident.

The full model code can be found [here](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Final_Project_Machine_Learning_Model.ipynb).

Our group then decided to use the same dataset and model structure to determine if family violence incidents post-2020 followed the same trends demonstrated in the previous two years. For this implementation, we split the cleaned and preprocessed dataset into incidents that occurred before 2020 and after 2020, and then addressed the same class imbalance and scaled the pre-Covid datasets.

![Covid Time Split](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Covid_Time_Split.png)

The Random Forest Classifier model was then trained and tested using the pre-Covid data and the model's performance metrics are below.

![Pre-Covid Model Performance](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Pre_Covid_Evaluation.png)

The pre-covid model was then used to predict incidents of family violence in Austin and the model's predictions were compared with the actual post-Covid data. The performance metrics are below.

![Post-Covid Model Performance](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Post_Covid_Evaluation.png)

The full model code can be found [here](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Covid_Machine_Learning_Model.ipynb)

### Suggestions for future model development and application:

- Use the Random Forest Classifier feature importances to determine which features to remove from the dataset. This could potentially improve the model's performance.
- Use the final machine learning model with future Austin crime datasets to determine if Austin's family violence incidents follow the same trend.
