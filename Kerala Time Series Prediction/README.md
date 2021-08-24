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
