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

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/seasons.jpg)

The average precipitation of JAAS (June to September) is tremendously higher than in other seasons. In contrast, the precipitation of January and February is quite low than others.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/months.jpg)

The box plot shows the precipitation in every month varies from year to year, and the difference can go a huge range regarding the dots alone the boxes.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/scatter.jpg)

The regression lines show there is a trend that the rainfall in JJAS (Jun-Sep) season slightly decrease. It also causes the trend of the annual precipitation to go down. However, the dots spread a wide range from the regression lines. It tells the same message as the insight from the previous box plot. The precipitation in different seasons varies from year to year.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/heatmap.png)

This heatmap shows the correlation coefficient of the monthly precipitation between months. It is clear there is no significant correlation between months. Only the correlation, 0.22, between February and March looks higher, but it is still too low. In general, the heatmap tells predicting monthly precipitation by correlation is not quite ideal.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/data_1.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/seasonal_1.png)

This line plot shows the rainfall in Kerala from 1998 to 2017. It seems the precipitation increases up and down periodically every year. It might be a piece of useful information for this analysis to predict the rainfall.

## 3.2 Exploratory Data Analysis Summary
The given dataset has 119 rows and 17 columns without missing data. Regarding the visualization, here are the insights below.

1. The JAAS Season has significant higher precipitation than other seasons.
2. The rainfall variance in the same month of different years spreads in a huge range.
3. Although the regression line shows the rainfall in the JJAS season slightly decrease, the scatter plot demonstrates the difficulty of predicting by regression due to the variance.
4. The heatmap tells that predicting by the correlation between months is not quite ideal.
5. This line plot shows a periodic pattern that the rainfall increases up and down in certain months.

Due to viewpoint 5, it might be viable to predict by seasonal factors. Thus, the next section will start prediction analysis in regards to the insights from the EDA.

# 4 Analyze
## 4.1 Seasonal Factor Analysis
If the precipitation can be affected by a seasonal factor, it is possible to predict by using the factor. The step would be as follows.

1. Get the moving average numbers
2. Calculate the seasonal factors for every month
3. Get the average seasonal factors to fit back into the months
4. Use the average factors to get deseasonalized numbers
5. Predict a number by using the regression line generated by the deseasonalized numbers
6. Seasonalize the prediction generated by the deseasonalized numbers to get final results

These are the steps to predict by seasonal factors. However, the viability depends on how good the deseasonalized model is. This analysis will evaluate the model by the R-Squared number of the regression generated by deseasonalized numbers.

## 4.1.1 Optimize The Model by All Data

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/data_2.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/seasonal_2.png)

The line plot demonstrates the deseasonalized rainfall has many outliners, although the moving average numbers go smoothly. This situation would cause a problem to make a further prediction. Thus, in order to evaluate whether this seasonal factor analysis is viable. Checking the R-squared number of the regression is needed.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/description_1.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/description_2.jpg)

Comparing the R-squared number of the original model to the deseasonalized model, the improvement only increases from 0.001 to 0.006. The optimized regression can only explain 0.6% of variables, which is very bad. Thus, the next step is to try another way to optimize this prediction model.

## 4.1.2 Optimize The Model by 4 Seasons

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/data_3.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/seasonal_3.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/description_3.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/description_4.jpg)

The optimization is still not able to improve the prediction model, even though we choose to predict a seasonal rainfall instead of monthly rainfall. The R-squared number only increases from 0.001 to 0.015. It demonstrates predicting the rainfall by seasonal factors completely fails. As a result, this analysis will change to predict by machine learning algorithms.

## 4.2 Machine Learning Method
Since the previous prediction method based on seasonal factors was not quite ideal, this section will use machine learning methods to build a prediction model. This analysis will compare the predictions from classification and regression models.

### 4.2.1 Predict by Classifiers
The steps of classification would be as below.

1. Prepare a dataframe with needed information for training the models
2. Label the rainfall into 4 levels of ranges
3. Fit different models with GridSearch and see the accuracy
4. Review the accuracy scores and confusion matrix to ensure whether the results are acceptable

Ideally, this analysis chooses the below columns to build up the data for training the machine learning models. Moreover, since the moving average method made some missing variables in 1901, the dataframe drops the rows.

- Year
- Month
- Precipitation (mms)
- Moving average number
- Annual rainfall from the last year
- JF (Jan-Feb) season rainfall from the last year
- MAM (Mar-May) season rainfall from the last year
- JJAS (Jun-Sep) season rainfall from the last year
- OND (Oct-Dec) season rainfall from the last year

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/data_4.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/description_5.jpg)

Looking into these classification reports, the precision scores of 2 models, LGBM and XGBoost, for 4 clusters are all above 50%. It seems these two models are better than the others. However, further evaluation is still needed. Therefore, this analysis will compare the model accuracy of each model.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/accuracy.jpg)

Despite LGBM and XGBoost, this bar chart shows the accuracy of GaussianNB and Random Forest look acceptable. Still, LGBM has the highest accuracy score, 70.98%. It could be the model for this Kerala rainfall prediction. In the next part, this analysis will review the confusion matrix and select the best solution.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/confusion.png)

In regards to the rainfall prediction, the worst situation is that the forecast says the weather is mild, but actually, it causes a natural disaster, such as droughts or floods. Thus, this analysis would like to evaluate the models by these false predictions. One is that the model clusters the rainfall into level 2, level 3, and level 4, but the actual rainfall is level 1, which is a drought month. The other one is that the model clusters the rainfall into level 1, level 2, and level 3, but the actual rainfall is level 4, which floods would happen in the month. Then, this analysis will compare the proportion of these false predictions to ensure whether LGBM is still the best solution.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ff.jpg)

