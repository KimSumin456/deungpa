---
title:  "1.Computer Abstractions and Technology"
excerpt: "등록금 파먹기 - 컴퓨터 구조 파먹기 (Parming Computer Architecture)"
toc: true
toc_sticky: true

categories:
- 컴퓨터 구조
tags:
- 등록금 파먹기
- 컴퓨터 구조
- Computer Abstractions and Technology
---

[작성 중]

## 1.1 Introduction
* 컴퓨터 혁명(The Computer Revolution)
  * feasible, pervasive 새로운 응용을 실현 가능할 수 있게 되었고, 널리 보급되었다

* 무어의 법칙 (1965) (Moore's Law (1965))
  * "칩당 트랜지스터의 개수는 매 18개월마다 두 배가 될 것이다"

* 컴퓨터의 종류 (Classes of Computers)
  * 데스크탑 컴퓨터
  * 서버 컴퓨터
  * 임베디드 컴퓨터

* 포스트PC 시대 (The PostPC Era)
  * PC→ 휴대폰↓ 스마트폰↑ 태블릿↑

* 무엇을 배울 것인가 (What You Will Learn)
  * 어떻게 프로그램(program)이 기계어(machine language)로 번역되는지
    * 그리고 어떻게 하드웨어가 기계어를 실행하는지
  * 하드웨어/소프트웨어 인터페이스
  * 프로그램 성능을 평가하는 방법
    * 그리고 어떻게 프로그램 성능을 높일 수 있는지
  * 병렬 프로세싱

* 성능의 이해 (Understanding Performance)
  * 알고리즘
    * 실행되는 연산의 개수를 결정한다
  * 프로그래밍 언어, 컴파일러, 구조
    * 연산당 실행되는 인스트럭션의 개수를 결정한다
  * 프로세서와 메모리 시스템
    * 인스트럭션이 실행되는 속도를 결정한다
  * (OS를 포함한) 입출력 시스템
    * 입출력 연산이 실행되는 속도를 결정한다

## 1.2 Eight Great Ideas in Computer Architecture
1. Design for Moore's Law
2. Use Abstraction to Simplify Design
3. Make the Common Case Fast
4. Performance via Paralleslism
5. Performance via Pipelining
6. Performance via Prediction
7. Hierarchy of Memories
8. Dependability via Redundancy

## 1.3 Below Your Program
* Below Your Program (Below Your Program)
  * 애플리케이션 소프트웨어
    * High-Leve Language(HLL)로 쓰여짐
  * 시스템 소프트웨어
    * 컴파일러가 HLL를 machine code로 번역한다
    * 운영체제의 서비스 코드
      * 입출력 핸들링
      * 메모리와 스토리지 관리
      * 작업 스케쥴링 & 자원 공유
  * 하드웨어
    * 프로세서, 메모리, I/O 컨트롤러

* 프로그램 코드의 계층 (Levels of Program Code)
  * High-level language
    * C언어
  * Assembly language
    * 어셈블리어(인스트럭션으로 된 표현)
  * Hardware representation
    * 기계어(바이너리 코드)

## 1.4 Under the Covers
* 컴퓨터의 구성 요소 (Components of a Computer)
  * input, output, memory, datapath, control
* 본체 열기 (Opening the Box)
* 프로세서 내부 (CPU) (Inside the Processor (CPU))
  * Datapath: 데이터에 대한 연산을 수행
  * Control: datapath, memory 등 제어
  * Cache memory: 데이터에 즉시 접근할 수 있는 작고 빠른 (비싼) SRAM 메모리
* 추상화 (Abstractions)
  * 추상화는 복잡함을 해결해준다
    * 계층화를 통해 하위 레벨을 세세히 신경 쓰지 않아도 분업할 수 있게 해준다
  * Instruction set architecture (ISA)
    * The hardware/software interface
  * 애플리케이션 바이너리 인터페이스
    * ISA + 시스템 소프트웨어 인터페이스
  * 구현
    * 기본 세부사항과 인터페이스
* 데이터를 위한 안전한 장소 (A Safe Place for Data)
  * 휘발성 메인 메모리(주 기억장치)
    * 전원이 꺼지면 인스트럭션과 데이터가 날아간다
    * 예) DRAM
  * 비휘발성 보조 메모리(보조 기억장치)
    * 전원이 꺼지면 인스트럭션과 데이터가 날아가지 않는다
    * 예) 마그네틱 디스크, 플래시 메모리, 옵티컬 디스크(CDROM, DVD)
