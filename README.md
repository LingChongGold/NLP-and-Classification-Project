# Project 3: Subreddit Classification Problem

In this project, we are tasked to select 2 subreddits from [Reddit](https://www.reddit.com/), scrape the posts and build 2 classification models to classify which post belongs to which subreddit. After the models is built, an evaluation have to be performed and we have to select the model that best answer the problem statement.

The project is split into 2 notebooks:
- First notebook gathers and cleaned the data
- Second notebook we performed exploratory data analysis, feature engineering, modelling and evaluation

# Problem Statement

**Data Science Problem:**<br>Create 2 classification model to identify if a post is from the subreddit [learn python](https://www.reddit.com/r/learnpython/) (positive) or [learn programming](https://www.reddit.com/r/learnprogramming/)  (negative). Select the model you think best answers the problem and evaluate the model.

**Business Problem:**<br>Identify whether a post should be in the learn python or learn programming subreddit. With a good classification model, we can move the posts to the respective subreddits. This allows our user select one amongst the two subreddit to join base on their interest, increasing user experience which in turns increases retention rate and traffic to the site<br><br>Further expansions like autotagging or suggesting to thread starter which subreddit is the best for the post to be created in can be considered for future iterations.  


# Executive Summary
In this project, we identified learnpython and learnprogramming subreddits, scrape data from them, built 4 classification models to identify which post belong to which subreddit, evaluate the top 2 models and select one which best answer our business needs, to identify whether a post should be in the learn python or learn programming subreddit and move the post to the respective subreddits.

We used requests to scrape the data, and identified that selftext which contains the text of the post is the best column we can use for our NLP classification problem. We then cleaned the data using BeautifulSoup, nltk's stopwords, regex and python's string manipulation. After gathering and cleaning the data, we are have a total of 1930 posts, 49.27% of them from learn programming and 50.73% from learn python. We have an almost equal ratio of post for each subreddit which is considered a good dataset to have for classification problems. From this we are also able to determine that our baseline accuracy is 50.73%

Wordcloud was created for each subreddit to visualise words that appear frequently in each subreddit and the top 20 words for the entire corpus was identified and plotted on a graph with their frequency count.

During this phase of exploratory data analysis we discovered that there are common words which frequently appear in both subreddits. A customised stopwords list was created. This customised stopwords list contains words which our models will ignore. We then performed stemming and lemmatizing on the self text column and identified that lemma text is the best compared to the original and stemmed text.

We then built 4 models:

- Count Vectorizer with Naive Bayesian's MultinomialNB
- Tfidf Vectorizer with Naive Bayesian's MultinomialNB
- Count Vectorizer with Logistics Regression
- Tfidf Vectorizer with Logistics Regression

and found out that the Count Vectorizer with Naive Bayesian's MultinomialNB model which has a score of 78.05% in our test data answers our business problem the best as it is not overfitted and has the best precision.

# Conclusion

Although one of the model has a higher score compared to our selected model, it do not answer our busines problem adequately. Its precision is lower compared our selected model and for our business problem, the cost of false positive is higher when compared to the cost of false negative.

For the next iteration to improve this model, we can look at running the model again after moving the posts to their respective classified subreddits to determine and check if the model performed better as we will have lesser overlapped posts due to the close nature of the selected subreddits. Or we can collecting larger dataset then tune our model again to improve its classification accuracy. We can also perform an analysis if title, author or number comments are able to make distinct classifications amongst the classes and consider adding them in as a feature to improve the model.

When the model is accurate enough, we can expand the usage to other subreddits and consider having subreddit auto-tagging function or subreddit suggestion when a thread starter is creating a post. This decreases the clutterness of information in our subreddits and allows more distinct subreddit categories for users to choose from, increasing user experience and retention, which will in turn increase traffic volume and popularity of reddit to the community.