---
title:  "[데이터베이스] 1. Databases And Database Users"
excerpt: "등록금 파먹기 - 데이터베이스 파먹기 (Parming Database)"

categories:
- 데이터베이스
tags:
- 등록금 파먹기
- 데이터베이스
- Introduction
- Databases
- Database Users
---

## Overview
###### Part 1. Introduction to Databases
##### Chapter 1. Databases and Databsae Users
1. Introduction
2. An Example
3. Characteristics of the Database Approach
4. Actors on the Scene
5. Workers behind the Scene
6. Advantages of Using the DBMS Approach
7. A Brief History of Database Applications
8. When Not to Use a DBMS
9. Summary

<!--1_2_Lec_DB_intro-->
## 1.1 Introduction
Introduction
* 데이터는 어디에나 존재합니다!
* 데이터베이스(Database)와 데이터베이스 애플리케이션(Database Application)의 종류로는 기존의 데이터베이스 애플리케이션뿐만 아니라 멀티미디어 데이터베이스, 지리 정보 시스템(GIS), 빅데이터 및 NOSQL(Not Only SQL) 시스템 등으로 다양합니다.

### Basic Definition
기본 정의(Basic Definition)
* 데이터베이스(Database): 관련있는 데이터들의 집합입니다.
* 데이터(Data): 기록될 수 있고 유의미한 사실들입니다.
* 작은 세계(Mini-world): 데이터베이스에 저장되는 데이터는 현실 세계의 일부로서 하나의 작은 세계라고 볼 수 있습니다.
  * 예) 대학생의 성적(현실 세계)와 성적 증명서(작은 세계)
