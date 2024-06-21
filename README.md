# AI-Clowns
This is just a guide. Please proceed with the report for a detailed explanation of all the files. <br>
NOTE:- Do not skip the usage part.

## Table of Contents
- [Project Overview](#project-overview)
- [Data Preprocessing](#data-preprocessing)
  - [Handling Null Values](#handling-null-values)
  - [Dropping Unnecessary Columns](#dropping-unnecessary-columns)
  - [Applying Transformations](#applying-transformations)
- [Model Training](#model-training)
  - [Hyperparameter Tuning with GridSearchCV](#hyperparameter-tuning)
- [Model Saving and Loading](#model-saving-and-loading)
- [Making Predictions](#making-predictions)
- [Usage](#usage)
- [Requirements](#requirements)

## Project Overview
Prediction of sea surface temperature (SST) given the air temperature, humidity, zonal winds, meridional winds, latitude, longitude and the date.

## Data Preprocessing
### Handling null values
Handled the null values of certain features like air temp, zonal winds, etc., using spline interpolation while humidity (a column with many null values, almost 1/3) was imputed using xgboost. 

### Dropping Unnecessary Columns
The sea surface temperature does not depend on the day.

### Applying transformations
Yeo-Johnson transformer was applied to certain features to obtain a nearly Gaussian KDE, while others were just scaled using Standard Scaler.

## Model Training
Out of the many models we tested like xgboost, ARIMA, LSTM, Random Forest Regressor, etc., xgboost and from which Random Forest Regressor turned out to be the best, we adopted XGB with some hyperparameter tuning.

### Hyperparameter Tuning
Grid search CV was used for hyperparameter tuning of the XGB, and it gave test results with approximately 96 percent accuracy. 

## Model saving and loading
After training your model, you can save it using the 'pickle' module in Python.<br> 
This allows you to persist the model for later use without having to retrain it.

## Making predictions
Using the pickle files, we predict the sea surface temperatures of the two datasets 'evalutation.csv' and '1997_1998.csv'.

## Usage

Follow the files for proper understanding of the workflow and look into the comments and observations.<br>
The output, i.e., the predictions for the required 'evaluation.csv' and '1997_1998.csv', is in <b>CHRONOLOGICAL ORDER</b> i.e., sorted in accordance with the time column (day, month, year).<br>
These predictions are saved as CSV files and are named 'prediction_1997_1998.csv' and 'prediction_evaluation.csv'.<br>

While testing our predictions, please sort your dataframe. Code given below might be helpful<br>(Assuming df is your dataframe):<br>

```python
df['date'] = pd.to_datetime(df[['year', 'month', 'day']])
df = df.sort_values(by='date').reset_index(drop=True)
df.drop(columns=['date'], inplace=True)
df.head()
```
## Requirements

You need to import the following modules in Python:<br>
- pandas
- numpy
- sklearn
- seaborn
- tensorflow
- matplotlib
- pickle
