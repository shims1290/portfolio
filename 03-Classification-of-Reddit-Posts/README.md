<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">

# Project 3 - Web APIs & NLP

## Executive Summary

Using `Logistic Regression` model and `Tf-idf Vectorization`, we developed an NLP model to optimise the contents within a subreddit community for relevance. The model obtained 95% accuracy score, meaning it can make 95 accurate prediction about the true membership of the post out of every 100 predictions. The recall/ sensitivity score of the model is also relatively high at 98%. This means that there is only a 2% chance that the model will misclassify posts that truly belongs to the subreddit as an irrelevant post. 

The model used to determine the relevance of the posts is trained and tested using 1,700 observations of past subreddit posts scraped across the r/stocks and r/CryptoCurrency subreddit communities in mid-2021. We primarily draw information and insights from the textual data within the respective subreddit post titles and contents for model training.   

### Background

Reddit Inc. is a successful social media company with increasing revenues potential. In October 2020, it averaged 52 million daily active users [(source)]("https://www.wsj.com/articles/reddit-claims-52-million-daily-users-revealing-a-key-figure-for-social-media-platforms-11606822200") and it expects to generate $170 million revenue in 2020, primarily from its ad business [(source)]("https://www.businessofapps.com/data/reddit-statistics/").

Much of the success of the social media platform is owed to its ability to forge genuine and safe engagements among its users. With a mission to bring community and belonging to everyone in the world [(source)]("https://www.redditinc.com/policies/transparency-report-2020"), Reddit Inc. ensures the removal of spam posts or posts violating the content policy by admins, moderators and a scaled community moderation tool known as [AutoMod]("https://www.reddit.com/wiki/automoderator/full-documentation"). The chart below shows the nature and scale of content removal in 2020. 

<img src="https://www.redditinc.com/assets/images/site/Chart3b.png" style="float: center; height: 300px">

<p style="text-align: center">Chart Source: <a href="https://www.businessofapps.com/data/reddit-statistics/">Reddit Inc.</a></p>

With the growing popularity of the platform, more subreddits will likely emerge to cover various niche topics within a broader domain (e.g. data science vs data engineering). Moderators may find it challenging to curate posts to prevent content dilution as new reddit users may errorneously post contents under inappropriate subreddits.

## Problem Statement

To help subreddit moderators ensure high content quality and relevance, we develop a classification tool using machine learning techniques (i.e. **Logistic Regression and Naive Bayes models**) to identify posts that are likely to be inappropriately posted under the "wrong" subreddits for removal. 

The success of the project depends on both the accuracy and sensitivity scores of the model:

> 1) Accuracy score: This metric is useful as it tells us how many predictions were true. ***The higher the accuracy score, the better the model***.
>
> 2) Sensitivity score: This is also a key metric because we want to avoid labelling a post that is relevant to the subreddit as irrelevant. The removal of relevant posts will frustrate the subreddit members and discourage them from posting in the future. This runs counter to Reddit Inc.'s objective to improve user experience, grow user base and increase advertising revenue potential. As such, ***we want to minimise the false negatives as far as we can. A higher sensitivity score is better as it implies fewer false negatives***.

## Data

In the project pilot, we do so by capitalising on textual data scraped from the [r/Stocks]("https://www.reddit.com/r/stocks/") and [r/CryptoCurrency]("https://www.reddit.com/r/CryptoCurrency/") subreddits. These two subreddits are suitable for use as part of classification model development because both subreddits have:
- **Large user base** (~3 millions each), implying strong advertising revenue potential. This also ensures availability and abundance of recent posts for sampling and model training.
- **Text-rich posts** that are conducive for NLP analysis.

The two datasets to be used for model training are as follows. Each dataset has **1,700** observations scraped from the respective subreddits. See `02 Data Extraction.ipynb` for detailed web scraping procedure and code. 
>* [`stocks.csv`](../data/extracted/stocks.csv)
>* [`crypto.csv`](../data/extracted/crypto.csv)  

The data dictionary of the extracted data is below:

|Feature|Type|Description|
|:---:|:---:|:---| 
|subreddit|*string*|Indicates the membership of the post, i.e. `stocks` for r/stocks and `CryptoCurrency` for r/CyptoCurrency.| 
|created_utc|*integer*|UTC or Coordinated Universal Time is the primary time standard by which the world regulates clocks and time. This indicates the time when the post was created. This is based on the Greenwich Mean Time or GMT is the clock time at the Royal Observatory in Greenwich, London.| 
|title|*string*|Title of the reddit post.| 
|selftext|*string*|Contents of the reddit post.| 

For model evaluation and analysis, we assume r/stocks to be the anchor subreddit that we want to optimise post curation and content relevance for. Posts from r/stocks will be labelled or tagged as true member to the r/stocks subreddit (or 1 if classification variable is dummified). By extension, posts from r/CryptoCurrency will be considered as non-member of the r/stocks subreddit (or 0 if dummified). 

The posts scraped are created between the following timeframe:
* r/stocks: `2021-06-22 20:17:38` to `2021-07-21 07:03:24`
* r/CryptoCurrency: `2021-07-18 15:17:13` to `2021-07-21 07:02:29`

## Recommendations

1) **Deploy the model for testing with live data** to optimise contents for relevance. Given the strong performance of the model (95% accuracy score and 98% sensitivity score), the team can stand to benefit from deploying the model for pilot testing on the reddit platform.  

2) **Flag posts classified as non-member for moderators' assessment**. There is a risk of incurring user frustrations if the subreddit members' relevant posts become removed as a result of the model misclassification. To minimize wrongful post(s) removal, we can use the model's recommendation to flag possibly misclassfied posts for the moderators' consideration. This will help the moderators save time as they do not need to closely screen all the posts; they can just focus on reviewing the posts that the model has flagged. 

3) **Share keywords insights with the moderators**. This will help moderators set rules for content posting using the AutoModerator to ensure irrelevant topics will not be posted within the community. 

### Next Steps

In future, we can extend on this project to:

- Collect data samples across a longer time (e.g. the past year) for training and model optimisation to pre-empt risk that the topics of discussion and keywords may change across different times of the year 
- Train and further optimise the model for production across more subreddit communities 
- Train the data using irrelevant posts from more than one source

# Code Directory

01: Introduction
02: Data Extraction  
03: Data Cleaning, Exploratory Data Analysis & Vectorization  
04: Modelling with CountVectorizer  
05: Modelling with TF-IDF Vectorizer  
06: Model Evaluation, Findings & Recommendations 