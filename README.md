# Project 3: Finding Uplifting News in Reddit
### Javier Martinez Abrego Cantu

---

## Executive Summary


### Contents:
- [Problem Statement](#Problem-Statement)
- [Data Dictionary](#2018-Data-Import-and-Cleaning)
- [Data Extraction](#Data-Extraction)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Data Modeling](#Data-Modeling)
- [Data Visualization](#Data-Visualization)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

---


## Problem Statement
Whether it is TV, Radio, Twitter, Facebook or any other social media platform, we get a constant flux of news shoved into our heads every day. Unfortunatley, we dont realize that most of the news we read is either negative or conflicting. By using r/news and r/upliftingnews, I want to see if I can create a model that predicts which stories are uplifting and what makes a story uplifting.

---

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|title|object|titles|r/upliftingnews and r/news titles from 2016-2018| 
|subreddit|object|titles|Which subreddit this title belongs to| 
|score|int|titles|Reddit score from that post| 
|id|object|titles|Reddit id for that post| 

|Feature|Type|Dataset|Description|
|---|---|---|---|
|title|object|comments|r/upliftingnews and r/news comments from 2016-2018| 
|subreddit|object|comments|Which subreddit this comment belongs to| 
|score|int|comments|Reddit score from that comment| 
|id|object|comments|Reddit id for that comment|

---

## Data Extraction

In this section I go through the process of getting titles and comments from reddit by using pushshift.io's API. I used this API because it allowed me to grab posts from different timeframes much more asier than Reddit's original API.  

---

## Exploratory Data Analysis

In the Exploratory Data Analysis section I go through the dataframes created for the post titles and comments from Jan 1st 2018 to Dec 1st 2018. I remove duplicate titles and comments based on the id. This way we remove any particular post we happened to include multiple times because each different post or comment has its own unique id. I also create a binary column indicating 1 for the title/comment being from the subreddit r/upliftingnews and 0 for the title/comment being from r/news


---

## Data Modeling

For this project, I used piplines with gridsearches to be able to find the best model that can predict whether a post is in r/news or r/uplifting news. For vecotrizing options I used Count Vectorizer, TF-IDF Vectorizer and Hashing Vectorizer. As for the actual models, I used K Nearest Neighbors, Random Forrest, AdaBoost and Logistic Regression. By using gridsearch I was also able to find the best possible parameters for both the models and vectorizers.

---

## Data Visualization

Looking at raw DataFrames and numbers can be a bit boring. Therefore I created a couple of visualizations that can help futher understand my results. Bar Graphs, Confusion Matrices and Word Clouds are included in these visualizations

---

## Conclusions and Recomendations
This project helped me further undestand the data science process, from finding a problem statment, gathering data, modeling to visualizations. I chose these two subreddits because as a frequent data user, I find myself browsing through r/upliftingnews quite often and thought it would be a great idea to be able to create a model that could potentially find any news story and be able to tell whether it is uplifting or not. Although my model is far from perfect I believe it does quite well. Because it focuses on a few key words it might have trouble with titles that have both both higly and negativley correlated words within the title. 

As expexted, our model worked better with titles than comments, since people in the comment  tend to post their opinions, reference other articles or anecdotes that deviate from the acual topic of the post. As a recomendation to anyone doing any project similar to this, I would suggest taking only the titles for this very same reason. 

Because r/news and r/upliftingnews are not utually exclusive (in fact r/upliftingnews is a subset of r/news), our false positives are not actually bad. It means that the model is 'mistaking' someting in r/upliftingnews as r/news which is not wrong. I believe it would have been better to maybe find another subreddit such as r/horriblydepressing or r/sadnews and be able to create a model that categorizes news titles as sad, neutral or uplifting.
