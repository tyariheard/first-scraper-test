# first-scraper-test
METHOD 1

import configparser config = configparser.RawConfigParser() 
config.read(filenames = '/path/twitter.txt')

!pip install tweepy import tweepy as tw

accesstoken = config.get('twitter','accesstoken') 
accesstokensecret = config.get('twitter','accesstokensecret') apikey = config.get('twitter','apikey') apisecretkey = 
config.get('twitter','apisecretkey')

auth = tw.OAuthHandler(apikey,apisecretkey) 
auth.set_access_token(accesstoken,accesstokensecret) 
api = tw.API(auth,wait_on_rate_limit=True)

search_word = 'checkin' date_since = '2020-12-16'

tweets = tw.Cursor(api.search,q = search_word, lang ='en',since = date_since).items(1000)

tweet_details = [[tweet.geo,tweet.text,tweet.user.screen_name,tweet.user.location]for tweet in tweets]
