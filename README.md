# Kaggle Competition: Tweet Sentiment Extraction (2020 June)

[Official website for Kaggle TSE competition](https://www.kaggle.com/c/tweet-sentiment-extraction)

## Content

1. [Dataset](#dataset)
2. [Competition task](#task)
3. [Evaluation](#evaluation)

## Dataset

train.csv, test.csv and sample_submission.csv are provided

### train.csv

27481 rows of tweets:

|   | textID  |  text |  selected_text | sentiment  |
|---|---|---|---|---|
| 0  | cb774db0d1  |  I`d have responded, if I were going | I`d have responded, if I were going  | neutral  |
| 1  | 549e992a42  | Sooo SAD I will miss you here in San Diego!!!  | Sooo SAD  | negative  |
| 2  | 088c60f138  | my boss is bullying me...  | bullying me	  | negative  |
| 3  | 9642c003ef  | what interview! leave me alone  | leave me alone		  | negative  |
| 4  | 358bd9e861  | Sons of ****, why couldn`t they put them on t...  | Sons of ****, | negative  |

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




