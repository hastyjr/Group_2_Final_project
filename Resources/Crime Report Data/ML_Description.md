# Description of Machine Learning Model for Austin Crime Data

## Description of preliminary data preprocessing:

Prior to loading in the data into our database, incidents with any null values were dropped. After the data was imported for the machine learning models, any unnecessary or redundant columns were dropped and categorical variables were encoded.

## Description of preliminary feature engineering and preliminary feature selection, including decision-making process:

We initially used sklearn’s OneHotEncoder on all categorical features ,which resulted in a data frame with approximately 7,000 columns. To reduce this number we converted features indicating a date to a datetime data type and then broke up the full dates into days, months, and years. We then used sklearn’s LabelEncoder to encode features with more than 20 unique values, and mapped the encoded values to their labels for future references. The remaining categorical variables were encoded using sklearn’s OneHotEncoder. The final data frame contains 66 features.

![Encoding Categorical Variables](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Encode_Categorical_Features.png)

The dataset was then split into the features and the target array. The feature chosen to be the target variable was the “Family Violence_Y” variable, this variable indicates whether an incident was classified as being family violence (1) or not (0).

## Description of how data was split into training and testing sets:

We split the features and target arrays into random training and testing subsets with sklearn.model_selection’s train_test_split() method. By default, the training set contains 75% of the data, and the testing set contains 25%. After this step the datasets were scaled before being used in the machine learning models.

![Splitting the dataset](https://github.com/hastyjr/Group_2_Final_project/blob/mschimmy_B2/Resources/Images/Train_test_split.png)

## Explanation of model choice, including limitations and benefits:

For our analysis we are using three different machine learning models: logistic regression, random forest classifier, and neural network. Supervised machine learning models were selected as the input data contained the desired target variable and is in a tabular format. Logistic regression and random forest classifier models were chosen as the output of the models should predict a discrete outcome. The performance of the two models is evaluated using sklearn.metrics accuracy_score, confusion_matrix, and classification_report. The performance of the supervised machine learning models were compared against that of a TensorFlow neural network model.
- The logistic regression model had an accuracy score of 96.6%, but a precision, recall, and f1-score of 0.00 for predicting family violence incidents. This is most likely attributed to some class imbalance in the training and testing sets and will be addressed in future versions of the model.
- The random forest classifier model had an accuracy score of 98.7%, and a precision of 0.88, recall of 0.72, and f1-score of 0.80 for predicting family violence incidents. The random forest classifier was also used to calculate and rank feature importance, and it was found that time that the incident occurred and the UCR Category 220 had the highest weight when determining if an indecent will be family violence or not.
- The deep learning neural network utilizes 2 hidden layers and an output layer, and was trained on 100 epochs. The hidden layers use the relu activation function, the output layer uses the sigmoid function, and the loss function is binary_crossentropy and uses the Adam optimizer. The accuracy of the neural network model was 96.6% with a loss of 25.2%.
