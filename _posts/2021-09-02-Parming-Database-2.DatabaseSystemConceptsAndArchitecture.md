---
title:  "[데이터베이스] 2. Database System Concepts And Architecture"
excerpt: "등록금 파먹기 - 데이터베이스 파먹기 (Parming Database)"

categories:
- 데이터베이스
tags:
- 등록금 파먹기
- 데이터베이스
- Introduction
- Database System Concepts
- Architecture
---

## Overview
###### Part 1. Introduction to Databases
##### Chapter 2. Database System Concepts And Architecture
1. Data Models, Schemas, and Instances
2. Three-Schema Architecture and Data Independence
3. Database Languages and Interfaces
4. The Database System Environment
5. Centralized and Client/Server Architectures for DBMSs
6. Classification of Database Management Systems
7. Summary


<!--2_1 DB System Concepts and Architecture-->
## 2.1 Data Models, Schemas, and Instances
### Data Models
Data Model
* 데이터 모델이란 데이터베이스의 구조, 연산, 제약을 정의한 추상적인 모델입니다.
  * 데이터베이스의 구조, 구조를 조작하는 연산, 데이터베이스가 준수해야하는 제약

Constructs
* 콘스트럭트는 데이터베이스 구조를 정의하는데 사용됩니다. 일반적으로 엘리먼트들(그리고 그 엘리먼트들의 데이터 타입), 엘리먼트들의 그룹 (엔티티, 레코드, 테이블 등), 그룹들 간의 관계 등이 포함되는 개념입니다.

Constraints
* 제약은 유효한 데이터에 대한 제한을 명시합니다. 항상 제약이 지켜지도록 해야합니다.

Operations
* 연산은 데이터 모델의 콘스트럭트를 참조해서 새 데이터베이스 조회와 갱신을 명시하기 위해 사용됩니다. 기본적인 모델 연산(삽입, 삭제, 갱신, 조회 등) 뿐만 아니라 사용자 정의 연산도 포함되는 개념입니다.

Categories of Data Models  
1. Conceptual (high-level, semantic) data mdels
* 엔티티 기반 데이터 모델 또는 오브젝트 기반 모델이라고도 부릅니다.
* 많은 사용자가 데이터를 인식하는 방식에 가장 가까운 개념을 제공합니다.

2. Physical (low-level, internal) data models
* 데이터가 컴퓨터에 저장되는 방식에 대한 세부사항을 설명하는 개념을 제공합니다.
* 일반적으로 DBMS 설계 및 관리 매뉴얼을 통해 애드호크 방식으로 명시됩니다.

3. Implementation (representational) data models
* 위의 Conceputal과 Physical 사이에 해당하는 개념을 제공합니다.
* 많은 상용 DBMS을 구현하는 데 사용됩니다.
  * 예) 많은 상용 시스템에서 사용되는 관계형 데이터 모델

4. Self-Describing Data Models
* 데이터 값과 그 데이터에 대한 설명이 결합된 데이터 모델입니다.
* 예) XML, key-value sotres, 일부 NOSQL 시스템

<span style="color:blue">날림)
데이터 모델은 추상적인 개념. 100년 전만 해도 없었던 개념인 데이터베이스란 무엇인가, 무엇을 데이터베이스라고 하는 가를 체계화하는 개념.
</span>

### Schemas, and Instances
Schema
* 스키마란 데이터베이스에 대한 설명입니다. 데이터베이스 구조, 데이터 타입, 제약에 대한 설명을 포함하는 개념입니다.
* 스키마 다이어그램이란 데이터베이스 스키마를 그림으로 나타낸 것입니다.
* 스키마 콘스트럭트란 스키마의 구성 요소 또는 스키마 내의 오브젝트입니다.
  * 예) STUDENT, COURSE

Instance
* 스테이트라고도 합니다. (인스턴스라는 용어는 개인 데이터베이스 구성요소를 나타내기도 합니다?)
* 스테이트란 데이터베이스에 저장된 특정한 순간에 존재하는 실제 데이터를 말합니다. 데이터베이스에 있는 모든 데이터 집합을 포함하는 개념입니다.
* 초기 데이터베이스 스테이트란 시스템에 처음 로드될 때의 데이베이스 스테이트를 의미합니다.

Valid State
* valid state란 데이터베이스의 구조와 제약을 만족하는 상태를 의미합니다

차이점
* 데이터베이스 스키마는 거의 바뀌지 않지만, 데이터베이스 스테이트는 데이터베이스가 업데이트 될 때마다 자주 바뀝니다.
* 건물로 비유하자면 스키마는 내부 설계 구조, 스테이트는 건물 외관이라고 할 수 있습니다.

_Figure 2.1 Schema diagram for the database in Figure 1.2_

<span style="color:blue">날림)
스키마란 구체적인 개념. 특정한 UNIVERSITY 데이터베이스, COMPANY 데이터베이스를 체계화하는 개념.
</span>


## 2.2 Three-Schema Architecture and Data Independence
## Three-Schema Architecture
External Schema
* 외부적 스키마는 외부적 레벨에서 다양한 사용자 뷰를 제공합니다.
  * 각각의 외부적 스키마는 데이터베이스의 일부를 설명합니다.
  * 보통 개념적 스키마와 같은 데이터 모델을 사용합니다.

