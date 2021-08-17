# Introduction
## Summary
A company sells different kinds of alcohol across regions in Russia, there was a success after running a wine promotion in Saint Petersburg. This analysis would like to suggest further promotions to maximize the profits. However, the current situation allows us to target only a few regions due to a limited budget. By generating more short-term wins, our company will eventually extend the business throughout the country.

With regards to figuring out the current situation, analyzing the micro and macro environment is required. For example, Porter’s five forces model is a common tool to understand a business' micro-environment (Chaffey, 2019, p70). To analyse the impacts of external factors, PESTLE can be used for knowing the macro environment (Brown, 2019, p29). This report will use clustering methods to select the regions with the same wine buying behavior as Saint Petersburg. It is a part of macro environment analysis that our business can earn a higher possibility to succeed by knowing external factors. Apparently, the regions where people have a similar buying trend would be potentially affected by the same wine promotion we proceeded in Saint Petersburg.

Since the budget allows us to pick only 10 regions for the next marketing campaign, this report will not only cluster the regions by historical wine sales at all times but take into account the recent sales of all alcohol. In this way, this report is able to recommend the priority of these 10 regions for the promotions. It will be beneficial for operation management as well as project management in regards to a limited budget.

## Analytics Tool and Dataset
This analysis uses Python as the analysis tool. The given dataset contains the sales numbers of 5 kinds of alcohol, wine, beer, vodka, champagne, and brandy, in different regions from 1998 to 2016. It has 1615 rows and 7 columns.

# Prepare
## Analysis Plan
The analysis plan is to answer the questions.

1. What is the sales trend of wine in different regions?
2. Which regions have the same buying behavior as Saint Petersburg?
3. What are the top 10 regions with higher potential returns for the next wine promotion?

## Method
This report will transform the dataset into two different tables. They are for two different dimensions of analysis.

1. To cluster the regions by the sales trend of wine, this table contains historical wine sales at all times.
2. The other table contains the average sales of different alcohol during the last three years.

The analysis steps will be as follows.

1. Review the data, clean it, and then transform it into 2 major tables.
2. Identify a ideal number of clusters for K-means by using Elbow method.
3. Cluster the regions by K-means clustering.
4. Select the top 10 areas that have the highest potential profit for the promotions.
5. Get another region list by using hierarchical clustering with the recent sales of different alcohol.
6. Comparing the clustering results from two different methods.

As for identifying a suitable number of clusters, Elbow Method can help determine the proper cluster for KMean clustering based on the sum of squared distance, SSE(Flood, 2018).

# Process¶
## Data Cleansing and Exploratory Data Analysis
This section involves data cleansing with an exploratory data analysis. It is a preparation of the dataset for further analysis.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/01_msno.png)

It seems there is a pattern. When sorting the dataset by regions, the missing values gather together. Thus, the next step is to figure out what particular regions have missing values. Are these regions' data completely lost in all kinds of alcohol, or are only some data missing? If it is just partially missing, will it still be useful for further analysis?

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/02_msno.png)

After removing the Chechen Republic and Republic of Ingushetia records, there is no missing value in the table. The first table containing all sales of different alcohol during the last three years is complete so far.

The next step is to prepare the other table containing the wine sales records at all times. Since some regions only lose partial sales records of wine, this step will fill the missing value by an average sales number.

Furthermore, because this table will be used for clustering based on the yearly sales trend, dividing the sales by the maximum sales number will force the sales of different regions to be in the same range. Thus, the clustering result will be affected by relative magnitude instead of the real sales numbers.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/04_msno.png)

Now, the second table containing the historical sales of wine is complete. So far, there are two major tables for further clustering analysis as follows.

1. A table contains all wine sales records in relative magnitude at all times.
2. A table contains the average sales of different categories during the last three years.

# EDA Summary

The given dataset has missing values. Most missing values are from 4 regions, Chechen Republic, Republic of Crimea, Republic of Ingushetia, and Sevastopol. The preparation process falls into two parts because this report would like to cluster the regions by two dimensions, the current sales combination of all alcohol and the wine sales trend.

Two regions do not have sales records during the last three years. Thus, the preparation of the first table is to remove the records of Chechen Republic and Republic of Ingushetia. Then, "data_recent" containing the average sales of different categories during the last three years is ready.

As for the other table, the further analysis aims to cluster the regions based on the sales trend of wine. Since some regions have partial missing records of wine, the preparation was to fill the missing value by an average sales number. Plus, in order to let the cluster by relative magnitude instead of the real sales numbers, the sales numbers were divided by the maximum number of wine sales. Then, "data" is cleaned by removing Chechen Republic, which does not have any sales record of wine.

However, the "data" table still needs transformation to make it suitable for further clustering. Below "data_pivot" is the complete version for analysis.
