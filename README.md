# Classifying Diabetes in Pima Indian Women

## Abstract

For this project, binary classification was performed using various machine learning models to predict if a person had diabetes. After the data was cleaned and scaled, features were created. A 75-25 test-train-split was done and Logistic Regressioin, Decision Tree, KNN, Random Forest, and XGBoost algorithms were used. The algorithms with the highest accuracies and F1 scores were Random Forest and XGBoost. 

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

After this, the data was transformed. First, Age and Pregnancies were changed into range bins and then dummy variables. The remaining continuous variables were transformed using a MinMax Scaler. After this, some interaction variables were created using the continuous variables. 


Finally, the class imbalance was looked at:

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/ClassImbalance.png)

There were 500 instances of the majority class, and 268 instances of the minority class. The minority class was upsampled to match the majority class using scikit learn's resample function. 

## Model Testing + Results
To begin testing different models, the data was divided into testing and training sets with a ratio of 75-25. The first model that was used was logistic regression. This was used in conjunction with GridSearch to find the best hyperparameters. This model performed fairly well with a Training F1 score of 0.774 and a testing F1 score of 0.757. A confusion matrix representing how the model performed can be seen below:

![Graphs](https://github.com/AR3441/PimaIndiansDiabetes/blob/master/Graphs/Logistic%20Regressioin%20Confusion%20Matrix.png)



## Resources 
[1] https://data.world/data-society/pima-indians-diabetes-database
