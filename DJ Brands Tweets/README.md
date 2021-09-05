# 1 Introduction
## 1.1 Summary
inMusic Brands Inc. is one of the major DJ equipment companies in the world. inMusic has 20 brands in DJ, electronic musical instrument, consumer electronics, etc. The DJ equipment brands are Numark, Rane DJ, and Denon DJ.

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

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/df_01.jpg)

Detect the types of languages used in the messages by the using detect_langs function from the langdetect package. Choose the posts only in English, and then make sure there is no missing value in the data. After the preparation, there are 2008 messages left in the data frame.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_01.jpg)

Then, start cleaning the text messages for keyword analysis. Then, count the words used in the messages by using the word_tokenize function from the nltk pakage. Also, give sentiment polarity and subjectivity cores for the messages. Although there are some missing values in the "retweet_from" column, it is acceptable since not every post is retweeted from someone. This analysis will drop unuseful columns when plotting a network graphic.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/df_02.jpg)

After the review, there are many missing values in the retweet_from column. It is acceptable since not every post has a retweet.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_02.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/graphic_01.jpg)

## 3.2 Exploratory Data Analysis
### 3.2.1 Engagement Analysis

Take a look at the posts using the highest number of words. It turns out these posts are from the same person, TurntableTy1. This user frequently posts the same content, and these posts do not get any likes and retweets.

Here are the top 10 posts with the highest positive sentiment. Interestingly, post No. 2035 is labelled as positive sentiment, but actually, it is sarcasm that it says the device crashes. It will be a subject how this analysis could improve to filter this sort of post.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/df_03.jpg)

The posts with DJ topics do get many likes. If we sort the messages by likes, these posts are relating to DJ.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/df_04.jpg)

Prepare a dataframe to understand when to post would get higher retweets as well as likes. The process will divide the numbers by the maximum value to represent the proportion between 0 to 1. After analyzing, posting at 11 pm would get the highest retweets and likes. As for retweets, posting at 7 am and 2 pm would get high retweets as well.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/heatmap.png)

### 3.2.2 Keyword Analysis
In this section, let us see what common keywords are used in the entire DJ community. Clearly, "turntable," "hip hop," "party," etc., are commonly used in these posts. Likewise, it is good to see the common keywords per brand. Here are posts with a "Pioneer" keyword mention "controller," "mixer," "tutorial," etc., as well as "David Guetta", who is a world-known DJ. The posts with a "Numark" keyword mention "controller," "vinyl," "price," etc., as well as "Serato" and "Ableton", which are DJ and music production software. As for Rane, the posts mention "Serato," "company," "virtual," etc. The interesting keyword here is "djsixty7even7," which should be investigated. Next, the posts relating to "Denon" mention "controller," "price," "interface," etc.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/pioneer.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/numark.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/rane.png)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/denon.png)

### 3.2.3  Popularity Analysis
First, regarding the bar chart below, Pioneer DJ gets the lowest average polarity score. However, it does not mean the brand image of Pioneer DJ is worse than inMusic's brands, Numark, Rane DJ, and Denon DJ. If looking into the box plot, it shows the scores of Numark's posts could go very low, although the average score is higher than Pioneer DJ. The posts relating to Rane DJ are too few so that the number could be biased. As for Denon DJ, it seems the feedback from the users is really better than Pioneer DJ.

Next, the line chart demonstrates Pioneer DJ is the most popular brand in the entire DJ community. Even though this analysis sums up the posts relating to inMusic's DJ brands, the total number is still lower than Pioneer DJ's post at all times. It tells most people are talking about Pioneer DJ instead of inMusic' brands.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/bar_01.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/box_01.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/line_01.jpg)

### 3.2.4  Network Analysis
The purpose of this section is to figure out who are the key users connecting different small communities. After choosing only retweet posts, there are only 337 messages left for network analysis. When looking into the network graphic, there are several key users shown on it. For example, a long trace connects 2 huge groups. There are 3 key users on this trace, Zinfuryanno, DJTimesMag, and DANNYFURLONGDJ. Once any one of these 3 users leaves, the huge community will split into 2 groups. Moreover, there are small communities around ItsJeffreyJeff, classicsdujour, tomthunkitsMind, Lorenzosbeats, thelittleidiot, etc. as the centers.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/df_05.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/networkx_01.jpg)

# 4 Analyze
Here starts building a model to predict the likes and retweets that the posts are going to get by machine learning. First, split the message into two cohorts in terms of retweets and likes. The prediction will distinguish whether the posts are going to get high retweets or likes. Next, prepare the data to train the model. In this part, this analysis will make a text matrix for machine learning. Then, after building the model, the accuracy of the optimized model to predict likes is 60.4% which is not accurate enough. Besides, the optimized model to predict retweets is only 66.7%. The prediction for both retweets and likes is not so ideal.

The worse situation is a false positive prediction. Posts are predicted that a high number of likes will be, but actually, they get few likes. The false-positive rate to predict likes is 36.4%, which is still a little high. As for predicting retweets, the false positive rate is 26.3%.

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/df_06.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_03.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_04.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_05.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_06.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_07.jpg)

![](https://github.com/foolwuilin/Data_Analytics_Projects/blob/main/DJ%20Brands%20Tweets/image/description_08.jpg)

# 5 Conclusion
In sum, here are viewpoints as below.

1. Posting at 11 pm would get both high retweets and high likes. As for retweets, posting at 7 am and 2 pm would also get high retweets.

2. "turntable" and "controller" are commonly used in DJ-related posts. The posts containing "Pioneer" mention "mixer," "tutorial," "David Guetta," etc. As for the posts containing the names of inMusic's brands, "price," "Serato," and "interface," etc., are the common keywords.

3. Although the average polarity score of Pioneer DJ's posts is not as high as inMusic's, Pioneer DJ is more popular that dominate the higher proportion of the posts.

4. Zinfuryanno, DJTimesMag, and DANNYFURLONGDJ are the key users bringing several major communities together. Plus, ItsJeffreyJeff, classicsdujour, tomthunkitsMind, Lorenzosbeats, thelittleidiot, etc., are important users creating some small communities.

5. The prediction model is not ideal. Only 60.4% of accuracy to predict likes and 66.7% of accuracy to predict retweets. It tells there is too much noise inside the training materials.

The prediction is still positive, although the numbers are not ideal. The model still could be a short-term countermeasure. As for a long term solution, it just needs an improvement. Thus, the Suggested further analysis.

1. Determine where the noise is and then improve the matrix to train the model.

2. Use other machine learning methods for deeper analysis and prediction.

3. Improve the prediction by a pipeline method.
