---
title:  "[실전코딩1] 1. SW Process"
excerpt: "등록금 파먹기 - 실전코딩1 파먹기 (Parming Practical Coding 1)"
toc: true
toc_sticky: true

categories:
- 실전코딩1
tags:
- 등록금 파먹기
- 실전코딩1
- Sw Process
---

## Preview
* SW Process
* Waterfall
* Agile
* DevOps

<!--1강 Page Replacement-->
## 19.0 SW Process
* 소프트웨어 개발 프로세스(software devleopment process)는 소프트웨어 제품을 개발하기 위해 필요한 과정 또는 구조이다. 소프트웨어 개발 프로세스에는 몇 가지 모델이 존재하며, 이들 각각은 해당 단계별로 요구되는 활동이나 작업을 기술하고 있다.

## 19.1 Waterfall
* 폭포수 모델(waterfall model)은 순차적인 소프트웨어 개발 프로세스로, 개발의 흐름이 마치 폭포수같이 지속적으로 아래로 향하는 것처럼 보이는 데서 이름이 붙여졌다.
* 이 폭포수 모델의 흐름은 소프트웨어 요구사항 분석 단계에서 시작하여, 소프트웨어 설계, 소프트웨어 구현, 소프트웨어 시험, 소프트웨어 통합 단계 등을 거쳐, 소프트웨어 유지보수 단계에까지 이른다.
* QA(Quality Assurance) 피드백을 받기까지 시간이 오래 걸리고, 협력이 어렵고, 프로젝트의 방향을 바꾸기 어렵다는 단점이 있다.

### 19.1.1 Today: weeks-to-months to value
### 19.1.2 Tomorrow: hours to days
### 19.1.3 The Day After Tomorrow: Seconds
### 19.1.4 V-model
* V 모델(V-model)은 폭포수 모델의 확장된 형태 중 하나로 볼 수 있다. 아래 방향으로 선형적으로 내려가면서 진행되는 폭포수 모델과 달리, 이 프로세스는 코딩 단계에서 위쪽으로 꺾여서 알파벳 V자 모양으로 진행된다는 차이점이 있다.
* 소프트웨어 개발의 각 단계마다 상세한 문서화를 통해 작업을 진행하는 잘 짜인 방법을 사용한다. 또한 테스트 설계와 같은 테스트 활동을 코딩 이후가 아닌 프로젝트 시작 시에 함께 시작하여, 전체적으로 많은 양의 프로젝트 비용과 시간을 감소시킨다.

## 19.2 Agile
* 애자일 소프트웨어 개발(agile software development)는 프로젝트의 생명주기 동안 반복적인 개발을 촉진한다.
* 폭포수 모델과 구별되는 가장 큰 차이점은 문서가 아닌 실질적인 코딩을 통한 방법론이라는 점이다.
* 그러므로 고전적인 방법론과는 다르게 앞을 예측하며 개발을 하지 않고, 일정한 주기를 가지고 끊임없이 프로토 타입을 만들어내며 그때 그때 필요한 요구를 더하고 수정하여 하나의 커다란 소프트웨어를 개발해 나가는 adaptive style 이라고 할 수 있다.

## 19.3 DevOps
* 데브옵스(DevOps)는 소프트웨어 개발(Development)과 운영(Operations)의 합성어로서, 소프트웨어 개발자와 정보기술 전문가 간의 소통, 협업 및 통합을 강조하는 개발 환경이나 문화를 말한다.
* 소프트웨어 개발조직과 운영조직 간의 상호 의존적 대응이며 조직이 소프트웨어 제품과 서비스를 빠른 시간에 개발 및 배포하는 것을 목적으로 한다.
* 데브옵스가 잘 된다면 Automate some stuff -> Reduce Incidents -> Free up people's time -> Payback some technical debt -> Improve quality -> Automate some stuff -> ... 의 선순환을 이룰 수 있다.

## 19.-1 Reference
* [소프트웨어 개발 프로세스 - 위키백과](https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EA%B0%9C%EB%B0%9C_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4)
* [폭포수 모델 - 위키백과](https://ko.wikipedia.org/wiki/%ED%8F%AD%ED%8F%AC%EC%88%98_%EB%AA%A8%EB%8D%B8)
* [애자일 소프트웨어 개발 - 위키백과](https://ko.wikipedia.org/wiki/%EC%95%A0%EC%9E%90%EC%9D%BC_%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EA%B0%9C%EB%B0%9C)
* [데브옵스 - 위키백과](https://ko.wikipedia.org/wiki/%EB%8D%B0%EB%B8%8C%EC%98%B5%EC%8A%A4)

* [개발방법론 비교! 애자일, 데브옵스, 폭포수, 어떤 것을 선택해야 할까요? - 삼평동연구소](https://www.youtube.com/watch?v=7KadB1ZUeMk)
* [개발에도 순서가 있다! 개발 방법론의 클래식, 폭포수 모델 - 삼평동연구소](https://www.youtube.com/watch?v=7nPg7_o2Pmc)