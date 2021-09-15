# 1. Introduction
## 1.1 Summary
A market basket analysis would help understand the purchase behavior of customers. In a shopping cart, normally, there are several items as a combination depending on the preference of different customers. Knowing what items would come after particular items, shelf planners would have better ideas of what items should be put together. Also, retail managers would better understand what sorts of items should be stored in the warehouse to prevent insufficiency.

## 1.2 Analytics Tool and Dataset
This analysis uses Python as an analytics tool.

There 2 given datasets. One contains 38765 transaction records with member IDs, transaction dates, and item names. The other one contains 14963 rows with only the items per transaction.

# 2. Prepare
## 2.1 Analysis Plan
The analysis plan is to answer the questions.

1. What are the most frequently sold items?
2. what are the consequents of the chosen items?
3. How confident do the consequents come after the items?
4. What are the most important items that should always be in the store?
5. How does the item network looks like?
6. What is the difference between analyzing the data based on customer ID and different transactions?

## 2.2 Method
This analysis will load the 2 datasets. The first one with member IDs will be used for creating a basket model based on IDs. The other one will be used for creating a model based on transactions. Literately, the total number of sold items should be the same. The analysis steps are as below.

1. Prepare the 2 .csv files
2. A bar chart to see the most frequently sold items
3. A quick look at the relationship between items
4. Select an item to proceed with a further analysis
5. A heatmap to review the association between antecedents and consequents
6. A network graphic to know the connections of the selected item

# 3. Process
First of all, load the essential packages and read the 1st datasets.
![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_01.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_01.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_02.jpg)

Get the support value by Apriori algorithm.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_03.jpg)

Create a dataframe with product support, confidence, and lift values.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_04.jpg)

Take a quick look at the distribution of the product combination

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_02.jpg)

# 4. Analyze
## 4.1 Dataset-1 (Customer IDs, Transaction dates, and Items)
So far, the datafame is ready for a further analysis.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_05.jpg)

Get the most important 5 items that customers would buy after purchasing whole milk

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_06.jpg)

Get the top 10 persentile items and then plot heatmaps to know how strong the association is based on support and lift values.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_03.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_04.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_05.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_06.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_07.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_08.jpg)

## 4.2 Dataset-2 (Transaction with Items Only)
First, review the total number of items to see wether there is any difference between dataset 1 and dataset 2. After checking, the numbers are the same. However, this analysis will generate a dataframe based on every transaction instead of customer IDs. Let's see the difference.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_09.jpg)

Get the support values by Apriori.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_07.jpg)

Generate a dataframe with support, confidence, and lift values by Association Rules 

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/df_08.jpg)

Only 10 combinations when preparing it based on each transaction.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_10.jpg)

Plot heatmaps to know how strong the association is based on support and lift values

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_11.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_12.jpg)

See the distribution of these 10 combinations.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_13.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/Market%20Basket%20Analysis/images/plot_14.jpg)

# 5. Conclusion
In sum, here are viewpoints as below.

1. Top 10 sold items are whole milk, other vegetables, rolls/buns, soda, yogurt, root vegetables, tropical fruit, bottled water, sausage, and citrus fruit.
2. Top 5 consequents of whole milk are other vegetables, rolls/buns, soda, tropical fruit, and yogurt.
3. Every item in the top 10 percentile of all combinations has high confidence that customers buy the items with the whole wilk.
4. Regarding the network graphics, whole milk has the highest number of connections with other items.
5. Total items in these two datasets are the same. However, if generating a basket analysis dataframe based on each transaction, the number of combinations would be fewer than creating it based on customer IDs.

Suggested further analysis.

1. Since there is a dataset with transaction dates and customer IDs, the dataset can also proceed with a sales trend or customer behavior analysis.
2. Choose other items to explore what consequents should be prepared in order to prevent product insufficiency.
3. Other visual types to explore more insights.
