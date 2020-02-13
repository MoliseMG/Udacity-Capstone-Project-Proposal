# Machine Learning Engineer Nanodegree

## Capstone Proposal
## Real or Not? NLP with Disaster Tweets Challenge (Kaggle Competition)

Molise Molefi  
January 16th, 2020

## Proposal
### Domain Background
Twitter is a 'microblogging' system that allows people to send and receive short posts called tweets. It is a platform to connect with people and catch on on everything that is happening around us, either be the news, emergencies, blogs and many more. This provides and encourages communication between multiple parties and also informs the public about events that are around them and that may affect them.

Twitter has approximately over 126 million daily users worldwide. 6,000 tweets are tweeted every second, which corresponds to over 350,000 tweets sent per minute, 500 million tweets per day and around 200 billion tweets per year. Due to the high usage of Twitter and the ubiquitousness of smartphones, Twitter has become an important communication channel in times of emergency. People prefer to announce an emergency they’re observing in real-time on Twitter because their posts can reach many people instantly on Twitter. Because of this, more agencies are interested in programmatically monitoring Twitter for disasters(i.e. disaster relief organizations and news agencies).But, it’s not always clear whether a person’s words are actually announcing a disaster.

Automatic identification of useful tweets is a challenging task because: (i) tweets are short – only 140 characters– and therefore, hard to understand without enough context;(ii) they often contain abbreviations, informal language,spelling variations and are ambiguous; and, (iii) judging a tweet’s utility is a subjective exercise. Despite advances in natural language processing (NLP), interpreting short informal texts automatically remains a hard problem (Nguyen et al. 2017).

### Problem Statement
The goal of this project is to predict which tweets are about real disasters and which one’s aren’t. To solve the problem, I am going to use Natural Language Processing and Machine Learning techniques to develop a model that can classify real disasters from unreal ones. 

### Datasets and Inputs
This dataset was created by the company figure-eight and originally shared on their ‘Data For Everyone’ website. It contains three .csv files which are:
* **train.csv** - the training set
* **test.csv** - the test set
* **sample_submission.csv** - a sample submission file in the correct format

1. Train.csv and Test.csv Column names
  * id - a unique identifier for each tweet
  * text - the text of the tweet
  * location - the location the tweet was sent from (may be blank)
  * keyword - a particular keyword from the tweet (may be blank)
  * target - in train.csv only, this denotes whether a tweet is about a real disaster (1) or not (0)

2. Train.csv
* Number of columns: 5
* Number of rows: 7614

3. Test.csv
* Number of columns: 5
* Number of rows: 3264

4. Sample_submission.csv
* The file is not important for the current project because it is used for model evaluation.


The datasets can be found at Kaggle by following this [link](https://www.kaggle.com/c/nlp-getting-started/data)

### Solution Statement
The proposed solution to this problem is to apply Machine learning and Natural Language Processing techniques to process and classify the data(tweets) as **Real Disaster** or **Unreal Disaster**.

Firstly, the tweets will be converted to lower case and tokenized into words. Then form a wordcloud based on the most occuring words. All tweets will be converted to numbers by using the index of the words in the WordCloud.
Because we are dealing with a classification problem, either RNN or XGBoost model will be used for classification of tweets as real and unreal disasters.

After training the model we are going to use the evaluation metrics described in later sections to analyse the performance of the model.

### Benchmark Model
Due to the fact that the train and test datasets have both features and labels, this is a supervised learning problem. Tree based models have proven to be the best when it comes to classification. Using CatBoost and Extreme gradient boost (XGBoost) for a benchmark will be a very good idea. I'll try to beat the benchmark by building an Ensemble model that consists of CatBoost, LightGBM and XGBoost. Also, I'll tune hyperparameters to incease the overall model accuracy.

### Evaluation Metrics
Prediction results are going to be evaluated using F1 score between the predicted and expected answers. F1 which is a function of Precision and Recall that is used to test the accuracy of the model. It considers both the precision _p_ and the recall _r_ of the test to compute the score: _p_ is the number of correct positive results divided by the number of all positive results returned by the classifier, and _r_ is the number of correct positive results divided by the number of all relevant samples (all samples that should have been identified as positive). If The model has F1 score that is close to 1 then it is accurate.

### Project Design

**Data Exploration**
* Load libraries
* Load train and test datasets
* Look at the shape of the data
* Statistical Summary

**Data Preprocessing**
* Drop keyword and location columns
* Remove noise such as '@user' and hashtags from all tweets
* Tokenize the tweets into words
* Remove stopwords from tweets
* Stem the tokens (i.e Using PorterStemmer)
* Produce a word dictionary
* Convert every word to an integer value using a vocabulary

**Data Splitting**
* Provided data is already split into test and training datasets

**Model Training and Evaluation**
* Build an ensemble model that consists of three models being catboost, LightGBM and XGBoost model.
* Select the best ensemble model based on accuracy after hyper-parameter tuning.

### Reference
[1] Accuracy, Precision, Recall or F1? [TowardsDataScience](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)  
[2] F1 score [Wikipedia](https://en.wikipedia.org/wiki/F1_score)  
[3] Real or Not? NLP with Disaster Tweets [Kaggle](https://www.kaggle.com/c/nlp-getting-started/overview/description)  
[4]Twitter keeps losing monthly users, so it’s going to stop sharing how many [TheVerge](https://www.theverge.com/2019/2/7/18213567/twitter-to-stop-sharing-mau-as-users-decline-q4-2018-earnings)  
[5] The Number of tweets per day in 2019 [Dsayce](https://www.dsayce.com/social-media/tweets-day/)    
[6]Nguyen, Mannai, Joty, Sajjad et al. "Robust Classification of Crisis-Related Data on Social Networks Using Convolutional Neural Networks." Qatar Computing Research Institute. 2017
