## [Press here for the original Python codes.](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/quantile-k-means-and-hierarchical-clustering.ipynb)

# 1. Introduction
## 1.1 Summary
A company sells different kinds of alcohol across regions in Russia, there was a success after running a wine promotion in Saint Petersburg. This analysis would like to suggest further promotions to maximize the profits. However, the current situation allows us to target only a few regions due to a limited budget. By generating more short-term wins, our company will eventually extend the business throughout the country.

With regards to figuring out the current situation, analyzing the micro and macro environment is required. For example, Porter’s five forces model is a common tool to understand a business' micro-environment (Chaffey, 2019, p70). To analyse the impacts of external factors, PESTLE can be used for knowing the macro environment (Brown, 2019, p29). This report will use clustering methods to select the regions with the same wine buying behavior as Saint Petersburg. It is a part of macro environment analysis that our business can earn a higher possibility to succeed by knowing external factors. Apparently, the regions where people have a similar buying trend would be potentially affected by the same wine promotion we proceeded in Saint Petersburg.

Since the budget allows us to pick only 10 regions for the next marketing campaign, this report will not only cluster the regions by historical wine sales at all times but take into account the recent sales of all alcohol. In this way, this report is able to recommend the priority of these 10 regions for the promotions. It will be beneficial for operation management as well as project management in regards to a limited budget.

## 1.2 Analytics Tool and Dataset
This analysis uses Python as the analysis tool. The given dataset contains the sales numbers of 5 kinds of alcohol, wine, beer, vodka, champagne, and brandy, in different regions from 1998 to 2016. It has 1615 rows and 7 columns.

# 2. Prepare
## 2.1 Analysis Plan
The analysis plan is to answer the questions.

1. What is the sales trend of wine in different regions?
2. Which regions have the same buying behavior as Saint Petersburg?
3. What are the top 10 regions with higher potential returns for the next wine promotion?

## 2.2 Method
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

# 3. Process¶
## 3.1 Data Cleansing and Exploratory Data Analysis
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

# 3.2 EDA Summary

The given dataset has missing values. Most missing values are from 4 regions, Chechen Republic, Republic of Crimea, Republic of Ingushetia, and Sevastopol. The preparation process falls into two parts because this report would like to cluster the regions by two dimensions, the current sales combination of all alcohol and the wine sales trend.

Two regions do not have sales records during the last three years. Thus, the preparation of the first table is to remove the records of Chechen Republic and Republic of Ingushetia. Then, "data_recent" containing the average sales of different categories during the last three years is ready.

As for the other table, the further analysis aims to cluster the regions based on the sales trend of wine. Since some regions have partial missing records of wine, the preparation was to fill the missing value by an average sales number. Plus, in order to let the cluster by relative magnitude instead of the real sales numbers, the sales numbers were divided by the maximum number of wine sales. Then, "data" is cleaned by removing Chechen Republic, which does not have any sales record of wine.

However, the "data" table still needs transformation to make it suitable for further clustering. Below "data_pivot" is the complete version for analysis.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/05_heatmap.png)

# 4. Analyze

In order to cluster regions by a time series of wine sales, this report will use K-means clustering. The K-means algorithm would allow the clustering process to allocate every data point to the nearest cluster with the shortest distance between points and the centroids (Garbade, 2018). Thus, by using K-means clustering, this report is able to split the regions into different groups having similar buying behavior of wine based on the sales trend.

However, before starting K-means clustering, figuring out the ideal number of clusters is required. Too few clusters would cause the entities in a group to have many different traits. Too many groups would cause that there is not much difference between groups. Therefore, this section proceeds with the Elbow method in order to determine the best number of clusters.

## 4.1 Elbow Method

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/06_mean_std.png)

**"data_pivot"** seems the distributions of the variables are not quite skewed. Since K-means clustering works better on variables with almost the same mean and variance, the variables in this table look acceptable for further analysis. However, the below normalization shows the normalized table is also good for K-means clustering. Thus, this report will use the normalized table for the analysis.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/07_elbow.png)

## 4.2 K-means Clustering¶
Regarding the outcome of the Elbow method, it is clear that 4 clusters are the ideal solution for this situation. As a result, this analysis splits regions into 4 clusters and then visualizes the buying behavior of the regions in different clusters. The heatmap shows 17 regions have the same buying behavior of wine as Saint Petersburg that the customers buy more wine between 2003 to 2011.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/08_behavior.png)

With regards to the heatmap above, the regions of cluster 0 have a peak of purchasing wine between 2007 and 2016. Cluster 1 buys more wine from 2003 to 2011. Cluster 2 has steady buying behavior that there are no obviously huge sales in the history. In contrast, cluster 3 has steady high wine sales at all times.

## 4.3 Top 10 Regions¶
In order to select 10 potential regions from the 17 regions in cluster 1, this section is to pick the most valuable regions by regression analysis and the actual sales numbers. First, the higher the correlation coefficient, the higher the potential profit. A positive correlation coefficient means the sales number increases every year. Thus, the correlation coefficient will be one criterion to select regions.

