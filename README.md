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

## ✔️ Machine Learning Model

Two machine learning models will be created to find patterns in Austin crime data and make predictions of future criminal activity. Each model will be instantiated, trained using a percentage of the crime dataset, evaluated for accuracy, recall, and precison and then optimized before model deployment. Some machine learning models considered include the following:

- Logistic Regression Model to determine the input variable's probability of belonging to one of two groups
- Random Forest Model uses decisions trees and their combined output to make a classification or regression decision and can rank the performance of features

We hope to use machine learning models to accurately predict if a crime would be classified as Family Violence or not.


![Machine Learning Model Mockup](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy/Resources/Images/machine_learning_flowchart.png)
<sub>Machine Learning Model Mockup</sub>
