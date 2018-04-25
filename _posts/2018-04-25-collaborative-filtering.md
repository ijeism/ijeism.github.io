
---
title: collaborative filtering
layout: post
categories: blog
---

## Introduction

Online platforms - whether they are retailers, newspapers, or social media networks – have one goal: to attract the maximum volume of traffic to increase their own revenues. One way of achieving that is to enrich users’ experience when searching for content. For this purpose, an extensive class of web applications has been developed to help predict user responses to specific options. Examples include offering movies to customers of movie streaming services based on prediction of viewers’ interests, or offering customers of an on-line retailer such as Amazon suggestions about what they might want to buy, based on their purchase history, product searches, or other peoples’ ratings. Such a facility is referred to as a recommendation system (Rajaraman & Ullman, 2012).

Recommender systems basically generate meaningful recommendations to specific users for items, such as music, products, movies, or new articles that might be of interest to them. They are based on so-called ‘information filtering’ techniques commonly used on e-commerce websites. The aim of this project is to demonstrate how Hadoop can be used to effectively manage the large volumes of data typically involved in recommendation problems. For this purpose, Amazon product ratings data is used, and a MapReduce approach presented to identify appropriate products to recommend particularly to new users.
2.	Problem description and key concepts

So how do we go about recommending items to users? Let us imagine a user visiting Amazon’s website for the first time with no record or prior purchase history - a so-called cold user (Son, 2016). We could simply identify the most popular items on the website and recommend them to the new visitor. But this approach is rather static in nature and would not provide sufficient depth for personalization since it does not attempt to identify individual users’ interests or preferences in any way. How, then, can we ensure increased accuracy of recommendations when a user is new and there may be insufficient information to base a recommendation on? One way is to group items that are bought and preferred similarly by users and recommend items based on similarity to the other items in that group. 

2.1.	Preference and similarity
Similarity here is determined by an expression of a level of preference by other users for a particular item, which can be computed using simple similarity measures, such as Cosine Similarity, Pearson Correlation, Jaccard Similarity, etc., to group similar items together (Somani, 2015). A user of Amazon.com can express her opinion by rating items purchased, which we will use as a representation of users' indication of preference for items.

2.2.	Item-based Collaborative Filtering
There are two basic architectures for a recommendation system: i. content-based systems, focusing on properties of items; and ii. collaborative-filtering systems, focusing on the relationship between items and users (Rajaraman & Ullman, 2012). In this project, we focus on the quite popular collaborative filtering technique. 

Since our project focuses on a recommender system able to deal with new users, we look at the Item-based Collaborative Filtering approach – a specific type of collaborative filtering system that focuses on the similarity of user ratings for two items to identify items to recommend to new users (Rajaraman & Ullman, 2012). It finds relationships between the new user’s interests (e.g. an item she is looking at) and existing user ratings of that particular item and other items in order to determine useful recommendations for the new user. The basic idea we are exploring is: If a new Amazon.com visitor is viewing a particular product, what other products might be similar to that product? If she liked a particular product, what other products, that she might not have come across yet, seem similar based on peoples’ ratings?

2.3.	A big data problem
The large number of users and items are the main driving force behind recommendation systems, as they cannot provide relevant and effective recommendations without sufficient data supplying plenty of user data such as past purchases and associated ratings (Pal, 2015). In addition, recommendation system techniques involve finding items that are similar to an item a user is interested in. This requires computation of similarity metrics for all pairs of items considered, which presents a very large computational problem considering the number of products available at big online-retailers like Amazon. For this reason, it is practical to handle this type of problem using the divide and conquer pattern provided by the MapReduce framework. 

MapReduce is a programming model used in Hadoop - a framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models - designed to process large volumes of data (White, 2015). Using the Hadoop Distributed File System (HDFS), data stored across a cluster of machines can be processed quickly and in parallel, by dividing a task into a set of independent sub-tasks, each performing the same type of computation (Radtka & Miner, 2016; White, 2015). MapReduce scales well to many thousands of nodes and can handle very large amounts of data – as required for recommendation problems. 
