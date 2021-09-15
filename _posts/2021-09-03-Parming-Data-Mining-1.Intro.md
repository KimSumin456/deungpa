---
title:  "[데이터마이닝] 1. An Introduction to Data Mining"
excerpt: "등록금 파먹기 - 데이터마이닝 파먹기 (Parming Data Mining)"

categories:
- 데이터마이닝
tags:
- 등록금 파먹기
- 데이터마이닝
- Introduction
---

## Overview
1. What is Data Mining? What is the class about?
2. Data Mining Tasks
3. Meaningfulness of Analytic Answers
4. The Traditional Data Mining Process
5. What Matters When Dealing with Data?
6. 수업

## 1. What is Data Mining? What is the class about?
### What is Data Mining?
What is Data Mining?
* Knowldge discovery from data.
* Extraction of actionable information from (usually) very large datasets, is the subject of extreme hype, fear, and interest.

### What is the class about?
What is the class about?
* To extract the knowledge data needs to be sotored, managed, and **analyzed**
* Emphasis on scale and unsupervised learning

## 2. Data Mining Tasks
Data Mining Tasks
* Descriptive methods
  * Find human-interpretable patterns that describe the data
  * ex) Clustering
* Predictive methods
  * Use some variables to predict unknown or future values of other variables
  * ex) Recommender systems

## 3. Meaningfulness of Analytic Answers
Meaningfulness of Analytic Answers
* ?

A risk with "Data mining" is that an analyst can "discover" patterns that are meaningless
* Statisticians call it Bonferroni's principle

An Example
* We want to find (unrelated) people who at least twice have stayed at the same hotel on the same day

## 4. The Traditional Data Mining Process
The Traditional Data Mining Process
1. Data Collection
2. Feature Extraction
3. Data Cleaning and Integration
4. **Analytical Processing** and Algorithms

## 5. What Matters When Dealing with Data?
Challenges
* Usage
* Quality
* Context
* Streaming
* Scalability

Data Modalities
* Ontologies
* Structured
* Networks
* Text
* Multimedia
* Signals

Data Operators
* Collect
* Prepare
* Represent
* Model
* REason
* Visualize

## 6. 수업
Data Mining: Clutures
* Data mining overlaps with
  * Databases: Large-scale data, simple queries
  * Machine Learning: (Small) data, Complex models
  * CS Theory: (Randomized) Algorithms
* Different cultures
  * To a DB person, data mining is an extreme form of **analytic processing** - queries that examine large amounts of data
    * Result is the query answer
  * To a ML person, data mining is the **inference of models**
    * Result is the parameters of the model
* In this class we will do both!

Data Mining In This Class
* Comvines best of machine learning, statistics, artificial intelligence, databases
* But more stress on Scalability, Algorithms, Computing Architectures, Real-World Applications

What will we learn?
* Mine different types of data
  * Data is high dimensional
  * Data is a graph
  * Time series (or longitudinal)
* Use different models of computation
  * Streams and online algorithms
  * Single machine in-memory
* Solve real-world problems
  * Recommender systems
  * Market basket analysis
  * ~~Spam detection~~
  * Duplicate document detection
  * Anomaly detection
  * Time series prediction
* Various Tools
  * Linear algebra (SVD, Rec. Sys., Communities)
  * Dynamic programming (frequent itemsets)
  * Hashing (Locality sensitive hashing (LSH), Bloom filters)
  * ~~Optimization (stochastic gradient descent)~~