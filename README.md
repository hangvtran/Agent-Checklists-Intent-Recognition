# Agent-Checklists-Intent-Recognition
Multi classification model to predict workflow and guide customer service agents based on customer utterances, using natural language processing (NLP) models and determine if an agent has completed the action

## Overview
Manual surveys conducted by agents is a prolonged and inefficient process that results in a significant amount of time spent by call center phone agents researching customer data and utilizing knowledge bases, guides and FAQ information. To improve this situation, it is important to find solutions that will enhance customer satisfaction by reducing wait times and ensuring that agents are able to identify the most effective workflow for each client.

## Objective
Our objective is to predict the appropriate workflow an agent must go through to solve a client’s issue, in order to assess whether or not the agent successfully used the predicted workflow.

## Dataset
- Action-Based Conversations Dataset (ABCD): Over 10K human-to-human dialogues with 96 distinct workflows
- A list of conversations, where each conversation is a dict containing:
    convo_id: a unique conversation identifier
    scenario: details about the customer setup along with the underlying flow
    original: the raw conversation of speaker and utterances as a list of tuples

## Steps
To prepare the text data for the model building we perform text preprocessing
Some of the preprocessing steps are:
- Removing punctuations 
- Removing URLs
- Removing Stop words
- Lower casing
- Tokenization
- Stemming
- Lemmatization


## Technologies and libraries used
- Programming language : Python3
- Data science libraries : pandas, numpy, matplotlib, seaborn
- Machine Learning Library : sklearn
- Runtime Environment : Google Colab and Kaggle Notebook
- Training Algorithms : 3 basic methods and 3 ensemble methods are used.
    * Base line: Dummy Classifier
    * Basic methods: Logistic Regression / Decision Tree / Naive Bayes Classifier
    * Ensemble methods : Random Forest / XGBoost(Extreme Gradient Boosting) / Stacking (Logistic Regression + RandomForest + XGBoost)


## Notebook — Complete step by step execution
>> Google Colab : https://colab.research.google.com/drive/1Y3mG8sqZEbdTcG9SFmGOdgqi30xLdsgV

## Summary
[![Model-Comparison.png](https://i.postimg.cc/6psGxxCk/Model-Comparison.png)](https://postimg.cc/Whn40KW8)

### Model Evaluation: Accuracy
[![Evaluation-Accuracy.png](https://i.postimg.cc/nLFrnFrP/Evaluation-Accuracy.png)](https://postimg.cc/JsFMqWbN)
- Accuracy Score: Logistic Regression, Stacking > XGBoost > Random Forest >Naive Bayes > Decision Tree
- Logistic regression and Stacking model performs the best with accuracy score 0.88

### Model Evaluation: Time Efficiency
[Evaluation-Time-Efficiency.png](https://postimg.cc/tnRTsG0L)
- Run time: Naive Bayes < Random Forest < Decision Tree < Logistic Regression < XGBoost < Stacking
- Stacking model is significantly inefficient in terms of run time ( total:2940 sec, 0.33 sec/convo) 

### Model Evaluation: Overfitting
[![Evaluation-Overfitting.png](https://i.postimg.cc/0jRzSL9g/Evaluation-Overfitting.png)](https://postimg.cc/sQmfdHBK)
- Logistic regression works good for both training data and test data.
- Random Forest , XGBoost, Stacking possibly overfitted


## Conclusion

### Logistic Regression
> Performs the best in terms of three category of evaluation
    - Accuracy:  0.88
    - Time efficiency:  total runtime: 19 sec, 0.02/conversation
    - Not overfitted

### Models with ensemble method
> Perform relatively better than basic models with regards to accuracy score
> Requires more runtime because of their complicated algorithm
> Random Forest model can be the second best model 
    - Accuracy: 0.86
    -Time efficiency: total runtime:  3 sec, 0.0003/conversation
> Stacking shows stable score for all over Precision, Recall, F-1 score, accuracy but very time consuming 



