---
title:  "[데이터마이닝] Preliminaries"
excerpt: "등록금 파먹기 - 데이터마이닝 파먹기 (Parming Data Mining)"

categories:
- 데이터마이닝
tags:
- 등록금 파먹기
- 데이터마이닝
- Preliminaries
---

## Overview
1. Linear Algebra Review
2. Data Mining Preview

## 1. Linear Algebra Review
생략

## 2. Data Mining Preview
### 1. Importance of Words in Documents
한 문서 안에서 어떤 단어가 얼마나 중요한지 어떻게 알 수 있을까요?
* TF-IDF(Term Frequency - Inverse Document Frequency)는 정보 검색과 텍스트 마이닝에서 이용하는 가중치로, 여러 문서로 이루어진 문서군이 있을 때 어떤 단어가 특정 문서 내에서 얼마나 중요한 것인지를 나타내는 통계적 수치입니다.
  * [TF-IDF - 위키백과](https://ko.wikipedia.org/wiki/Tf-idf)
* TF-IDF의 핵심 아이디어는 2가지입니다.
  * TF(Term Frequency): 한 문서에서 자주 등장하는 단어는 중요도가 높다.
    * 예) ball, bat, pitch, run, ...
  * IDF(Inverse Document Frequency): 여러 문서에서 자주 등장하는 단어는 중요도가 낮다.
    * 예) a, an, the, ...
* 어떤 term의 TF-IDF를 계산하는 방법은 다음과 같습니다.
  * term이란 단어가 활용될 때 변하지 않는 부분, 즉 어간을 의미합니다.
    * 예) flying, flyed, fly to, ... 중 'fly'를 의미합니다
  * TF =  (한 document 내에서) 어떤 term의 frequent / 여러 term들의 frequent 중 가장 높은 frequent
  * IDF = log<sub>2</sub>(doucment들의 개수 / 어떤 term이 나타난 doucment들의 개수)
  * TF.IDF score = TF * IDF

### 2. Hash Functions, Index, Seconday Storage
생략

### 3. Base of Natural Log, Power Law
생략