* 데이터베이스 관리 시스템(Database Management System, DBMS): 전산화된 데이터베이스의 생성과 유지를 용이하게 해주는 소프트웨어 패키지/시스템입니다.
* 데이터베이스 시스템(Database System): DBMS 소프트웨어와 데이터 그 자체를 의미합니다. 때로는 애플리케이션까지 포함한 뜻으로 사용되기도 합니다.
* 데이터베이스 정의(Defining a database): 저장될 데이터의 타입(type), 구조(structure), 제약(constraints)을 명시합니다.
* 메타 데이터(Meta-data): 데이터베이스의 정의, 또는 기술적인([descriptive - 네이버 영어사전](https://en.dict.naver.com/#/entry/enko/766e4d9baa30413a99facb4b0e97cdca)) 정보를 말합니다. 데이터베이스 카탈로그(catalog) 또는 사전(dictionary) 형태로 DBMS에 저장됩니다.
* 데이터베이스 조작(Manipulating a database): 데이터베이스를 쿼리(query)하고 업데이트(update)합니다. 보고서(reports)도 생성합니다.
* 데이터베이스 공유(Sharing a database): 여러 유저와 프로그램들이 데이터베이스에 동시 접근하는 것을 허용합니다.
* 응용 프로그램(Application program): DBMS로 쿼리를 날림으로써 데이터베이스에 접근합니다.
* 쿼리(Query): 일부 데이터를 찾습니다.
* 트랜잭션(Transaction): 일부 데이터를 읽거나 씁니다.
* 보호(Protection): 하드웨어나 소프트웨어 오작동에 대한 시스템 보호(System protection)와 인증 또는 오류에 대한 정보 보호(Security protection)를 제공합니다.
* 데이터베이스 시스템 유지(Maintain the database system): 사용자의 요구가 변화함에 따라 시스템을 개선합니다.

일반적인 DBMS의 기능(Typical DBMS Functionality)
* 데이터 타입, 구조, 제약에 관하여 특정한 데이터베이스를 <b>정의(Define)</b>합니다.
* 저장소(secondary storage medium)에 초기 데이터베이스 내용을 <b>생성(Construct) 또는 로드(Load)</b>합니다.
* 데이터베이스를 <b>조작(Manipulating)</b>합니다
  * 조회(Retrieval): 쿼리, 보고서 생성
  * 수정(Modification): 내용 삽입, 삭제, 업데이트
  * 웹 앱(Web applications)을 통한 데이터베이스 접근
* 동시다발적인(concurrent) 사용자들과 응용 프로그램들의 집합을 <b>처리(Processing)하고 공유(Sharing)</b>합니다.
  * 모든 데이터를 유효하고 일관성 있게 유지합니다.

## 1.2 An Example
_Figure 1.1 A simplified database system environment_
* 그림 참고

_Figure 1.2 A database that stores student and course information_
* 그림 참고

예제: 대학교 데이터베이스(An example: UNIVERSITY database)
* 대학교 데이터베이스
  * 대학 환경의 학생, 강의, 성적에 관한 정보를 담고 있습니다.
* 데이터 레코드(records)
  * 데이터베이스는 5개의 파일로 구성되어있고, 각 파일은 데이터 레코드를 저장하고 있습니다.
  * (UNIVERSITY 데이터베이스의 데이터 레코드) STUDENT, COURSE, SECTION, GRADE_REPORT, PREQUISTITE
* 데이터 엘리먼트(elements)
  * 레코드의 각 데이터 엘리먼트 그 요소의 데이터 타입을 지정함으로써 각 파일의 레코드 구조를 정합니다.
  * (STUDENT 레코드의 데이터 엘리먼트) Name, Student_number, Class, Major
  * (STUDENT 레코드의 Name 엘리먼트의 데이터 타입) a string of alphabetic charcters
* 이제 UNIVERSITY 데이터베이스를 실제로 구축합니다.
  * 각각의 정보를 나타내는 데이터를 알맞은 파일에 레코드(record)로 저장합니다.
  * 다양한 파일의 레코드들은 서로 관계되어 있습니다.
* 데이터베이스의 조작에는 쿼리와 업데이트가 포함됩니다.
  * 쿼리의 예는 다음과 같습니다. (Examples of queries)
    * 성적 증명서 조회
    * 2008년 가을학기에 개설된 데이터베이스 과목을 수강한 학생의 이름과 해당 과목의 성적을 나열
    * 데이터베이스 강의의 선수 과목을 나열
  * 업데이트의 예는 다음과 같습니다. (Examples of updates)
    * 스미스를 2학년으로 변경
    * 이번 학기의 데이터베이스 과정에 대한 새 섹션 만들기
    * 지난 학기의 데이터베이스 섹션의 스미스에 A 학점 입력

데이터베이스에 대한 애플리케이션의 동작(Application Activities Aginst a Database)
* 애플리케이션은 쿼리와 트랜잭션을 발생시킴으로써 데이터베이스와 상호작용합니다.
  * 쿼리: 데이터의 다른 부분에 접근하고 요청(request)의 결과를 도출합니다(formulate).
  * 트랜잭션: 일부 데이터를 읽고, 특정 값을 **업데이트** 하고, 새로운 값을 만들고(generate), 그 값을 데이터베이스에 저장합니다.
* 애플리케이션은 승인되지 않은 사용자가 데이터에 접근하는 것을 허용해서는 안 됩니다.
* 애플리케이션은 데이터베이스에 대해 사용자의 요구가 변화하는 것을 따라야합니다.

## 1.3 Characteristics of the Database Approach
데이터베이스 접근법의 특징(Characteristics of the database approach)
* 전통적인 파일 처리(Traditional file processing)
  * **각 사용자**가 특정한 소프트웨어 애플리케이션에 필요한 파일들을 정의하고 구현했었습니다.
* 데이터베이스 접근(Database approach)
  * 단일 레포지토리는 한 번 정의된 다음, **다양한 사용자가** 접근합니다.

데이터베이스 접근법의 주요 특징(Main characterstics of database approach)
1. 데이터베이스 시스템의 자기 기술성(Self-describing nature of a database system) _-> 1.3.1_
2. 프로그램과 데이터의 분리(Insulation between programs and data) / 데이터 추상화(data abstraction) _-> 1.3.2_
3. 데이터의 다양한 뷰 지원(Support of multiple views of the data) _-> 1.3.3_
4. 데이터 공유와 다중사용자 트랜잭션 처리(Sharing of data and multiuser transaction processing) _-> 1.3.4_

### 1.3.1 Self-Describing Nature of a Database System
데이터베이스 시스템의 자기 기술성(Self-Describing Nature of a Database System)
* 데이터베이스 시스템은 구조와 제약에 대한 완전한 정의를 포함하고 있습니다.
* 메타데이터(Meta-data)란 데이터베이스의 구조를 설명하는 데이터입니다.
* 데이터베이스 카탈로그는 DBMS 소프트웨어와 데이터베이스 사용자들(데이버테이스 구조에 대한 정보를 필요로 하는)에 의해 사용됩니다.

### 1.3.2 Insulation between programs and data, and data abstraction
프로그램과 데이터의 분리(Insulation between programs and data)
* 프로그램 데이터 독립성(Program-data independence): 데이터 파일들의 구조는 접근 프로그램들과는 별개로 DBMS 카탈로그에 저장됩니다.
  * 전통적인 파일 시스템은 한 파일의 구조를 변경하면 그 파일을 접근하는 모든 프로그램을 변경해야 했었습니다.
* 프로그램 연산 독립성(Program-operation independence): 연산들은 두 가지로 특정됩니다.
  * 인터페이스는 연산의 이름과 필요로 하는 파라미터의 데이터 타입을 명시합니다.
  * 구현(Implementation)은 인터페이스에 영향을 끼치지 않고 변경할 수 있습니다.

데이터 추상화(Data abstraction)
* 데이터 추상화가 프로그램 데이터 독립성과 프로그램 연산 독립성을 가질 수 있게 해줍니다.
* 데이터의 개념적 표현(Conceptual representation of data)에선 어떻게 데이터가 저장되었는지 또는 어떻게 연산이 구현되었는지에 대한 세부사항은 포함하지 않습니다.
* 데이터 모델은 개념적 표현을 제공하는 데이터 추상화의 종류입니다.

### 1.3.3 Support of multiple views of the data
데이터의 다양한 뷰 지원(Support of multiple views of the data)
* 뷰(View)란 데이터베이스의 부분집합입니다 데이터베이스 파일로부터 파생된 <b>가상 데이터(virtual data)</b>를 포함하지만 명시적으로 저장되진 않습니다.
* 다중사용자 DBMS(Multiuser DBMS)는 사용자들이 다양한 애플리케이션을 보유하고 있습니다. 반드시 다중 뷰를 정의하는 기능을 제공해야합니다.

### 1.3.4 Sharing of data and multiuser transaction processing
데이터 공유와 다중사용자 트랜잭션 처리(Sharing of data and multiuser transaction processing)
* 다중사용자들이 동시에 데이터베이스로 접근하는 것을 허용합니다.
* 동시다발적인 제어 소프트웨어(concurrency control software)는 통제된 방식을 통해 여러 사용자가 동일한 데이터를 업데이트할 수 있도록 해줍니다.
  * 업데이트의 결과는 문제없이 정확합니다.
* 온라인 트랜잭션 처리 (OnLine Transaction Processing, OLTP) application은 온라인 예약 시스템을 의미합니다. 많은 에이전트와 많은 손님이 있습니다.
  * 격리(isolation): 각 트랜잭션은 서로 영향을 미치지 않습니다.
  * 아토믹(atomic): 각 트랜잭션은 한 번에 완전히 성공하거나 아예 실패하거나 합니다.

## 1.4 Actors on the Scene
### 1.4.1 Database Administartors
데이터베이스 관리자(Database Administartors)
* 데이터베이스에 대한 액세스 권한을 부여합니다.
* 데이터베이스 사용을 조정하고 관찰합니다.
* 소프트웨어와 하드웨어 자원을 확보합니다.

### 1.4.2 Database Designers
데이터베이스 디자이너(Database Designers)
* 저장할 데이터를 선별합니다.
* 그 데이터를 표현하고 저장하기에 적절한 구조를 선택합니다.

### 1.4.3 End Users
사용자(End Users)
* 데이터베이스 접근이 필요한 작업을 수행하는 사람들입니다.
  * 일반 사용자(casual end users) - 데이터베이스에 가끔 접근합니다
  * 소박한 사용자(naive or parametric end users) - 잘 짜여진 데이터베이스를 자주 쿼리하고 업데이트합니다
  * 복합적인 사용자(sophisticated end users) - 공학자, 과학자, 분석가처럼 자신만의 애플리케이션을 구현하기 위해 접근합니다.
  * 독립적인 사용자(standalone users) - 개인 데이터베이스를 갖습니다

### 1.4.4 System Analysts and Application Programmers (Software Engineers)
시스템 분석가(System Analysts)
* 사용자들의 요구사항(니즈)를 파악합니다.

애플리케이션 프로그래머(Application Programmers)
* 그 요구사항을 프로그램으로 구현합니다.

이러한 분석가들과 프로그래머들을 소프트웨어 개발자(software developers) 또는 소프트웨어 엔지니어(software enginners)라고 부릅니다.

## 1.5 Workers behind the Scene
### 1.5.1 DBMS system designers and implementers
DBMS 시스템 디자이너와 개발자(DBMS system designers and implementers)
* DBMS 모듈과 인터페이스를 소프트웨어 패키지로 디자인하고 개발합니다.

### 1.5.2 Tool developers
툴 개발자(Tool developers)
* 툴을 디자인하고 개발합니다.

### 1.5.3 Operators and maintenance personnel
운영직와 관리직(Operators and maintenance personnel)
* 데이터베이스 시스템을 위한 하드웨어와 소프트웨어 환경의 실행과 관리를 책임집니다.

## 1.6 Advantages of Using the DBMS Approach
### 1.6.1 Controlling Redundancy
중복 관리(Controlling Redundancy)
* 데이터 정규화(data normalization)
* 비정규화(denormalization)
  * 쿼리의 속도(performance)를 향상시키기 위해 때때로 의도적인 중복(controlled redundancy)을 필요로도 합니다.

### 1.6.2 Restricting Unauthorize Access
무단 접근 제한(Restricting Unauthorize Access)
* 보안 및 인증 서브시스템
* 기밀한(privileged) 소프트웨어

### 1.6.3 Providing Persistent Storage for Program Objects
프로그램 오브젝트를 위한 영구적인 저장소 제공(Providing Persistent Storage for Program Objects)
* 객체지향 DBMS에서는 C++의 복잡한 객체를 영구적으로 저장할 수 있습니다.
* 임피던스(impedance) 불일치 문제
  * 객체지향 데이터베이스 시스템은 일반적으로 데이터 구조에 호환성(compatibility) 제공합니다.

### 1.6.4 Providing Storage Structures and Search Techniques for Efficient Query Processing
효율적인 쿼리 처리를 위한 자료 구조와 검색 알고리즘 제공(Providing Storage Structures and Search Techniques for Efficient Query Processing)
* 인덱싱(indexes)
* 버퍼링 및 캐싱(buffering and caching)
* 쿼리 처리와 최적화(Query proceesing and optimization)

### 1.6.5 Providing Backup and Recovery
백업 및 복구 제공(Providing Backup and Recovery)
* DBMS의 서브시스템의 백업 및 복구를 제공합니다.

### 1.6.6 Providing Multiple User interfaces
다중사용자 인터페이스 제공(Providing Multiple User interfaces)
* GUIs(Graphical User Interfaces)를 제공합니다.

### 1.6.7 Representing Complex Relationships among Data
데이터 간의 복잡한 관계 표현(Representing Complex Relationships among Data)
* 서로 관련 있는 다양한 데이터들을 여러 가지 방법으로 표현할 수 있습니다.

### 1.6.8 Enforcing Integrity Constraints
무결성을 위한 제약 강제(Enforcing Integrity Constraints)
* 권장하는 무결성을 위한 제약(Refernetial integrity constraint)
  * 예) 모든 '섹션'의 레코드는 반드시 '강의' 레코드와 연관되어야 한다.
* 키 또는 고유성을 위한 제약
  * 예) 모든 '강의' 레코드는 반드시 겹치지않는 유일한 값의 '과목코드'를 가져야한다.

