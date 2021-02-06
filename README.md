# Hypothesis-Text-Classification

  

Extraction of explicit statements of hypotheses or propositions from set of 139 scientific/academic research documents on business in PDF using Natural language processing (NLP) models.

  

Typically, hypotheses or propositions are expressed in the following form in the PDFs:

  

Hypothesis 1: X is positively related to Y.

H1a: A would increase B.

Proposition 1A: The higher the i, the lower the j.

  

# Requirements
* The Hypothesis_Text_Classification_NLP.ipynp Jupiter Notebook file can be run on Google Colab or Jupiter Notebook

* The scientific/academic research documents used in the project can be downloaded from [dropbox](https://www.dropbox.com/sh/q49mnn6i575b8nh/AAByLkuQuU4RLJ44o0i-Fiuma?dl=0).

* Download punkt nltk package

```sh

$ nltk.download('punkt')

```

* Install fastext

```sh

$ pip install fasttext

```

* Install pdfminer

```sh

$ pip install pdfminer

```

  

## Import the following required packages where needed in the Jupiter Notebook file


- import pandas as pd
- import numpy as np
- from google.colab import drive
- import nltk
- from nltk import word_tokenize, FreqDist
- from nltk.tokenize import sent_tokenize
- import sys
- import io
- import glob, os
- import re
- import codecs
- import warnings
- from sklearn.feature_extraction.text import TfidfTransformer
- from sklearn.feature_extraction.text import CountVectorizer
- from sklearn.naive_bayes import MultinomialNB
- from sklearn.model_selection import train_test_split
- import fasttext
- import csv

  

# Steps

  

**Step 1:** Parse the text data from PDFs using pdfminer and save it into text files with name same as PDF file.

**Step 2:** Create text_files_dict python dictionary with key: filename, value: text extracted from PDF

**Step 3:** Clean the text extracted from PDF by removing sentences with irrelevant strings and marking Hypothesis sentences with '<split>Hypo {}:' using regex

**Step 4:** Extract the Hypothesis like sentences from the above cleaned sentences and create a Hypothesis dataframe with Paper ID, Hypothesis/Proposition # and Hypothesis/Proposition Full Sentence

**Step 5:** Create a CSV file from the above dataframe. This CSV can be manually processed to contain only true Hypothesis sentences. For now use the Hypothesis like sentences from the dataframe.

**Step 6:** Similarly extract Non Hypothesis sentences equal in number with Hypothesis Sentences from the above cleaned sentences and create a Non Hypothesis dataframe with sentence and classification columns to use in NLP models like Naive Bayes and FastText for faster text classification.

**Step 7:** Combine the Hypothesis and Non Hypothesis dataframes into hypothesis_classification dataframe with sentence and classification columns. sentence column contains both Hypothesis and Non Hypothesis sentences, and classification column contains Hypothesis and Non_Hypothesis labels.

**Step 8:** Split the hypothesis_classification dataframe into training data(90%) and test data(10%).

**Step 9:** Perform Text Classification with various NLP models and choose the best one with good speed and accuracy.

  

# Text Classification Model Metrics

1) Naive_Bayes Model accuaracy - 82.61%

2) FastText Model accuracy - 97.4%
