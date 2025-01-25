# PRODIGYINFOTECH_DS_4

# Sentiment Analysis on Twitter Data

## Project Overview

This project involves performing sentiment analysis on social media data, specifically Twitter data, to understand public opinion and attitudes towards specific topics or brands. The analysis includes data cleaning, sentiment classification, and data visualization.

## Prerequisites

To run the code, you need the following Python libraries:
- pandas
- seaborn
- matplotlib
- textblob
- wordcloud

Install the necessary libraries using:

```bash
pip install pandas seaborn matplotlib textblob wordcloud
```

## Data Cleaning and Sentiment Analysis

1. **Extract ZIP File**:
   Extract the dataset from the given ZIP file (`sentiment analysis.zip`).

2. **Load Dataset**:
   Load the dataset from the extracted file (e.g., `twitter_training.csv`).

3. **Sentiment Analysis**:
   Use the TextBlob library to analyze and classify the sentiment of the tweets as positive, negative, or neutral.

4. **Data Visualization**:
   Visualize the sentiment distribution and trends over time using seaborn and matplotlib. Generate word clouds for positive sentiments.

## Sample Code

Here's a sample code snippet to get started:

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from textblob import TextBlob
from wordcloud import WordCloud

# Load dataset
data = pd.read_csv('/content/twitter_training.csv')

# Perform sentiment analysis
def analyze_sentiment(text):
    analysis = TextBlob(text)
    if analysis.sentiment.polarity > 0:
        return 'positive'
    elif analysis.sentiment.polarity == 0:
        return 'neutral'
    else:
        return 'negative'

data['sentiment'] = data['text'].astype(str).apply(analyze_sentiment)

# Visualize sentiment distribution
plt.figure(figsize=(8, 6))
sns.countplot(x='sentiment', data=data)
plt.title('Sentiment Distribution')
plt.show()

# Generate word cloud for positive tweets
positive_text = ' '.join(data[data['sentiment']=='positive']['text'])
wordcloud = WordCloud(width=800, height=400).generate(positive_text)
plt.figure(figsize=(10, 5))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis('off')
plt.title('Word Cloud for Positive Sentiments')
plt.show()
```

## Conclusion

This project provides valuable insights into public opinion and attitudes towards specific topics or brands through sentiment analysis and visualization.

---

Feel free to use and adapt this README file to suit your needs. If there's anything else you'd like to include or modify, let me know!
