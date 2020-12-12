# Twitter_Influence_Analyzer
TLDR:
This project uses various Machine Learning algorithms (Naive Bayes, Random Forest, XGBoost, K-means Clustering) to identify the impact Tweets have on politicians approval rating and determine whether it is possible to predict if a Tweet will have a positive or negative impact on the politicians approval rating.


## ABSTRACT: 
On November 8, 2016 history was changed forever. Donald Trump, one of the most controversial political figures ever,beat Hillary Clinton in the United States presidential race. Throughout his campaign Trump had used Twitter to post various tweets that sparked outrage. This report attempted to find a relationship between Donald Trump’s tweets and his approval rating. After the models were built, run, and tested, they still had fairly low accuracy. This is due to the complex nature of Trump’s approval ratings, and that it is influenced by far more factors than just his tweets. While we originally thought that most of the things that happen with Trump will be tweeted about, we didn’t take into account any delay between Trump’s bad behavior and his tweets about it. 

We also hypothesized that his tweets often contain similar clusters of words, that are also common media headlines. For this hypothesis, k means clustering was used, and the 20 clusters that were gathered from his tweets were indeed all common news headlines such as “Trump Urges Russia to find Clinton’s Missing Emails” from CNN. 

To give a general representation of what words Trump uses the most, the tweets were then parsed into individual words, and counted. This word cloud allowed us to visualize all words that Trump uses, and which words are most popular.
![alt text](https://github.com/akalia25/Twitter_Influence_Analyzer/blob/master/Screenshots/WordMap-2.png)


### Variables
The dependent variable that the model predicts is a binary variable that describes whether the public approval rate for Donald Trump increases or decreases as a result of his tweets. It is assumed that there are only two outcomes, either the rate decreases or not (increasing or unchanged).

One of the key explanatory variables in the tweet-analysis model would be text contents of all tweets posted by Donald Trump on a single day. It will be collected in the format of pure text. Since the primary function of the system is to perform predictive analysis based on his tweets, it is extremely crucial to capture all the words he posted to find a correlation between the change in his approval rate and specific vocabularies from his tweets.


### KMean:
To perform K-mean clustering on the tweets, all the tweets are transformed into bag of words as discussed in feature transformation. The distances between each tweet is computed using Jaccard distance in which the all words with a value of 0 in the bag of words is disregarded because matching zeros do not contribute to the similarity of two tweets. Based on the distance matrix, the cluster centers can be identified by going through iterations for K-mean clustering. The results can be visualized on a scatter plot. In addition, in order to clearly show the topic clusters, the top 5 frequently used words in each cluster is displayed to represent the cluster 
![alt text](https://github.com/akalia25/Twitter_Influence_Analyzer/blob/master/Screenshots/K-Mean%20clustering-2.png)


The confusion matrix for the Machine Learning Algorithms as well a brief summary on the model follows as below : (for a detailed report please see project_report document) 


### Naive Bayes:
One of the main goals of this project was to determine if the approval rating would be increasing or decreasing the day after Trump tweets. The Naive Bayes classifier was the first method we used to check if the approval rating would be increasing or decreasing the day after Trump sent out a series of tweets. This was the first model we used because it can be trained very quickly, doesn’t require as much training data as other models, and is not very computationally intensive. 
Confusion Matrix:
28 27
14 25


### Random Forest:
The random forest is an ensemble learning method that works by constructing many decision trees on different subsets of features and taking the average results of all the decision trees. In this case, the feature it is creating the subsets on are the bag of words.  
Confusion Matrix:
47 8
36 3


### XGBoost:
The third model for supervised learning used is XGBoost. XGBoost is an optimized distributed gradient boosting system designed to be highly efficient, flexible.
Compared to the first two model, XGBoost performs better than randomforest but worse than naive bayes in terms of precision for class 1(0.448) and total accuracy(0.55). One nice feature that XGBoost has is to output feature importance as shown below where the most important features are displayed given their average impact on the approval rate. Some insights can be drawn from the chart below
![alt text](https://github.com/akalia25/Twitter_Influence_Analyzer/blob/master/Screenshots/XGBoostFeatureImportance-2.png)
Confusion Matrix:
39 16
26 13


## Conclusion
Clearly the models that were tested did not achieve the desired accuracy when attempting to predict Trump’s approval rating based on his tweets from the previous day. To improve the models, additional features are considered, such as number of likes and number of retweets for each tweet. A slight increase in the accuracy of each (supervised) prediction models has been noticed, indicating that the public attention on a certain tweet, as represented by the number of likes and retweets, has a slight impact on Trump’s public approval rating. 

Although Donald Trump is extremely active on Twitter, there are many other factors that need to be considered when discussing his approval rating. Some of these factors include his public behavior, his responses to criticism and things he has done as president. Another thing to consider is that Trump’s behavior one day may cause his approval rate to drop the following day, however it may be a few days until Trump decides to tweet about the issue. One final external factor that most likely accounted for the inaccuracy of the model is the behavior of other political figures. If other presidential candidates have a positive light shone on them in the media, this could cause the approval rating to drop for Trump. In addition, if someone on Trump’s team is caught in a scandal, or some other negative behavior, this would also likely cause the approval rating to drop.

Despite the relatively low accuracy of the models when predicting the approval rating, the k-means clusters gave much more insight. One hypothesis based on the word cloud was that words with similar frequencies were often tweeted together in the same tweets. For example, “news” and “fake”, as well as “obamacare” and “healthcare”. The k-mean clusters confirmed this hypothesis, because the aforementioned word groups were clustered together. These clusters also gave other insights, because the various clusters contain keywords that are often seen in media headlines such as “Trump Urges Russia to find Clinton’s Missing Emails” from CNN.

