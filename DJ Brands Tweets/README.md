# 1 Introduction
## 1.1 Summary
inMusic Brands Inc. is one of major DJ equipment companies in the world. inMusic has 20 brands in DJ, electronic musical instrument, consumer electronics, etc. The DJ equipment brands are Numark, Rane DJ, and Denon DJ.

This social media analysis uses the messages crawled from Twitter. The time period is from July 16th to July 25th. By analyzing the data, we will be able to understand how people react to these brands, including the brands of competitors. Also, it would help understand the key customers in the DJ community. Once the key customers are identified, we will be able to target these key users and then connect to different customer groups.

## 1.2 Analytics Tool and Dataset
The dataset is collected by Twitter API by searching the brands of our company and the major competitor, "pioneer DJ," "Numark," "Rane DJ," and "Denon DJ." Also, in order to analyze not only these brands but the DJ community. The search keywords include 4 major types of DJ products, "DJ mixer," "DJ controller," "DJ turntable," and "CDJ."

This paper uses Python as the analytics tool, and the data for the analysis contains 2070 messages.

# 2 Prepare
## 2.1 Analysis Plan
The analysis plan is to answer the questions.

1. When to post would get more retweets and likes?
2. What are the most common words used in these messages?
3. Which messages are the most sentimental?
4. Which company is more popular by comparing the brands of inMusic to Pioneer DJ?
5. How do different communities connect to each other?
6. How accurate is a model to predict the likes and retweets that the messages are going to get?

## 2.2 Method
First of all, the appendix shows the process of crawling data from the Twitter API. Then, this analysis will load the .json file with 2070 Twitter messages. The steps of this analysis are as follows.

1. Load the .json files and transform them into dataframes with needed columns
2. Plot a heatmap to understand when to post would get more likes and retweets.
3. Clean the text messages and plot graphics to know the common keywords used in these messages.
4. Plot a line chart to compare the frequency of mentioning inMusic's brands and Pioneer DJ.
5. Plot a network to know where the communities are and who the key users connect to different groups.
6. Build a model to predict the likes and understand how accurate the model is.

# 3 Process
## 3.1 Data Cleansing
This section involves data cleansing. It is a preparation of the dataset for further analysis. First of all, load the essential pakages.

Load the .json files and review the data structure. Confirm that there are 2070 messages in the .json file. Then, collect some information we need for further analysis, such as "created_at," "full_text," "retweet_count," "favorite_count," "screen_name, and "retweeted_status."

![](/images/df_01.jpg)