* 네트워크 (Networks)
  * 커뮤니케이션과 리소스 공유
  * 근거리 통신망(LAN): 이더넷
    * 건물 내
  * 광대역 통신망(WAN): 인터넷
  * 무선 네트워크: WiFi, Bluetooth

## 1.5 Technologies for Building Processors and Memory
* 기술 동향: 프로세서 및 디스크 (Technology Trends: Processor and Disk) / 메모리 (Technology Trends: Memory)
  * 프로세서는 계속해서 빨라지고 있는데 메모리는 못 따라가고 있고, 그 차이가 점점 커지고 있다
* 반도체 기술 (Semiconductor Technology)
* 제조용 ICs (Manufacturing ICs)
* Intel Core i7 우퍼 (Intel Core i7 Wafer)
* 프로그램 구성 (Program Compilation)
  * 프로그램: 고급 프로그래밍 언어로 작성됨
  * 컴파일러: 프로그램을 어셈블리어로 변환
* 어셈블리어와 기계어 (Assmbly & Machine Language)
  * 어셈블리어: 사람이 읽을 수 있는 표현
  * 기계어: 기계가 읽을 수 있는 표현, 1과 0으로 이루어짐
  * 어셈블러: 어셈블리어를 기계어로 변환
* 인스트럭션 코드 (Instructions Codes)
  * 프로그램은 일련의 인스트럭션들이다
  * 인스트럭션은 컴퓨터에게 특정한 연산을 수행하도록 지시하는 비트 그룹이다
  * 프로그램의 인스트럭션들은 필요한 데이터와 함께 메모리에 저장된다
* 인스트럭션 코드의 예 (Example of Instruction Codes)
* 어떻게 컴퓨터는 인스트럭션을 실행하는가? (How Does Computer Execute the Instructions?)
  * 메모리에 저장되어 있는 인스트럭션이 CPU로 올라가서 실행된다
* 저장된 프로그램 개념 (Stored Program Concept)
  * 프로그램 자체는 하드 디스크에 저장되어 있다가, 전원을 켜고 필요하면 메인 메모리에 올라가고, 프로세서에서 실행된다

## 1.6 Performance
* 성능의 정의 (Defining Performance)
  * 컴퓨터의 성능은 어떻게 나타내야할까?
* 응답 시간과 처리량 (Response Time and Throughput)
  * Response time: 한 작업을 수행하는 데 걸리는 시간으로
    * 프로세서의 속도를 빠르게 하면 Response time을 줄일 수 있을 것이다
  * Throughput: 단위 시간 당 수행한 작업들의 개수로
    * 프로세서의 개수를 늘리면 throughput을 늘릴 수 있을 것이다
  * 우리는 response time으로 성능을 나타낼 것이다
* 상대적 성능 (Relative Performance)
  * 정의
    * Relative Performance = 1 / Execution Time
    * Performance~X~/Performance~Y~ = Execution time~Y~/Execution time~X~이면 "X 가 Y보다 n배 빠르다"라고 한다.
  * 예제
    * 프로그램을 실행하는 데 걸리는 시간이 A는 10초, B는 15초이다. 그러면 Execution Time~B~ / Execution Time~A~ = 15s / 10s = 1.5이므로, A는 B보다 1.5배 빠르다라고 말할 수 있다.
* 실행시간 측정 (Measuring Execution Time)
  * Elapsed time = (total) response time
    * 프로세싱 그리고 입출력, 운영체제 오버헤드, 낭비한 시간, 기타 등등을 모두 포함한 시간을 말한다
    * 시스템 성능(system performance)를 결정한다
  * CPU time = (total) response time - 프로세싱 이외의 시간
    * 입출력, 기타 등등 시간은 제외한 시간을 말한다
    * 사용자 CPU 시간(user CPU time)과 시스템 CPU 시간(system CPU time)으로 구성된다
