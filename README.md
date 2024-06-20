# AI-Clowns
This is just a guide; for detailed explanation of all the files, please proceed with the report.<br>
NOTE- Do not skip the usage part. 

## Table of Contents
- [Project Overview]
- [Data Preprocessing]
  - [Dropping Unnecessary Columns]
  - [Applying Transformations]
- [Model Training]
  - [Hyperparameter Tuning with GridSearchCV]
- [Model Saving and Loading]
- [Making Predictions]
- [Usage]
- [Requirements]

## Project Overview
Prediction of sea surface temperature given air temperature,humidity,zonal winds,meridonial winds,lat,long and date

## Data Preprocessing
Handled the Null values of certain features like air temp, zon winds etc using spline interpolation while humidity(a column with many null values, almost 1/3) was imputed using xgboost. 

### Dropping Unnecessary Columns
The sea surface temperature does not depend on day

### Applying transformations
Yeo jonshon trasformer was applied to certain features for obtaining a nearly Gaussian KDE, while others were just simply scaled using Standard Scaler

## Model Training
Out of the many models we tested like xgboost, ARIMA, LSTM, Random Forest Regressor etc, xgboost and Random forest regressor turned to be the best and we adopted XGB with some hyperpatameter tuning

### Hyperparameter Tuning
Grid search CV was used for hyperparameter tuning of the XGB and it gave test results with approximately 96 percent accuracuy 

## Model saving and loading
After training your model, you can save it using the 'pickle' module in Python.<br> 
This allows you to persist the model for later use without having to retrain it.

## Making predictions
Using the pickle files, we predict the sea surface temperatures of the two datasets 'evalutation.csv' and '1997_1998.csv'

## Usage

Follow the files for proper understanding of the workflow and look into the comments and observations<br>
The output i.e, the predictions for the required 'evaluation.csv' and '1997_1998.csv' is in <b>CHRONOLOGICAL ORDER</b> i.e, sortedin accordance with the time column(day , month, year)<br>
These predictions are saved as csv files and are named as 'prediction_1997_1998.csv' and 'prediction_evaluation.csv'

## Requirements

You need to import the following modules in python :<br>
pandas<br>
numpy<br>
sklearn<br>
seaborn<br>
tensorflow<br>
matplotlib<br>
pickle<br>
