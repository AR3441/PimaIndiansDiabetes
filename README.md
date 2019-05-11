# Classifying Diabetes in Pima Indian Women

## Abstract

For this project, binary classification was performed using various machine learning models to predict if a person had diabetes. After the data was cleaned and scaled, features were created. A 75-25 test-train-split was done and Logistic Regressioin, Decision Tree, KNN, Random Forest, and XGBoost algorithms were used. The algorithms with the highest accuracies and F1 scores were Random Forest and XGBoost. 

## Data, Data Cleaning, and Transformations
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

After this, the data was transformed. First, Age and Pregnancies were changed into range bins and then dummy variables. The remaining continuous variables were transformed using a MinMax Scaler. 

## Resources 
[1] https://data.world/data-society/pima-indians-diabetes-database
