# Yahoo Finance Stock News Sentiment Analysis
Yahoo Finance stock news web scraper and sentiment analysis.


### [1] Description
For a chosen stock, this function searches Yahoo Finance for the latest news and gets the latest sentiment (individual + overall) using a trained model.


### [2] Use Case
From this application, users will be able to predict the expected overall sentiment of a particular stock in a relatively short amount of time based on the textual sentiment of financial experts. Users can then base their investment decisions on sound financial advice without spending hours skimming through financial news. Note, however, that this is meant to assist and not replace the human element of investing.


### [3] Repository Contents
1) SA Training Data.csv<br>
CSV file containing a corpus of 100 articles and their corresponding sentiment labels manually curated from Yahoo Finance. The sentiment analysis model was trained using these articles.

2) Stock Ticker Symbol Scraping.ipynb<br>
Utility Jupyter notebook used to scrape all the stock ticker symbols available on Yahoo Finance. Executing this file produces "scraped_tickers.csv" (an exported CSV file containing scraped tickers from a stock ticker symbol website) and "name2ticker_dict.pkl" (a dictionary mapping stock names to their respective ticker symbols).

3) Yahoo Finance Sentiment Analysis (Final).ipynb<br>
The main file that demonstrates the web scraping and sentiment analysis model. It also contains in-depth information detailing the model.

4) Yahoo Finance Sentiment Analysis Model Training.ipynb<br>
Utility Jupyter notebook used to train the sentiment analysis model. The model is trained on the Maximum Entropy classifier model from the NLTK package. When executed, this file produces "maxent_sentiment_classifier.pkl" (trained model object) and "dictionary.pkl" (gensim dictionary object), which were used in "Yahoo Finance Sentiment Analysis (Final).ipynb".

5) dictionary.pkl<br>
Saved Gensim dictionary object that enables the sentiment analysis model to work.

6) maxent_sentiment_classifier.pkl<br>
Saved trained model object to be used in the sentiment analysis model.

7) name2ticker_dict.pkl<br>
A saved Python dictionary object mapping stock names to their respective ticker symbols. This object was used to enable the sentiment analysis function to distinguish between stock names and ticker symbols interchangeably.  

8) scraped_tickers.csv<br>
CSV list of stock names and their respective ticker symbols scraped from a stock ticker symbol website.


### [4] How the Project Works
The sentiment analysis project can be split into 3 sub-processes. These sub-processes are contained and defined in "Yahoo Finance Sentiment Analysis (Final).ipynb".

1) Web Scraping (WebScraper class)<br>

For a particular stock, the function scrapes Yahoo Finance for news on that stock using Python's BeautifulSoup4 package. It first scrapes the webpage for all news article URLs relating to that stock and stores them into a list. Subsequently, the function scrapes each URL for its headline and body of text and stores them into another list.

2) Training the sentiment analysis model (SentimentAnalyzer class)<br>

The sentiment analysis model was trained using the Maximum Entropy classification model from Python's NLTK and Gensim packages. To train the model, we curated 100 news articles from Yahoo Finance and manually categorized them into their overall sentiment toward a particular stock, consisting of 34 optimistic, 33 neutral, and 33 pessimistic articles. We then trained the classifier model based on these 100 curated labelled articles to recognize and classify new unseen news articles into these 3 categories. After training, the model was saved using Python's pickle package.

3) Combining the scraped articles and sentiment analysis model into a sentiment analysis application (StockSentimentApp class)<br>

The scraped articles and trained sentiment analysis model are combined and developed into a sentiment analysis application. The application takes in a ticker symbol as its input and outputs the sentiment of each scraped article. It does this by applying the trained classifier model to each news article stored in the corpus of scraped articles. The headline and hyperlink of each article are also shown in the output to enable the user to click and read each article if they are interested. Furthermore, the function summarizes and outputs the overall sentiment toward the stock based on the count of each predicted sentiment.


### [5] How to Use
In "Yahoo Finance Sentiment Analysis (Final).ipynb", run all the cells. When prompted, key in a stock name or ticker symbol (e.g., "Amazon" or "AMZN"; the input is case-insensitive). The function will then output a list of articles and their corresponding predicted sentiments.


### [6] Disclaimer
The sentiment analysis model was trained based on the Maximum Entropy model, which is a probabilistic model that chooses the model with the highest entropy from a set of models that fit training data. It's based on the principle of maximum entropy and information theory. Because of this, certain articles that talk about multiple stocks or companies may result in inaccurate sentiment predictions.

### [7] Author
Martin Cheng
