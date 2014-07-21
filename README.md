---
tags: API, cocoapods
languages: objc
---

# Tweet Sentiment

Let's find out how The Flatiron School is doing on Social Media. We'll need two APIS to do this. One to get the tweets, and another to do what's called [sentiment analysis](http://en.wikipedia.org/wiki/Sentiment_analysis).

## Instructions

  1. Create a new project and install the [STTwitter](https://github.com/nst/STTwitter) CocoaPod. 
  2. Do the appropriate method call to get all tweets with the query `FlatironSchool`. You can use my App Key/Secret and use Twitter App Only Authentication.

  ```
  Key: GOOcJSI2VC9DajNOvM5oI8oXx
  Secret: nrczlQ0yJmwEDUqEsBta6yX8akhJARglJXTPJe6UuiaC1uWaCq
  ```

  3. Once you have the tweets. Send each tweet for sentiment analysis via [The Sentiment 140 API](http://help.sentiment140.com/api). This returns a polarity value of 0 for negative, 2 for neutral and 4 for positive. Technically, we are supposed to use the Bulk Classification Service, but it's a bit confusing. I'd just use the Simple Classification Service. The Simple Classification Service requires a key you can use my email `joe@flatironschool.com` as the key. For both the `query` and the `text` key you will need to [URL encode](http://en.wikipedia.org/wiki/Percent-encoding) the `NSString` values. You can do this relatively simply with this code:

  ```
  NSString *unescaped = @"RT @RRombom: My answer to How successful are code bootcamps, like Dev Bootcamp and @FlatironSchool at job placement? http://t.co/dtkVA3rYkK";
  NSString *escapedString = [unescaped stringByAddingPercentEncodingWithAllowedCharacters:[NSCharacterSet URLHostAllowedCharacterSet]];
  NSLog(@"escapedString: %@", escapedString);
  ```

  4. Your App should have just a label. When the app loads, it should request all of the tweets mentioning `FlatrionSchool` and then give an average sentiment for the term `FlatironSchool` displayed in the label.
