This is code that analyses sentiment from tweets that can be pulled from Twitter
The current version of the code uses a small selection of mock data to display basic output.

The code below shows how to to set up and authenticate the Twitter API and then gives a function to fetch tweets.

# Set up Twitter API keys
consumer_key = 'YOUR_CONSUMER_KEY'
consumer_secret = 'YOUR_CONSUMER_SECRET'
access_token = 'YOUR_ACCESS_TOKEN'
access_token_secret = 'YOUR_ACCESS_TOKEN_SECRET'

# Authenticate with the Twitter API
auth = tweepy.OAuth1UserHandler(consumer_key, consumer_secret, access_token, access_token_secret)
api = tweepy.API(auth)

# Function to fetch tweets
def fetch_tweets(keyword, count=100):
    tweets = tweepy.Cursor(api.search_tweets, q=keyword, lang='en').items(count)
    tweet_list = [[tweet.text, tweet.created_at] for tweet in tweets]
    df = pd.DataFrame(tweet_list, columns=['Tweet', 'Timestamp'])
    return df

    
