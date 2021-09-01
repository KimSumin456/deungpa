---
title:  "[운영체제] 1. Introduction"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Introduction
---

## Preview
* Operating Systems
* Computer Systems

<!--1강 Introduction to Operating Systems-->
## 1.1 What Operating Systems Do
* 운영체제란 User/Application과 Computer Hardware 사이에서 중간자 역할을 하는 프로그램이다.
* 운영체제는 Hardware를 제어하고, 수많은 User/Applications들이 하드웨어를 사용하려는 상황을 조정한다.
### 1.1.1 User View
* User/Application View로 바라볼 때 운영체제의 역할은 User/Application이 hardware, resource utilization에 대해 신경쓰지 않아도 '쉽게' 프로그램을 실행할 수 있도록 해주는 일이다.
* 프로그램을 실행할 수 있는 환경을 제공하고, 컴퓨터 시스템을 abstract view로 제공한다.
### 1.1.2 System View
* System View로 바라볼 때 운영체제의 역할은 수많은 Users/Applications이 '효율적이고 공정하게' 리소스(resources)를 사용할 수 있도록 잘 관리해주는 일이다.
* 컴퓨터 시스템의 하드웨어와 I/O 디바이스 등 컴퓨터 시스템의 다양한 리소스를 관리하고, 오류 및 부적절한 사용을 방지하기 위한 프로그램을 제어한다.
### 1.1.3 Defining Operating Systems
* 일반적으로 운영체제에 대한 완전한 정의는 없다. 운영체제는 보통 응용 프로그램들이 공통적으로 필요로 하는 리소스 제어나 할당 같은 작업이 하나로 통합된 소프트웨어다.
* 운영체제의 일부분에 대한 정의도 일반적으로 받아들여지고 있는 게 없다. 그 중 일반적인 정의로 운영체제는 컴퓨터에서 항상 실행되는 하나의 프로그램, 커널로 정의되기도 한다. 
그리고 커널과 함께 운영 체제와 연결되어 있지만 꼭 커널의 일부는 아닌 시스템 프로그램과 시스템의 작동과 관련이 없는 모든 프로그램을 포함하는 애플리케이션 프로그램이 있다.

## 1.3 Computer-System Architecture
현대의 모든 컴퓨터는 폰 노이만 구조를 가지고 디자인되어 있다. 현대 컴퓨터를 구성하는 3가지 요소는 CPU, Memory, 그리고 I/O devices다.
컴퓨터 시스템은 다양한 기준으로 구분될 수 있는데, 우리는 이것을 범용 프로세서(general purpose processors)의 수에 따라 대략적으로 분류할 수 있다.
### 1.3.1 Single-Processor Systems
* Single-Processor란 하나의 Processing Core을 가진 하나의 CPU를 포함하는 프로세서이다.
* 수년 전, 대부분의 컴퓨터 시스템은 Single Processor를 사용했다. Single Processor는 크기를 더 줄이고 코어를 더 빠르게 동작시키면서 성능을 높여나갔다.
 하지만 그렇게 성능을 높인 Single Processor는 많은 전기 에너지가 필요했고 이로 인해 과다한 열 에너지가 방출되는 Power Wall 문제에 부닥치게 된다.
* 그렇기 때문에 더 이상 Single Processor의 성능을 높이는 대신 여러 개의 Processor를 사용해서 성능을 높이는 방향으로 발전하게 되었고, 현대 컴퓨터들은 Multiprocessor System을 사용한다.
### 1.3.2 Multiprocessor Systems
* Multi-Processor라고 하면 여러 개의 프로세서(=CPU, 칩)를 사용하는 Multiprocessor System 뿐만 아니라, 하나의 프로세서이지만 여러 개의 코어를 가진 Multicore system(=Single-chip multiprocessor)도 의미할 수 있다.
  * Symmetric Multiprocessing (SMP)는 각 프로세서가 운영체제 기능과 User/Application 프로세스 등을 포함한 모든 작업을 평등하게 수행하는 방식이다.
    Asymmetric Multiprocessing (AMP)는 각 프로세서가 특정 작업을 분담해서 차별적으로 수행하는 방식이다.
  * Uniform Memory Access architecture (UMA)는 프로세서는 여러 개지만 공동 메모리 1개를 사용하는 구조이다.
    Non-Uniform Memory Access architecture (NUMA)는 프로세서 여러 개가 각자 메모리도 가지고 있는 구조이다. 정확한 의미의 멀티 프로세서다.
### 1.3.3 Clustered Systems
* 여백

<!--(강의 순서대로 재배치 한 것임. 숫자 단 하나도 오타 아님)-->
## 1.2 Computer-System Organization
* 현대의 컴퓨터 시스템은 하나 이상의 CPU와 다수의 device controllers로 구성되어 있으며, 이들은 (logical하게) common bus를 통해 연결되어 있다. common bus는 구성 요소들이(CPUs, devices) 공유하는 메모리에 접근할 수 있는 길을 제공한다. 그렇기 때문에 CPUs와 devices들은 동시에 메모리에 접근하기 위해 경쟁한다.
* 각 Device Controller (DC)는 특정한 device type을 담당한다. 그리고 local buffer를 가지고 있다.
* I/O is from/to ..?
### 1.2.1 Interrupts
### 1.2.3 I/O Structure
### 1.2.2 Storage Structure

<!--2강 -->
## 1.4 Operating-System Operations
## 1.5 Resource Management
## 1.6 Security and Protection
## 1.7 Virtualization
## 1.8 Distributed Systems
## 1.9 Kernel Data Structures
## 1.10 Computing Environments
## 1.11 Free and Open-Source Operating Systems
## 1.12 Summary