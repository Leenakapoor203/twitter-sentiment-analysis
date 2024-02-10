WHAT IS SENTIMENTAL ANALYSIS

- Sentiment Analysis is the process of ‘computationally’ determining whether a piece
of writing is positive, negative or neutral.

- It’s also known as opinion mining, deriving the opinion or attitude of a speaker.
  
- Sentiment Analysis is the process of determining whether a piece of writing
(product/movie review, tweet, etc.) is positive, negative or neutral. It can be used to
identify the customer or followers attitude towards a brand through the use of             
variables such as context, tone, emotion, etc. Marketers can use sentiment analysis to
research public opinion of their company and products, or to analyze customer
satisfaction. Organizations can also use this analysis to gather critical feedback about
problems in newly released products.

- Sentiment analysis not only helps companies understand how they’re doing with their
customers, it also gives them a better picture of how they stack up against their
competitors. For example, if your company has 20% negative sentiment, is that bad?
It depends. If your competitors have a roughly 50% positive and 10% negative
sentiment, while yours is 20% negative, that merits more discovery to understand the
drivers of these opinions. Knowing the sentiments associated with competitors helps
companies evaluate their own performance and search for ways to improve.

MAIN LIBRARIES USED

1.TWEEPY
Introduction
- Tweepy is a Python library for accessing the Twitter API. It is great for simple automation and
creating twitter bots. Tweepy has many features.
Hello Tweepy
- import tweepy
- auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
- auth.set_access_token(access_token, access_token_secret)
- api = tweepy.API(auth)
- public_tweets = api.home_timeline()
- for tweet in public_tweets:
- print(tweet.text)
This example will download your home timeline tweets and print each one of their texts to
the console. Twitter requires all requests to use OAuth for authentication. The Authentication
Tutorial goes into more details about authentication.

- API

- The API class provides access to the entire twitter RESTful API methods. Each method can
accept various parameters and return responses. For more information about these methods
please refer to API Reference.
Models

- When we invoke an API method most of the time returned back to us will be a Tweepy
model class instance. This will contain the data returned from Twitter which we can then use
inside our application. For example the following code returns to us an User model:
- Get the User object for twitter...
- user = api.get_user(&#39;twitter&#39;)
- Models contain the data and some helper methods which we can then use:
- print(user.screen_name)
- print(user.followers_count)
- for friend in user.friends():
- print(friend.screen_name)



2.TEXTBLOB : 

TextBlob is a Python (2 and 3) library for processing textual data. It provides a simple API for
diving into common natural language processing (NLP) tasks such as part-of-speech tagging,
noun phrase extraction, sentiment analysis, classification, translation, and more..TextBlob
stands on the giant shoulders of NLTK and pattern, and plays nicely with both.
Features

- Noun phrase extraction
- Part-of-speech tagging
- Sentiment analysis
- Classification (Naive Bayes, Decision Tree)
- Language translation and detection powered by Google Translate
- Tokenization (splitting text into words and sentences)
- Word and phrase frequencies
- Parsing
- Word inflection (pluralization and singularization) and lemmatization
- Spelling correction
- Add new models or languages through extensions
- WordNet integration

3.MATPLOTLIB:

Matplotlib is an amazing visualization library in Python for 2D plots of arrays. Matplotlib is a
multi-platform data visualization library built on NumPy arrays and designed to work with
the broader SciPy stack. It was introduced by John Hunter in the year 2002.
One of the greatest benefits of visualization is that it allows us visual access to huge amounts
of data in easily digestible visuals. Matplotlib consists of several plots like line, bar, scatter,
histogram etc.


PROBLEM STATEMENT AND APPROACH

The problem in sentiment analysis is classifying the polarity of a given text at the
document, sentence, or feature/aspect level .
whether the expressed opinion in a document, a sentence or an entity feature/aspect is
positive, negative, or neutral

SOLUTION APPROACH

- We follow these 3 major steps in our program:
- Authorize twitter API client.
- Make a GET request to Twitter API(TWEEPY) to fetch tweets for a particular query.
- Parse the tweets. Classify each tweet as positive, negative or neutral.

PROCEDURE

Authentication:
In order to fetch tweets through Twitter API, one needs to register an App through their
twitter account. Follow these steps for the same:
- Open this link and click the button: ‘Create New App’
- Fill the application details. You can leave the callback url field empty.
- Once the app is created, you will be redirected to the app page.
- Open the ‘Keys and Access Tokens’ tab.
- Copy ‘Consumer Key’, ‘Consumer Secret’, ‘Access token’ and ‘Access Token
Secret’.

APPROACH:
- First we create a TwitterClient class. This class contains all the methods to interact
with Twitter API and parsing tweets..
- In get_tweets function, to call the Twitter API to fetch tweets
- fetched_tweets = self.api.search(q = query, count = count)
- In get_tweet_sentiment we use textblob module.
- analysis = TextBlob(self.clean_tweet(tweet))
- call clean_tweet method to remove links, special characters, etc. from the tweet using
some simple regex.
Then, pass tweet to create a TextBlob object, following processing is done over text
by textblob library:
- Tokenize the tweet ,i.e split words from body of text.
- Remove stopwords from the tokens.(stopwords are the commonly used words which
are irrelevant in text analysis like I, am, you, are, etc.)
- Do POS( part of speech) tagging of the tokens and select only significant
features/tokens like adjectives, adverbs, etc.
- Pass the tokens to a sentiment classifier which classifies the tweet sentiment as
positive, negative or neutral by assigning it a polarity between -1.0 to 1.0 .
- Positive and negative features are extracted from each positive and negative review
respectively.
- Training data now consists of labelled positive and negative features. This data is
trained on a Naive Bayes Classifier
- Then, we use sentiment.polarity method of TextBlob class to get the polarity of
tweet between -1 to 1.
Then, we classify polarity
- Finally, parsed tweets are returned. Then, we can do various type of statistical
analysis on the tweets. For example, in above program, we tried to find the percentage
of positive, negative and neutral tweets about a query.
- Polarity is classified as:
- if analysis.sentiment.polarity &gt; 0:
return &#39;positive&#39;
elif analysis.sentiment.polarity == 0:
return &#39;neutral&#39;
else:
return &#39;negative&#39;
 

