# Classifying Diabetes in Pima Indian Women

## Abstract

For this project, binary classification was performed using various machine learning models to predict if a person had diabetes. After the data was cleaned and scaled, features were created. A 75-25 test-train-split was done and Logistic Regressioin, Decision Tree, K Nearest Neighbors, Random Forest, and XGBoost algorithms were used. The algorithms with the highest accuracies and F1 scores were Random Forest and XGBoost. 

## The Data
The data was retrieved from Kaggle<sup>1</sup>. The dataset is originally from National Institude of Diabetes and Digestive and Kidney Diseases. The data looks specifically at attributes of women over the age of 21 that are of Pima Indian heritage. The original dataset includes the following columns:
- Glucose
- Blood Pressure
- BMI
- Diabetes Pedigree Function
- Insulin
- Number of Pregnancies
- Age
- Skin Thickness: Triceps Skinfold Thickness 
- Outcome

To begin cleaning the data, NaNs and zero values were removed from the Glucose, Blood Pressure and BMI columns by replacing the zeros with the mean of the values that weren't zero. This couldn't be done however for the Insulin and Skin Thickness column which had zeros for over half the total number of instances. These columns were removed from the dataset altogether. The remaining columns were then checked for outliers using an IQR boxplot. Since there weren't too many outliers, they were kept in the dataset. 

After this, the data was transformed. First, Age and Pregnancies were changed into range bins and then dummy variables. The remaining continuous variables were transformed using a MinMax Scaler. After this, some interaction variables were created using the continuous variables. In total there were 20 predictor variables. 


Finally, the class imbalance was looked at:

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/ClassImbalance.png)

There were 500 instances of the majority class, and 268 instances of the minority class. The minority class was upsampled to match the majority class using scikit learn's resample function. 

## Model Testing + Results
To begin testing different models, the data was divided into testing and training sets with a ratio of 75-25. The first model that was used was logistic regression. This was used in conjunction with GridSearch to find the best hyperparameters. This model performed fairly well with a Training F1 score of 0.774 and a testing F1 score of 0.757. A confusion matrix representing how the model performed can be seen below:

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/Logistic%20Regressioin%20Confusion%20Matrix.png)

### Decision Tree 
The next model used was Decision Tree. It was also used with GridSearch to find the best hyperparameters.
The metrics for this model as well as a confusion matrix can be seen below: 

Training F1 Score: 0.778
Testing F1 Score: 0.735                                                                                                                 ![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/Decision%20Tree%20Confusion%20Matrix.png)

This model performed fairly poorly on thet testnig set, and in terms of the number of false negatives. This is important because you woulld not want your model to miss patients that actually have diabetes. 

### Random Forest
The next model used was Random Forest. This was also used with GridSearch and performed much better. It achieved the following scores:

Test Accuracy Score: 0.792

Testing F1 Score: 0.818

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/Random%20Forest%20Confusion%20Matrix.png)

### K Nearest Neighbors

KNN was the next model and had the following metrics and confusion matrix: 

Test Accuracy Score: 0.764
               
Test F1 Score: 0.790

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/KNN%20Confusion%20Matrix.png)

### XGBoost

XGBoost was the final model to be used and performed unsurprisingly even without using GridSearch. These were the metrics for this model:

Test Accuracy: 0.796

Test F1 Score: 0.819

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/KNN%20Confusion%20Matrix.png)

## Feature Importance

Now that all the models have been tested, the feature importance was looked at. This is a chart visualizing feature importances based on the logistic regression model:

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/logistic%20regression%20feature%20importance.png)

Looking at this chart, Glucose and an interaction between Glucose and BMI are the most important features. To see just how important Glucose was, it was dropped and the logistic regression model was run again. It still performed surprisingly well with a Testing F1 Score of 0.749. For this model, the most important feature was Diabetes Pedigree Function. After this, the model was run again with both of these features removed and the model still performed fairly well with an F1 score of 0.68. 

## Conclusion
Different classification models were tested on a dataset with engineered features. They all performed decently with XGBoost and Random Forest performing the best. Future steps to improve accuracy scores would involve using XGBoost with cross validation or creating even better features. 

## Resources 
[1] https://data.world/data-society/pima-indians-diabetes-database
