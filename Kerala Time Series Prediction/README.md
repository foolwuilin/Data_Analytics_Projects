## [PRESS HERE FOR THE CODING](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/time-series-prediction-for-kerala-rainfall.ipynb)

# 1 Introduction
## 1.1 Summary
Kerala is a state of India. Wikipedia describes Kerala (n.d.) contributes massive pepper and natural rubber to the total national output. The agricultural sector, coconut, tea, coffee, cashew and spices are important in this region. Thus, well predicting the rainfall in Kerala would benefit the agriculture industry to make a better plan and possibly increase the output.

This analysis explores the data to see the current situation in Kerala. The next step will try to understand the difficulty of predicting the rainfall in this area and then choose a better method. The expected prediction accuracy should be at least higher than 60%; otherwise, it will cause a negative effect if the prediction is around or lower than 50% accuracy.

## 1.2 Analytics Tool and Dataset
This report uses Python as the analytics tool. The given dataset contains the monthly rainfall precipitation, annual precipitation, and the annual precipitation split into 4 different seasons, JF (Jan-Feb), MAM (Mar-May), JJAS (Jun-Sep), and OND (Oct-Dec), from 1901 to 2017. Total 117 rows and 19 columns as in the dataset.

# 2 Prepare
## 2.1 Analysis Plan
The analysis plan is to answer the questions.

1. What is the rainfall situation in Kerala?
2. Is any difficulty in predicting the rainfall?
3. What prediction method would help, and how accurate the prediction is?

## 2.2 Performance Metrics
This analysis will use the below metrics to evaluate whether the method is suitable for this rainfall prediction.

1. R-Squared - R-squared measures the proportion of the variance for a dependent variable explained by another independent variable or variables in a regression model (Fernondo, 2021).
2. Accuracy - An accuracy number tells how good the model is able to correctly predict data points out of all the data points (Deep AI, n.d.).
3. Confusion Matrix - Data School (2014) explains that a confusion matrix shows a table describing the performance of a classification model on a set of test data for which the true values are known.
4. MAE and RMSE - Root Mean Squared Error (RMSE)and Mean Absolute Error (MAE) are used for evaluating Regression Models. These metrics indicate the deviation from the actual values and how accurate the predictions are (Acharya, 2021). The lower errors, the better accuracy.

## 2.3 Method
The analysis follows the steps as below.

1. Review the data structure and clean it if it is necessary.
2. Proceeding Exploratory Data Analysis to review the rainfall situation.
3. Predict the rainfall by seasonal factors and then seek other methods to improve the prediction.
4. Use classification methods to predict and evaluate the performance.
5. Use regression models to predict and review the outputs.

# 3 Process
## 3.1 Exploratory Data Analysis
This section involves the preparation of the dataset, including data cleansing. Then, an EDA (Exploratory Data Analysis) will help understand the main characteristics of the dataset. Further analysis would be based on the findings from the EDA.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/msno.png)

After the review, there is no missing value in this dataset. Thus, Here will go forward to the EDA section.
