---
title:  "[데이터마이닝] 3. Data Preparation"
excerpt: "등록금 파먹기 - 데이터마이닝 파먹기 (Parming Data Mining)"

categories:
- 데이터마이닝
tags:
- 등록금 파먹기
- 데이터마이닝
- Data Preparation
---

## Overview
0. Motivation: Data Types and Variations of Problems
1. Feature Extraction and Portability
2. Data Cleaning
3. Data Reduction and Transformation
4. Summary

## 0. Motivation: Data Types and Variations of Problems
Problem
* Time series
* Spatial
* Sequence
* Networks

Method
* Patterns
* Clustering
* Outliers
* Classification

데이터와 문제의 종류에 따라 그에 맞는 분석 방법이 다릅니다. 따라서 어떻게 데이터를 전처리하고 사용할 것인지를 잘 정하는 것이 중요합니다.

## 1. Feature Extraction and Portability
Feature Extraction
* 그림 참고
* Domain - Raw Data - Features

Data Type Portability
* 데이터는 다차원적이고 다양한 형태를 가지고 있습니다.

Ways of Transforming Data
* 그림 참고
* Source data type - Destination data type - Methods

X to Y Data ...
* 생략

## 2. Data Cleaning
The Reason of Cleaning
* Data collection technologies are inaccurate
* Privacy reasons
* Manual errors
* data collection is expensive

Hnadling Missing Entries
* Delete
  * 데이터 개수가 넉넉하다면 미싱 데이터 그냥 삭제하기
* Esimate or Impute
  * 다른 항목의 값이 비슷한 데이터들의 평균이나 전체 데이터들의 평균 등으로 빈 항목의 값을 추정
  * Matrix Completion: 디컴포지션(분해) 후 재조합으로 값 생성
* Well-defined Algorithm
  * 미싱 데이터가 있어도 잘 동작하는 알고리즘 고안

Handling Incorrect and Inconsistent Entries
* Inconsistency detection
  * 외국 이름 표기법, 단위 등 통일성 검사
* Domain knowledge
  * 심박수 등 상식을 기반으로 한 이상 데이터 감별
* Data-centric methods
  * raw data 눈으로 보고 outlier(특이점) 항상 확인

Scaling and Normalization
* Feature have different scales
  * age, salary, height 등 다른 종류의 데이터들은 다른 자릿수의 값들을 가지고 있습니다. 이를 그대로 분석하면 알고리즘 상 상대적으로 큰 자릿수를 가진 데이터의 영향력이 커지게 됩니다.
  * 따라서 데이터들의 자릿수를 맞춰줄 필요가 있습니다.
* Standardization
  * 정규화
* Min-Max Scaling
  * 동떨어진 Min, Max 값이 있으면 전체적인 값이 잘 반영되지 않을 수 있다는 단점이 있습니다.

## 3. Data Reduction and Transformation
## 4. Summary