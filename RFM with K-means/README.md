# 1. Introduction
The given dataset contains sales records with 64.682 transactions and 22.625 customers IDs in 2016. The columns are Transaction, Customer ID, Transaction ID, Category, SKU, Quantity, and Sales Amount.

# 2. Objectives
The questions for this analysis are as follows.

1. What is the retention rate of the users in terms of the date since these users sign up.
2. Who are the top 5% frequency quantile with valid activity in 14 days? Who are the top 0.5% quantile in recency, frequency, and influence? Who are the top 10 most valuable users?
3. Who are the most valuable customers by using K-Means clustering?
4. The outcome difference between the k-means clustering and the linear quantile method.

# 3. Method
- Python 

This analysis splits into two sections. The first section is to cluster the customers by using a linear quantile method. This way, it will be clear who purchases on certain days and how much they spent recently.
The second section is a k-mean clustering analysis. This method splits the customers into three different clusters in different criteria, recency, frequency, and monetary. In this way, there will be a group of selected people marked as the most important customers for this business.

Lastly, this analysis compares the outcomes from the linear quantile method and the k-mean clustering method. There is a difference between these two methods to achieve customer segmentation.

# 4. Prepare¶
First of all, take a look at the dataset.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_01.jpg)

# 5. Process
Determine whether there is a null value in the dataset. After the review, there is no missing value in the dataframe.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/info_01.jpg)

# 6. Analyze
## 6.1 Quantile Method
Calculate the duration month.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_02.jpg)

Get the number of users in terms of how many months they have been with valid activities. Then, generate the matrix by using a pivot table.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_03.jpg)

Plot a heatmap to visualize the retention rates in terms of the duration and the date that the account is created.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_01.jpg)

Figure out the average sales amount in terms of the customers splits into different duration months. Also, plot a heatmap to understand the situation.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_04.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_02.jpg)

Make sure the last date of the transaction. The last date is Dec 31st, 2016. Thus, here is to set Jan 1st, 2017, as the date of this analysis is processing in order to calculate the recency (The lower recency, the better). Then, generate a new dataframe for recency, frequency, and monetary.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_05.jpg)

Here is to subset the data by the top 20% frequency quantile and the last activity in 2 weeks. The total number of customers in this group is 1,108.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/info_02.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_06.jpg)

Visualize the data to view the distribution of these 1,108 customers.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_03.jpg)

Here is to subset the data by the top 5% quantile in recency, frequency, and monetary. The total number of these customers is 224.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/info_03.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_07.jpg)

Again, visualize the data to see where these 224 customers are.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_04.jpg)

Subset the data by the top 1% quantile in recency, frequency, and monetary to get 17 customers, and then sort the value by monetary to pick the top 10 valuable customers.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/info_04.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_08.jpg)

Sort the values by monetary to get the top 10 valuable customers. Then, point out the top 10 customers in a scatter plot.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_09.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_05.jpg)

## 6.2 K-means Clustering
Because K-Means works well on variables with the same mean and standard deviation. Here is normalizing the data and reviewing the key statistics to verify whether the data is good to use. Here is to plot the distribution of the three subjects. As the graphics show, these numbers are highly skewed.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_06.jpg)

Get the log scale in order to get a better distribution and then plot the log numbers to see the distribution. Although the log recency is still slightly skewed, frequency and monetary look better than before.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_07.jpg)

Regarding the below elbow method, the sharpest angle is the optimal number of clusters. Thus, 3 clusters are the appropriate clusters.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_08.jpg)

Plot a line chart to compare the traits of clusters. Obviously, cluster 2 has higher frequency and monetary with short recency, which is much better than the others.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_09.jpg)

Plot a heat map to easily distinguish the cluster, cluster 2, with valuable customers.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/plot_10.jpg)

Identify the customers in cluster 2 and list out the customer IDs. There are 4262 customers in this cluster.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_10.jpg)

# 7. Conclusion
In sum, here are viewpoints as below.

1. The customers who started purchase in early 2016 have a higher retention rate. The customers who started purchase in Feb with six months duration and who started purchase in Aug with two months duration have a higher average expenditure.

2. 1,108 users are in the top 20% frequency quantile with an activity in the past two weeks. 224 users are in the top 5% quantile in recency, frequency and monetary. The IDs of the top 10 most valuable users are shown in the table above.

3. There is a significant difference between the results of the K-Means clustering and the linear quantile clustering. The K-Means clustering brings 4,262 customers together as a group, which might be too huge to target some customers for a specific marketing campaign.

Suggested further analysis.

1. Use other clustering methods to compare the differences.

2. More visualizations to get a better exploratory data analysis.

3. A clear marketing plan would help provide the direction to explore preferable information. 