Another criterion is the actual sales of the regions. The previous clustering uses relative magnitude to cluster regions by the sales trend of wine in years. However, in this way, the regions in cluster 1 may not have as high sales as Saint Petersburg. Thus, further analysis will calculate average sales during the last three years and then rank regions by these sales numbers as well as the correlation coefficients.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/09_trend.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/10_0_cluster.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/10_scatter.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/11_top10.jpg)

So far, by sorting the score numbers, the above table clearly shows the top 10 regions where the next wine promotion should proceed. The below scatter plot demonstrates the distribution of these 10 regions.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/12_top10scatter.jpg)

The K-mean clustering helps select regions by the sales trend of wine. Also, the coefficients and sales numbers help give scores for ranking. Because of this, this report is able to pick the top 10 regions for the next wine promotion.

However, it is beneficial to see a different result by taking into account all kinds of alcohol. Thus, the next section will use another clustering method to find the regions similar to Saint Petersburg in terms of the sales of different alcohol.

## 4.4 Hierarchical Clustering

"data_recent" contains the sales records during the last three years when the previous Process phase. Next, this section groups the table by regions and get the average recent sales of different alcohol. By looking at the dendrogram of hierarchical clustering, splitting regions into 4 clusters is an option. If reducing the number of clusters, the hierarchical distance will be too long that there is much difference between clusters.

The cluster with Saint Petersburg has 34 regions. By comparing the hierarchical clustering and K-means clustering results, this report is able to come out 6 high priority regions out of the top 10 regions. This approach is also beneficial for operation and project management to arrange the priority of tasks.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Customer%20Behavior%20Clustering/image/13_hierarchy.png)

**Top 10 Regions in both lists: ['Leningrad Oblast', 'Chukotka Autonomous Okrug', 'Kaliningrad Oblast', 'Pskov Oblast', 'Saint Petersburg', 'Kursk Oblast']
Top 10 Regions not in the hierarchical cluster: ['Republic of Karelia', 'Kirov Oblast', 'Sverdlovsk Oblast', 'Penza Oblast']**

# 5. Conclusion
This report aims to select 10 potential regions for the next wine promotions to maximize the profits. The chosen methods are K-means clustering and hierarchical clustering. Regarding K-means clustering, this report decided to proceed with K-means clustering with 4 clusters by the Elbow method. The K-means clustering with historical wine sales selects 17 regions with the same wine buying behavior as Saint Petersburg.

In order to figure out which 10 regions have the highest profitability. This report selects the regions by regression analysis. The higher the correlation coefficient, the higher the potential profit. Furthermore, by taking into account the wine sales, this report is able to pick the top 10 regions as below.

1. Republic of Karelia
2. Kirov Oblast
3. Leningrad Oblast
4. Sverdlovsk Oblast
5. Chukotka Autonomous Okrug
6. Kaliningrad Oblast
7. Pskov Oblast
8. Saint Petersburg
9. Kursk Oblast
10. Penza Oblast

As for the hierarchical clustering, this report uses a table with recent sales of all alcohol. After splitting the regions into 4 clusters, there are 34 regions picked by the sales combination. Since clustering by historical sales should more accurately reflect the buying behavior than clustering by only the recent sales, this report takes the top 10 regions clustered by K-means clustering with historical sales as a primary list.

By comparing the top 10 regions with the region list picked by the hierarchical clustering, this report is able to recommend that 6 regions should be the primary regions for the wine promotions.

1. Leningrad Oblast
2. Chukotka Autonomous Okrug
3. Kaliningrad Oblast
4. Pskov Oblast
5. Saint Petersburg
6. Kursk Oblast

Then, below 4 regions can be set as the lower priority in the top 10 regions.

1. Republic of Karelia
2. Kirov Oblast
3. Sverdlovsk Oblast
4. Penza Oblast

Since the budget is limited, it will be beneficial that this report suggests a priority list. This approach would help the operation team to plan risk management. Also, it will help the project manager create a better plan for setting up the priority of tasks.

According to the heatmap of the clusters selected by K-means, the 4 clusters have totally different buying trends. Clearly, the K-means clustering does split the regions properly. However, clustering by other methods will still be nice to have. Further analysis can try other methods and then compare different results to seek whether there is a better solution.

# 6. Reference
Brown, M. (2019). Innovation in Marketing - CIM Official Module Guide. Berkshire: The Chartered Institute of Marketing.

Chaffey, D. (2019). Digital Marketing: Strategy, Implementation and Practice (7th ed.). Harlow: Pearson Education.

Flood, B. (2018). K-means Clustering: Algorithm, Applications, Evaluation Methods, and Drawbacks. Towards Data Science. Retrieved from https://towardsdatascience.com/

Garbade, M. J. (2018). Understanding K-means Clustering in Machine Learning. Towards Data Science. Retrieved from https://towardsdatascience.com/