### 1.6.9 Permitting Inferencing and Actions Using Rules and Triggers
규칙을 통한 추론 및 행동 허용(Permitting Inferencing and Actions Using Rules and Triggers)
* 연역적인 데이터베이스 시스템
  * 연역적인 규칙을 정의할 수 있습니다.
  * 저장된 데이터베이스 사실들로부터 새로운 정보를 추론할 수 있습니다.
* 트리거
  * 테이블이 업데이트 됐을 때 자동으로 실행되는 규칙을 만들 수 있습니다.
* 절차
  * 여러가지 절차들을 한 번에 묶어서 실행되는 규칙을 만들 수 있습니다.

### 1.6.10 Additional Implications of Using the Database Approach
데이터베이스 접근을 이용한 결과(Additional Implications of Using the Database Approach)
* 애플리케이션 개발 시간의 감소(Reduced application evelopment time)
* 유연성(Flexibility)
* 최신 정보 이용가능(Availability of up-to-date information)
* 규모의 경제성(Economies of scale (cost reduction))

## 1.7 A Brief History of Database Applications
### 1.7.1 Early Database Applications Using Hierarchical and Network Systems
### 1.7.2 Providing Data Abstraction and Application Flexibility with Relational Databases
### 1.7.3 Object-Oriented Applications and the Need for More Complex Databases
### 1.7.4 Interchanging Data on the Web for E-Commerce Using XML
### 1.7.5 Extending Database Capabilities for New Applications
### 1.7.6 Emergence of Big Data Storage Systems and NOSQL Databases
생략

## 1.8 When Not to Use a DBMS
다음과 같은 경우엔 일반적인 파일을 사용하는 것이 더 바람직합니다.
* 간단하고 잘 정의되어 구조를 변경할 일이 거의 없는 데이터베이스 애플리케이션
* 엄격하고 실시간 요구가 많은 경우
* 한정된 저장 공간을 가진 시스템
* 데이터에 다중 사용자가 접근할 일이 없는 경우

## 1.9 Summary
* Database 
  * Collection of related data (recorded facts)
* DBMS 
  * Generalized software package for implementing and maintaining a computerized database
* Characteristics of the database approach
* Types of database users
* History of database
* Database applications have evolved
* When not to use a DBMS