The bar chart demonstrates LGBM still has the lowest possibility to mispredict natural disasters. It is an inspiring outcome that LGBM should be the solution for this calssification analysis.

### 4.2.2 Predict by Regression Models
The steps of the regression analysis would be as below.

1. Delay the precipitation in order to generate materials for machine learning models to predict.
2. Fit regression models and plot the predictions
3. Review the correlations of the elements used for the models to see whether there is overfitting
4. Evaluate the prediction by MAE and RMSE

First, delay the precipitation 12 times for regression models to predict because we already know the rainfall has a yearly repeat pattern from the previous section. Also, adding year, month, and season columns would potentially help the regression model predict.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/data_5.jpg)

- LinearRegression

The red spots indicate outliners. The prediction has many outliners since the weather is not stable in Kerala. It is difficult to predict the rainfall in this area. This analysis will evaluate the performance of the prediction by MAE and RMSE in the later section. Here, we are looking at the coefficients of every element fit into the prediction models. In this LinearRegression, the season and month factors have higher coefficients, which means the models may slightly overfit by using these two factors. The idea coefficient model should have a smoothly decreasing slope.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_1.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_2.png)

- Ridge

The slope of the coeeficients smoothly goes down in this Rifge model. It seems better than the LinearRegresson model. However, this analysis will keep comparing different models.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_3.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_4.png)

- Lasso

It is obvious that lag_12, season, and month factors have higher coefficients in this Lasso model. It still says there is slightly overfitting comparing to the Ridge model.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_5.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_6.png)

- XGBRegressor

As for XGBRegressor, it does not provide coefficients because it is a tree learner model. Here, we only review the line plot to compare the prediction and the actual rainfall.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_7.png)

- ElasticNet

The below charts shows lag_12 has a high coefficient. It demonstrates ElasticNet is the model that overfits the most in these 5 regression models so far.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_8.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/ts_9.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/description_6.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Kerala%20Time%20Series%20Prediction/image/rmse.jpg)

Lastly, these 5 regression models have similar results with closed MAE and RMSE. It seems the XGBRegressor has the lowest MAE and RMSE. However, as mentioned in the previous section, the coefficients of the elements are missing. Thus, it is unknown whether the XGBRegressor overfits or not.

Despite XGBregressor, the Ridge could be the second choice with lower MAE and RMSE. Also, in the previous section, the coefficients in the Ridge model demonstrate a smoothly decreasing slope. Therefore, this analysis would consider Ridge as an ideal regression model for predicting the rainfall in Kerala.

# 5 Conlusion
This analysis aims to select a prediction model for rainfall forecasting. Since Kerala contributes a high amount of agricultural products in India, maximizing the outputs and minimizing the risks of confronting natural disasters are the concern of this analysis.

In general, if the situation has regular seasonal factors, e.g. sales of a retailer, predicting by seasonal factors would get promising results. However, after trying the seasonal factor method, the outcome looks bad due to too many outliers. The R-squared scores are too low to predict the rainfall accurately. Thus, the next step is to use a machine learning method instead.

First of all, this analysis tested 6 classifications as below.

1. GaussianNB
2. Random Forest
3. Logistic Regression
4. Decision Tree
5. LGBM
6. XGBoost

As for a prediction, the worst situation is that the model mispredicts natural disasters, which means selecting a prediction model should consider the false prediction of droughts and floods. After the analysis, LGBM is the ideal model for the prediction in terms of classification. The prediction accuracy is 70.98%, and the false prediction of droughts and floods is the lowest, 8% and 4%.

However, since rainfall is continuously changing records, a time series analysis by using regression models could be the method to get a more accurate prediction. Thus, this analysis uses the below machine learning algorithms to seek a better solution then.

1. LinearRegression
2. Ridge
3. Lasso
4. XGBRegressor
5. ElasticNet

After the evaluation, XGBRegressor contributes a higher correlation between the prediction and the actual rainfall. It seems the XGBRegressor is an ideal regression model to predict. On the flip side, XGBRegressor does not provide the coefficients of the training elements, so it is unclear whether XGBRegressor overfits or not. Thus, this analysis chooses Ridge to be the second option for the rainfall prediction due to better coefficients as well as low MAE and RMSE.

Lastly, here are suggestions for further analysis to potentially improve the prediction.

1. Keep trying other machine learning models to get a better result.
2. Feature optimization to improve the prediction.
3. Finding out the pattern of outliners and then removing them may improve the prediction of regression models.
4. For model users, adjusting the level ranges might get a better result from classification. Also, by comparing the results from classification and regression models, model users may be able to predict a drought month or flood month that we can see the outliners from the line charts generated by regression models.

# 6 Reference
Kerala. (n.d.). In Wikipedia. Retrieved on Aug 4, 2021, from https://en.wikipedia.org/wiki/Kerala
Fernando, J. (2021). R-Squared Definition. Investopedia. Retrieved from https://www.investopedia.com/
Deep AI (n.d.). Accuracy in Machine Learning. Retrieved on Aug 4, 2021, from https://deepai.org/machine-learning-glossary-and-terms/accuracy-error-ratea
Data School (2014). Simple guide to confusion matrix terminology. Retrieved from https://www.dataschool.io/
Acharya, S. (2021). What are RMSE and MAE? Towards Data Science. Retrieved from https://towardsdatascience.com/