Conceptual Schema
* 개념적 스키마는 개념적 레벨에서 사용자들을 위한 전체 데이터베이스에 대한 구조와 제약을 제공합니다.
  * 구현 개념적 데이터 모델을 사용합니다.

Internal Schema
* 내부적 스키마는 내부적 레벨에서 물리적인 저장 구조와 접근 경로를 설명합니다.
  * 일반적으로 물리적인 데이터 모델을 사용합니다.

_Figure 2.2 The three-schema architecture_

스키마 레벨 사이의 매핑은 요청과 데이터를 변환하는 데 필요합니다.
* 프로그램은 외부적 스키마를 참고하고, 실행을 위해 DBMS에 의해 내부적 스키마로 매핑됩니다.
* 내부적 DBMS 레벨로부터 추출된 데이터는 알맞은 사용자의 외부적 뷰로 재구성됩니다.

<span style="color:blue">날림)
스키마란 특정한 데이터베이스에 대한 설명이라고 했는데, 자고로 그 설명하는 방식이 각자 다를 수 있는 법이다. 마치 한국사라는 같은 과목의 교과서라고 해도 초등학교, 중학교, 고등학교 교과서에 든 내용과 디테일은 서로 다른 것처럼.  
External Schema는 일반 사용자들에게, Conceptual Schema는 어플리케이션 개발자, Internal Schema는 데이터베이스 관리자에게 적합한 설명이라고 할 수 있을 것 같다.
</span>

## Data Independence
Logical Data Independence
* 지역적 데이터 독립성이란 개념적 스키마를 변경해도 외부적 스키마와 그와 관련된 애플리케이션에 영향을 끼치지 않는 특성입니다.

Physical Data Independence
* 물리적 데이터 독립성이란 내부적 스키마를 변경해도 개념적 스키마에 영향을 끼치지 않는 특성입니다.
  * 예) 데이터베이스 성능을 향상시키기 위해 특정 파일 구조를 재배치하거나 새로운 인덱스를 생성하려할 때 내부 스키마를 바꿀 수 있습니다.


## 2.3 Database Languages and Interfaces
## Language
Data Definition Language (DDL)
* DDL(Data Definition Language)이란 데이터베이스 관리자나 디자이너가 데이터베이스의 개념적 스키마를 명시할 때 사용하는 언어입니다.
* 많은 DBMS에서 내부적, 외부적 스키마를 정의하는 데에도 쓰입니다.
* 일부 DBMS에선 SDL(Storage Definition Language)과 VDL(View Definition Language)로 나누어 내부적과 외부적 스키마를 정의하기도 합니다.
  * SDL은 일반적으로 DBMS 명령어를 통해 데이터베이스 관리자와 디자이너에게 제공됩니다.

Data Manipulation Language (DML)
* DML(Data Manipulation Language)이란 데이터베이스 조회와 갱신을 지정하는데 사용되는 언어입니다.
* DML 명령어는 'data sublanguage'로서 일반적인 프로그래밍 언어(C, Java 등) 내에서 사용될 수 있습니다.
  * 프로그래밍 언어에서 DBMS에 접근하기 위해 함수 라이브러리를 제공할 수도 있습니다.
* 아니면 'query language'로서 독립적으로 사용될 수도 있습니다.
* DML의 종류로 High Level or Non-procedural Language과 Low Level or Procedural Language가 있습니다.

* High Level or Non-procedural Language
  * 선언적 언어(declarative languages)라고도 합니다.
  * "설정" 지향적이며, 어떻게 조회할 것인지가 아닌 무엇을 조회할 것인지만 명시합니다.
  * 예) SQL 관계형 언어

* Low Level or Procedural Language
  * 대화형처럼((CMD에서 파이썬 쓰듯이)) 한 번에 한 레코드 씩 데이터를 조회합니다.
  * 루핑과 같은 콘스트럭트는 지정 포인터와 함께 여러 개의 레코드를 검색하려고 할 때 필요합니다.

<span style="color:blue">날림) 일단 처음엔 데이터베이스를 생성해야 할 거고, 만든 다음엔 사용해야 할 것 아닌가. 여기서 데이터베이스를 생성하는 언어가 DDL이고, 데이터베이스를 사용하는 언어가 DML인 것이다.  
그리고 DML 중에서도 데이터베이스를 사용할 때 파이참(IDE)에서 파이썬 코딩하듯이 편안하게 쓸 수있는 언어가 있고 CMD에서 파이썬 코딩하듯이 불편하게 ~~(하지만 간지나게)~~ 쓸 수 있는 언어가 있는데, 전자를 High Level or Non-procedural Language, 후자를 Low Level or Procedural Language라고 하는 것이다.
</span>

## Interfaces
프로그래밍 언어 내에서 사용되는 embedding DML을 위한 인터페이스들

* Embedded Approach
  * 예) embedded SQL (for C, C++, etc.), SQLJ (for Java)