* CPU 클럭킹 (CPU Clocking)
  * clock period = clock cycle = clock = cycle
  * clock frequency = clock rate = 1 / clock cycle
* CPU 시간 (CPU Time)
  * CPU execution time = CPU time = CPU clock cycle * clock cycle time = CPU clock cycle / clock rate
* CPU 시간 예제 (CPU Time Example)
  * 컴퓨터 A는 2GHz clock, 10s CPU time이다. 새 컴퓨터 B를 디자인 하는데 6s CPU time으로 맞추려고 한다. 컴퓨터 B는 clock을 빠르게 할 수 있지만, 1.2 * clocky cycles이 걸린다. 그러면 컴퓨터 B는 clock을 얼마나 빠르게 해야할까?
    * Clock Rate~B~ = Clock Cycle~B~ / CPU Time~B~ = 1.2 * Clock Cycles~A~ / 6s
    * Clock Cycles~A~ = CPU Time~A~ * Clock Rate~A~ = 10s * 2GHz = 20 * 10^9
    * Clock Rate~B~ = 1.2 * 20 * 10^9^ / 6s = 24 * 10^9 / 6s = 4GHz
    * clock~B~를 4GHz로 해야한다.
* 인스트럭션 개수와 CPI (Insruction Count and CPI)
  * CPI(Clock cycle Per Instruction) = clock cycle / instruction
  * CPU clock cycle = IC(Instruction Count) * CPI
  * CPU execution time = IC * CPI * clock cycle time
* CPI 예제 (CPI Example)
  * 컴퓨터 A는 Cycle Time = 250px, CPI = 2.0이고, 컴퓨터 B는 Cycle Time = 500ps, CPI = 1.2이다. ISA는 같다. 누가, 얼마나 빠른가?
    * CPU Time~A~ = IC * CPI~A~ * Cycle Time~A~ = I * 2.0 * 250ps = I * 500ps
    * CPU Time~B~ = IC * CPI~B~ * Cycle Time~B~ = I * 1.2 * 250ps = I * 600ps
    * CPU Time~B~ / CPU Time~A~ = I * 600ps / I * 500ps = 1.2
    * A가 1.2배 빠르다
* CPI 자세히 알아보기 (CPI in More Detail)
  * 위에선 CPI가 동일하다고 가정했지만 사실 instruction class마다 다르다.
    * Clock Cycle =
      $$
      \sum\limits_{i=1}^{n} {CPI~i~ * IC~i~}
      $$
  * Weighted average CPI
    * Relative frequency를 이용해 더 정확하게 계산할 수 있는 방법
    * CPI = Clock Cycles / IC = 
      $$
      \sum\limits_{i=1}^{n} {CPI~i~ * (IC~i~ / IC)}
      $$
* CPI 자세한 예제 (CPI Example)
  * (생략)
  * 이렇게 instruction class마다 CPI가 다르다
* 성능 요약 (Performance Summary)
  * CPU Time = (Instructions / Program) * (Clock cycles / Instruction) * (Seconds / Clock cycle) = (IC) * (CPI) * (Clock Cycle Time)
  * 성능에 영향을 주는 요인
    * 알고리즘: IC, CPI에 영향을 미친다
    * 프로그래밍 언어: IC, CPI에 영향을 미친다
    * 컴파일러: IC, CPI에 영향을 미친다
    * ISA: IC, CPI, Clock rate에 영향을 미친다

## 1.7 The Power Wall
* 파워 트렌드 (Power Trends)
* 단일프로세서 성능 (Uniprocessor Performance)
* 파워 축소 (Reducing Power)
* 멀티프로세서 (Multiprocessors)
* 주의: 암달의 법칙 (Pitfall: Amdahl's Law)
* 최근 컴퓨터 구조의 진화 (Recent Evolution of Computer Architecture)
* 컴퓨터 구조의 미래 (Future of Computer Architecture)

## 1.8 The Sea Change: The Switch from Uniprocessors to Multiprocessors
## 1.9 Real Stuff: Benchmarking the Intel Core i7
## 1.10 Fallacies and Pitfalls
## 1.11 Concluding Remarks
## 1.12 Historical Perspective and Further Reading
## 1.13 Exercises

* Summary