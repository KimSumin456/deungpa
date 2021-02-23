---
title:  "2.Instructions: Language of the Computer"
excerpt: "등록금 파먹기 - 컴퓨터 구조 파먹기 (Parming Computer Architecture)"
toc: true
toc_sticky: true

categories:
- 컴퓨터 구조
tags:
- 등록금 파먹기
- 컴퓨터 구조
- Instructions - Language of the Computer
---

<!--5-1강-->
## 2.1 Introduction
* 인스트럭션(instruction)이란
  * 컴퓨터 하드웨어가 이해하고 따르는 명령을 지칭하는 말이다.
    * 명령을 문자(symbolic) 표현한 언어가 어셈블리어, 명령을 숫자(binary)로 표현한 언어가 기계어다. 그리고 어셈블리어보다 가독성과 생산성을 높인 C, C++, Java와 같은 언어가 고급 프로그래밍 언어(high-level programming)이다.
    * 그래서 프로그래머가 C 언어로 C 프로그램을 만들면, C 프로그램은 컴파일러에 의해 어셈블리어 프로그램으로 컴파일 되고, 다시 어셈블리어 프로그램은 어셈블러에 의해 기계어 프로그램으로 번역된다.
  * 어셈블리어의 명령어 키워드 하나를 의미하기도 한다.
## 2.2 Operations of the Computer Hardware
* 인스트럭션 집합(Instruction Set) 또는 인스트럭션 집합 구조(Instruction Set Architecture, ISA)란
  * 컴퓨터 언어의 모든 인스트럭션 목록을 말한다.
  * 컴퓨터마다 다른 인스트럭션 집합(Instruction Set)을 가진다.
    * x86, ARM, MIPS 등이 있다.
  * 초기 컴퓨터들은 매우 간단한 인스트럭션 집합(Instruction Set)을 가졌다.
  * 최신 컴퓨터들도 여전히 간단한 인스트럭션 집합(Instruction Set)을 포함하고 있다.
* MIPS 인스트럭션 집합(The MIPS Instruction Set)
  * 이 책에서는 MIPS라는 인스트럭션 집합(Instruction Set)을 예제로 사용한다.
  * 예전부터 많이 사용되어 왔고 현대의 ISA와 매우 흡사하며 그 형태가 간단하기 때문이다.
* 간략한 산술 연산 예제를 통해 어떻게 C code가 MIPS 하드웨어가 이해할 수 있는 어셈블리어로 컴파일되는지 알아보자
  * 예제 2.2.1
    * C code:
      * a = b + c;
    * Compiled MIPS code (assembly):
      * add a, b, c
  * 예제 2.2.2
    * C code:
      * a = b + c;
    * Compiled MIPS code (assembly):
      * add a, b, c
  * 예제 2.2.3
    * C code:
      * f = (g + h) - (i + j);
    * Compiled MIPS code (assembly):
      * add $t0, g, h #temp t0 = g + h
      * add $t0, g, h #temp t0 = g + h
      * sub f, t0, t1;
  * MIPS에서 모든 산술 연산은 이러한 형식을 가진다.
## 2.3 Operands of the Computer Hardware
* 레지스터 피연산자(Register Operand)
  * 레지스터란 프로세서에 들어 있는 소규모 기억 장치이다. 프로세서에 위치하기 때문에 빠르게 데이터에 접근 가능하다.
  * MIPS는 0번 레지스터부터 31번 레지스터까지 총 32개의 32 비트 레지스터를 가진다. 각 레지스터는 번호와 함께 &t0, &s1와 같은 어셈블러 이름(Assembler names)을 가지고 있다.
  * 이렇듯 32 비트를 기본 단위로 연산하기 때문에 32 비트 데이터를 워드(word)라는 단위로 나타낸다.
* 사실 위에서 본 예제들은 정확한 표현이 아니다. 왜냐하면 산술 인스트럭션(Arithmetic instructions)은 레지스터 피연산자를 사용하기 때문이다. 예제 2.2.3을 정확히 고치면 다음과 같다.
  * 예제 2.2.3
    * f, g, h, i, j는 각각 $s0, $s1, $s2, $s3, $s4에 저장되어 있다고 가정하자.
    * C code:
      * f = (g + h) - (i + j);
    * Compiled MIPS code (assembly):
      * add $t0, $s1, $s2
      * add $t0, $s3, $s4
      * sub $s0, $t0, $t1
* 레지스터 피연산자: MIPS 32 레지스터(Register Operands: MIPS 32 Registers)
* 메모리 피연산자(Memory operands)
  * 메인 메모리는 배열, 구조체와 같은 복합적인 데이터를 저장하는 데 사용된다. 프로세서 밖에 위치하기 때문에 빠르게 데이터에 접근이 불가능하다. 산술 연산은 레지스터 피연산자를 사용한다고 했으므로, 이 데이터들로 산술연산을 하기 위해선 메모리에서 레지스터로 값을 가져와야 한다. 이때 메모리는 byte 단위의 주소(address)로 접근 가능하다.
    * MIPS는 Big Endian 방식을 사용한다. Big Endian이란 MSB(Most-significant byte)를 앞에 적는 방식이다.
* 예제를 통해 어떻게 메모리에 저장된 데이터의 산술 연산을 할 수 있는 지 알아보자
  * 예제 2.2.4
    * C code:
      * A[12] = h + A[8];
    * Compiled MIPS code:
      * lw $t0, 32($s3) # $s3에 저장된 주소값으로 메모리에 접근해서, 그로부터 +32byte 떨어진 곳에 저장된 데이터를 $t0로 가져온다.
      * add $s1, &s2, $t0 # 이로써 메모리에 저장된 데이터 값을 이용해 산술 연산을 할 수 있다.
      * sw $t0, 48($s3) # $s3에 저장된 주소값으로 메모리에 접근해서, 그로부터 +48byte 떨어진 곳에 $t0에 저장된 데이터를 저장한다.
## 2.4 Signed and Unsigned Numbers
<!--5-2강-->
## 2.5 Representing Instructions in the Computer
## 2.6 Logical Operations
## 2.7 Instructions for Making Decisions
<!--5-3강-->
## 2.8 Supporting Procedures in Computer Hardware
<!--5-4강-->
## 2.9 Communicating with People
## 2.10 MIPS Addressing for 32-bit Immediates and Addresses
## 2.11 Parallelism and Instructions: Synchronization
<!--5-5강-->
## 2.12 Translating and Starting a Program
## 2.13 A C Sort Example to Put It All Together
## 2.14 Arrays versus Pointers

## 2.15 Advanced Material: Compiling C and Interpreting Java
## 2.16 Real Stuff: ARMv7 (32-bit) Instructions
## 2.17 Real Stuff: x86 Instructions
## 2.18 Real Stuff: ARMv8 (64-bit) Instructions
## 2.19 Fallacies and Pitfalls
## 2.20 Concluding Remarks
## 2.21 Historical Perspective and Further Reading
## 2.22 Exercises