* Procedure Call Approach
  * 예) JDBC (for Java), ODBC(Open Database Connectivity) (for 나머지 프로그래밍 언어들을 위해 API 형태로)

* Database Programming Language Approach
  * 예) PL/SQL

* Scripting Languages
  * 예) PHP, Python

DBMS 인터페이스들
* User-friendly DBMS interfaces
  * 메뉴 기반 (웹 기반): 웹 브라우징에서 널리 사용됨
  * 형태 기반: 소박한 사용자(은행 직원 등) 정도를 위해 디자인 됨
  * 그래픽 기반: 마우스로 손쉽고 친숙한 사용 가능, 스키마 다이어그램으로 쿼리를 명시
  * 자연어: 영어로 쓰인 요청 처리
  * 위의 것들의 조합: 취사선택 가능

* Other DBMS interfaces
  * 자연어
  * 음성
  * 키보드로 검색 가능한 웹 브라우저
  * 매개변수를 입력받는 인터페이스
  * DBA(데이터베이스 관리자)를 위한 인터페이스

<span style="color:blue">날림) CLI나 GUI 등 여러가지 방식으로 Git을 사용할 수 있는 것처럼, 여러가지 방식(매개체)으로 DBML을 사용할 수 있다.
</span>


## 2.4 The Database System Environment
Typical DBMS Conponent Modules  
_Figure 2.3 Component modules of a DBMS and thier interactions._


## 2.5 Centralized and Client/Server Architectures for DBMSs
1. Centralized DBMS
* 중앙집중식 DBMS란 DBMS 소프트웨어, 하드웨어, 응용 프로그램, 사용자 인터페이스 처리 소프트웨어 등 모든 것을 단일 시스템에 합친 형태의 DBMS를 의미합니다.
* 사용자는 원격 터미널을 통해 접속할 수 있으나, 모든 처리는 중앙에서만 이루어집니다.
* _Figure 2.4 A physical centralized architecture._

2. Basic 2-tier Client-Server Architecture
* 서버가 특수한 기능을 가지고 전문화되었습니다.
  * 프린트 서버, 파일 서버, DBMS 서버, 웹 서버, 이메일 서버
* 클라이언트는 필요에 따라 각각 전문화된 서버를 접근할 수 있습니다.
* _Figure 2.5 Logical two-tier client/server architecture._

* DBMS 서버
  * DBMS 서버데이터베이스 쿼리와 트랜잭션 서비스를 클라이언트에게 제공합니다.
  * 관계형 DBMS 서버는 SQL 서버, 쿼리 서버, 트랜잭션 서버 등으로도 불리웁니다.
  * 어플리케이션은 클라이언트 쪽에서 표준 인터페이스를 거쳐 서버 데이터베이스에 접근하는 API를 통해 돌아갑니다.
    * ODBC:Open Database Connectivity standard
    * JDBC: For Java Programming Access

* 클라이언트
  * 클라이언트는 다양한 서버 자원에 접근하고 활용하는 클라이언트 소프트웨어 모듈을 통해 적절한 인터페이스를 제공합니다.
  * 클라이언트는 디스크리스 기계나 PC, 또는 오직 클라이언트 소프트웨어만 설치된 디스크를 가진 워크스테이션일 수도 있습니다.
  * 어떤 형태의 네트워크를 거쳐 서버로 연결됩니다.
    * 네트워크의 형태는 LAN(Local Area Network), Wirell Network 등이 있습니다.

3. Three Tier Client-Server Architecture
* 웹 어플리케이션 구현에 주로 사용됩니다.
* 중간 레이어를 어플리케이션 서버 또는 웹 서버라고 합니다.
  * 데이터베이스 서버에서 해당 데이터에 접근하기 위해 사용되는 어플리케이션의 웹 연결 소프트웨어 및 비즈니스 로직 부분을 저장합니다.
  * 데이터베이스 서버와 클라이언트 사이에서 부분적으로 처리되는 데이터를 보내기 위한 배관(conduit)처럼 동작합니다.
* Three-tier 구조는 보안을 향상할 수 있습니다.
  * 데이터베이스 서버는 오직 중간 티어를 거쳐야만 접근할 수 있습니다.
  * 클라이언트는 데이터베이스 서버에 직접적으로 접근할 수 없습니다.
  * 클라이언트는 UI와 웹 브라우저를 갖고 있습니다.
  * 클라이언트는 보통 웹과 연결된 PC 또는 모바일 장치입니다.
* _Figure 2.7 Logical three-tier client/server architecture, with a couple of commonly used nomenclatures._


## 2.6 Classification of Database Management Systems
Based on the data model used
* 레거시: Network, Hierarchical
* 현재 사용 중인: Relational, Object-oriented, Object-relational
* 최근 기술들: Key-value storage systems, NOSQL systems: document based, column-based, graph-based and key-value based, Native XML DBMSs

Other classifications
* single-user, multi-user
* centralized, Distributed


## 2.7 Summary
* Data Models and Their Categories
* Categories of Data Models
* Schemas, Instances, and States
* Three-Schema Architecture
* Data Independence
* DBMS Languages and Interfaces
* Database System Utilities and Tools
* Centralized and Client-Server Architectures
* Classification of DBMSs

