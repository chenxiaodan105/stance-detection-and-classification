# Xiaodan's Directory

## Contents
[1. Text Preprocessing](#Text-Preprocessing)

[2. Imbalance Data Handling](#Imbalance-Data-Handling)

[3. Negation Handling](#Negation-Handling)

[4. Methods](#Methods)

[5. Grid Search](#Grid-Search)


## Text Preprocessing
* tokenization
```
def tokenize_text(text):
    tokens = word_tokenize(text.lower())
    tokens = [token.strip() for token in tokens]
    return tokens
```
* remove punctuation
```
def remove_special_characters(text):
    tokens = tokenize_text(text)
    pattern = re.compile('[{}]'.format(re.escape(string.punctuation)))
    filtered_tokens = filter(None, [pattern.sub('', token) for token in tokens])
    filtered_text = ' '.join(filtered_tokens)
    return filtered_text
```
* remove words that are not purely alphabetic words
```
def remove_non_alphabetic_characters(text):
    tokens = tokenize_text(text)
    tokens = [w for w in tokens if w.isalpha()]
    return ' '.join(tokens)
```
* remove stopwords
```
def remove_stopwords(text):
    stop = list(set(stopwords.words('english')))
    tokens = tokenize_text(text)
    filtered_tokens = [token for token in tokens if token not in stop]
    filtered_text = ' '.join(filtered_tokens)
    return filtered_text
```
* remove all words that have a length <= 1 characters (this number can be changed)
```
def remove_tokens_with_frequency(text,count):
    tokens = tokenize_text(text)
    tokens = [w for w in tokens if len(w)>count]
    return ' '.join(tokens)
```
* stemming and lemmatization

## Imbalance Data Handling
* smote 
* balanced ensemble method using SVM or decision tree as base model
* [reference](https://imbalanced-learn.org/en/stable/ensemble.html)

## Negation Handling
* for a specific speech, parse the key sentence using spacy
* find both the scope and the key word in the sentence
* within the scope, count the number of the negation words, if it's even, it's not a negation, if it's odd, it's a negation

## Methods
* stance detection

| method |  F1 score(majority) | F1 score(minority) |
| ----------- | ----------- | ----------- | 
| bow + svm |  |
| tfidf + svm | |
| bow + random forest | |
| tfidf + random forest | |
| bow + BalancedBaggingClassifier | |
| tfidf + BalancedBaggingClassifier | |
| glove + CNN | |
| word2vec + lstm | |
| word2vec + BiLSTM + encoding | |


* stance classification

| method |  F1 score(majority) | F1 score(minority) |
| ----------- | ----------- | ----------- | 
| bow + svm |  |
| tfidf + svm | |
| bow + random forest | |
| tfidf + random forest | |
| bow + BalancedBaggingClassifier | |
| tfidf + BalancedBaggingClassifier | |
| glove + CNN | |
| word2vec + lstm | |
| word2vec + BiLSTM + encoding | |


## Grid Search
* grid search for tfidf and bow, including ngram, max_df, min_df, stop_words, max_features, etc.
* grid search for machine learning models(LR, SVM, random forest, naive bayes)







