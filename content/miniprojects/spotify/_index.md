---
title: "Song Popularity Analysis"
date: 2025-07-11
author: Wisdom Li
---

# Topic

> ***How can we determine the popularity of a song/album given its features (duration, danceability, loudness, tempo, etc)?***

## Hypothesis

By training a machine learning model through various input features, we can predict the target variable, popularity. Popularity is on a scale between 0-100, with 0 being the least popular and 100 being the most popular song.

## Data Acquisition

We used the spotify tracks [dataset](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset) found on Kaggle. The file contained 114,000 rows of different songs with 20 columns.

## Data Preprocessing

After dropping columns that had minimal correlation to popularity, since most models only accepted numerical inputs, we created a pipeline to impute missing values and one hot encode categorical values. We ended up using 14 features (duration_ms, explicit, danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, and time_signature) to create the machine learning model. 

## Exploratory Data Analysis

Before running the model, we explored the dataset to gain deeper insights. We found that the average song popularity is 33, with a standard deviation of 22. This means that the popularity of songs in the file can widely differ from one another. Afterwards, we used various plots to explore the data further. 
