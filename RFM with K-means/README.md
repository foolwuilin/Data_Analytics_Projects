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
The structure of this analysis would be split into two major chapters. The first section is to cluster the customers by using a linear quantile method. In this way, it will be clear who purchase on certain days and how much they spend recently.
The second section is a k-mean clustering analysis. This method splits the customers into 3 different clusters in different criteria, recency, frequency, and monetary. In this way, there will be a group of selected people marked as the most important customers for this business.

Lastly, this analysis campares the outcomes from the linear quantile method and the k-mean clustering method. There is a difference between these two methods to achieve customer segmentation.

# 4. Prepare¶
First of all, take a look at the dataset.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/RFM%20with%20K-means/images/df_01.jpg)




