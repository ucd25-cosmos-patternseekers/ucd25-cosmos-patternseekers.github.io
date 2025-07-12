---
title: "Movie Clustering"
date: 2025-07-11
---

> Webpage is still a WIP

## The Question

> *How can we recommend movies based on similarity?* 

## Exploratory Data Analysis
![](movie-eda.png)

## Dimension reduction
![](movie-tsne.png)
Note: We dropped the original *"cluster"* column in the dataset. The tSNE dimension reduction did not get to use given clustering data. For this reason, this graph may look different, less clustered, than other groups'.

## Clustering
![](movie-clustering.png)

## Cluster interpretation

![](movie-bars.png)
- Cluster 1 is drama and romance movies
- Cluster 2 is lighthearted comedy and sci fi movies
- Cluster 3 is dramatic action movies
- Cluster 4 is horror movies
