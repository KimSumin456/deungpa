---
title:  "[컴퓨터비젼] 1. Image Processing Basic"
excerpt: "등록금 파먹기 - 컴퓨터비젼 파먹기 (Parming Computer Vision)"

categories:
- 컴퓨터비젼
tags:
- 등록금 파먹기
- 컴퓨터비젼
- Image Processing Basic
---

<!--1강 Image Processing-->
## Overview
1. What is an Image
2. Local Operators
3. Neighborhood Operators

## 1. What is an Image
* [이미지 - 위키백과](https://ko.wikipedia.org/wiki/%EC%98%81%EC%83%81)
* 이미지는 2차원 평면 위에 그려진 시각적 표현물을 가리킵니다.
* 함수로 표현되는 벡터 이미지(Image as functions)와 행렬로 표현되는 래스터 이미지(Digital Image)으로 나눌 수 있습니다.

### Image as functions
* 벡터 이미지(그리고 아날로그 이미지?)는 f: R<sup>2</sup> -> R 라고 나타낼 수 있습니다.

### Digital Image
* 래스터 이미지는 샘플링(sampling)과 퀀티제이션(quantization)을 거쳐야합니다.
  * 샘플링(smapling): x에 대한 f(x) 값 일부를 미리 써놓음으로써 이미지의 함수 표현을 행렬표현으로 바꾸는 과정입니다. 이로 인해 어느 정도 이상 확대 시 해상도(resolution)가 깨진다는 단점이 있습니다.
  * 퀀티제이션(quantization) 단점: 밝기 표현을 위해 값을 정수화하는 과정입니다. 이로 인해 포화(saturation), 밝기 계단 현상이 발생한다는 단점이 있습니다.

## 2. Local Operators
* local operators란 출력 픽셀 값이 대응되는 하나의 입력 픽셀 값에게서만 영향을 받는 연산입니다.
  * point process라고도 합니다.

### Pixel transforms
* Operator
  * x = [x, y], g(x) = h(f(x))
* Simple point process
  * g(x) = af(x) + b
  * a: 대비(contrast), b: 밝기(brightness)를 바꾸는 연산입니다.
* Spatially varing
  * g(x) = a(x)f(x) + b(X)
  * 비네팅처럼 이미지를 더하는 연산입니다.
* Linear
  * 선형적이다란 g(ax) = ag(x), g(ax + bx) = g(ax) + g(bx)를 만족한다는 의미입니다
* Linear blend operator
  * g(x) = (1-a)f<sub>0</sub>+(a)f<sub>1</sub>(x)
  * 줌 배경처럼 이미지를 합치는(섞는) 연산입니다.
* Non-linear transform
  * 야간 촬영 모드처럼 어두울 때 사용하는 연산입니다.

### Color transforms
* RGB가 아닌 다른 색깔 형식으로 바꿀 수 있습니다.

### Composition & Matting
* Porter Duff operators: 각각의 비율을 지정해서 이미지를 합칠 수(섞을 수) 있습니다.
* Porter Duff Table: 그 중에 괜찮다고 알려진 비율을 추천해주는 표입니다.
* Matting: 크로마키처럼 배경만을 인식해서 뽑아내는 연산입니다.

## 3. Neighborhood Operators