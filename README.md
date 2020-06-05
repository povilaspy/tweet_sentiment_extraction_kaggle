# Kaggle Competition: Tweet Sentiment Extraction (2020 June)

[Official website for Kaggle TSE competition](https://www.kaggle.com/c/tweet-sentiment-extraction)

## Content

1. [Dataset](#dataset)
2. [Competition task](#task)
3. [Evaluation](#evaluation)
4. [Baseline](#baseline)
5. [Ideation](#ideation)
6. [Notebook: Twitter Sentiment Extraction](https://github.com/povilaspy/tweet_sentiment_extraction_kaggle/blob/master/kaggle_twitter_sentiment_extraction.ipynb)

## Dataset

train.csv, test.csv and sample_submission.csv are provided

### train.csv

27481 rows of tweets:

|   | textID  |  text |  selected_text | sentiment  |
|---|---|---|---|---|
| 0  | cb774db0d1  |  I\`d have responded, if I were going | I\`d have responded, if I were going  | neutral  |
| 1  | 549e992a42  | Sooo SAD I will miss you here in San Diego!!!  | Sooo SAD  | negative  |
| 2  | 088c60f138  | my boss is bullying me...  | bullying me	  | negative  |
| 3  | 9642c003ef  | what interview! leave me alone  | leave me alone		  | negative  |
| 4  | 358bd9e861  | Sons of ****, why couldn\`t they put them on t...  | Sons of ****, | negative  |

### test.csv

3534 rows of tweets:

|   | textID  |  text | sentiment  |
|---|---|---|---|
| 0  | f87dea47db  |  Last session of the day http://twitpic.com/67ezh | neutral  |
| 1  | 96d74cb729  | Shanghai is also really exciting (precisely -...  | positive  |
| 2  | eee518ae67  | Recession hit Veronique Branquinho, she has to... | negative  |
| 3  | 01082688c6  | happy bday!	 | positive |
| 4  | 33987a8ee5 | http://twitpic.com/4w75p - I like it!! | positive |

### sample_submission.csv

3534 rows of tweets:

|   | textID  |  selected_text |
|---|---|---|
| 0  | f87dea47db  |  NaN |
| 1  | 96d74cb729  |  NaN |
| 2  | eee518ae67  |  NaN |
| 3  | 01082688c6  |  NaN |
| 4  | 33987a8ee5 |  NaN |

## Task
Extract which words lead to the tweet sentiment label ('negative', 'neutral' or 'positive'). Return those in 'selected_text' column with submission file.

## Evaluation

Evaluation is based on Jaccard score, which shows similarity between two strings ('selected_text' in submission file and 'selected_text' in private test set file).

A Python implementation of Jaccard score is:

```python
def jaccard(str1, str2): 
    a = set(str1.lower().split()) 
    b = set(str2.lower().split())
    c = a.intersection(b)
    return float(len(c)) / (len(a) + len(b) - len(c))
```

Example described in Sanket Gupta's [blog post](https://towardsdatascience.com/overview-of-text-similarity-metrics-3397c4601f50):

* str1: AI is our friend and it has been friendly
* str2: AI and humans have always been friendly

<img src="https://miro.medium.com/max/926/1*u2ZZPh5er5YbmOg7k-s0-A.png">

* Jaccard similarity is calculated as the size of intersection divided by size of union of two sets.
* Performance of lemmatization to reduce words to the same root word is needed. That is “friend” and “friendly” will both become “friend”, “has” and “have” will both become “has”.
* Jaccard similarity for example above is 5/(5+3+2) = 0.5.

Source: [Overview of Text Similarity Metrics in Python](https://towardsdatascience.com/overview-of-text-similarity-metrics-3397c4601f50)

## Baseline

For the baseline we submit same 'text' as provided in test set without modifications:

```python
PATH = '/kaggle/input/tweet-sentiment-extraction/'
train = pd.read_csv(PATH + 'train.csv')
test = pd.read_csv(PATH + 'test.csv')
submission = pd.read_csv(PATH + 'sample_submission.csv')
submission['selected_text'] = test['text']
submission.to_csv("submission.csv", index=False)
```

This gives us Jaccard score of 0.594 which we will need to beat.

## Ideation

* Forecast positive/neutral/negative to match ground truth
* Extract tokens importance and return the string between first and last most important token
    * alternatively clean the tokens with lowest importance
    * for neutral comments, return full text

## Notebook: Twitter Sentiment Extraction

Notebook is available [here](https://github.com/povilaspy/tweet_sentiment_extraction_kaggle/blob/master/kaggle_twitter_sentiment_extraction.ipynb).
