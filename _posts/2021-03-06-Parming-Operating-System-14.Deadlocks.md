---
title:  "[운영체제] 14. Deadlocks"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Deadlocks
---

## Preview
*	Deadlock
    * Resources
    * Deadlock Problem
    * Conditions for Deadlock
* Strategies for Handling Deadlocks
  * Deadlock Prevention
  * Deadlock Avoidance
    * Safe State Example
    * Avoidance Algorithms
      * Resource-Allocation Graph
      * Banker’s Algorithm
  * Deadlock Recovery
  * Ignoring Deadlock

<!--14강 Synchronization (3)-->
## 11.1 Deadlock
Deadlock
* 데드락(Deadlock): 두 개 이상의 작업(task)이 서로 상대방의 작업이 끝나기 만을 기다리면서 아무것도 완료되지 못하는 상태를 가리킵니다. 프로세스가 잘못된 순서로 리소스를 가져갈 때 발생합니다.
  * [교착상태 - 위키백과](https://ko.wikipedia.org/wiki/%EA%B5%90%EC%B0%A9_%EC%83%81%ED%83%9C)
* 예
  ```
  Thread 0          Thread 1
  acquire(A);       acquire(B);
  acquire(B);       acquire(A);
  ```
* 상대방이 먼저 리소스를 놓기를 기다리며 교착상태에 빠집니다. 마치 초등학교에서 필통 인질을 맞교환하던 때와 똑같습니다.

Resources
* 리소스란 하드웨어 및 소프트웨어를 abstraction한 모든 것이라고 할 수 있습니다. 컴퓨터는 리소스들의 집합으로 이루어져 있고, 운영체제가 그 리소스들을 관리한다고 할 수 있습니다.
* CPU cycles, memory space, I/O devices 등 모든 것이 리소스입니다.

Deadlock Problem
* 데드락은 다음과 같은 상황에서 발생할 수 있습니다.
  * tasks가 하나 이상의 리소스들을 요구해야 합니다
  * blocked tasks는 리소스를 잡은 채로 다른 tasks가 잡고있는 리소스를 waiting해야 합니다.

### Conditions for Deadlock
* 데드락은 다음과 같은 4가지 조건을 모두 만족할 때 발생합니다
1. Mutual exclusion
* 한 번에 한 작업만 리소스를 사용할 수 있다
2. Hold and wait
* 작업은 리소스를 잡은 채로 다른 작업이 잡고있는 리소스를 기다린다
3. No preemption
* 리소스는 작업을 완료한 뒤 자발적으로만 release된다
4. Circular wait
* waithing tasks들 간의 릴레이션(relation)에 cycle이 발생한다

Conditions for Deadlock 사례 분석
* -1. 사거리 도로
* -2. Dining Philosophers Problem

## 11.2 Strategies for Handling Deadlocks
Deadlocks never happen: 데드락이 아예 발생하지 않도록 하기

1. Deadlock prevention -> 11.2.1
* conditions for deadlock의 4가지 중 1가지를 불만족시켜 데드락 발생 가능성을 조각냅니다
2. Deadlock avoidance -> 11.2.2
* 상황을 보고 리소스 요청을 승인 또는 거부합니다

Deadlocks may happen: 데드락이 발생하면 수습하기

3. Deadlock detection and recovery -> 11.2.3
* 시스템이 데드락에 빠지는 걸 지켜보고 복구합니다
4. Just ignore the problem altogether -> 11.2.4
* 문제를 완전히 무시합니다

### 11.2.1 Deadlock Prevention
* Deadlock Prevention: 데드락은 필수적인 conditions for deadlock 네 가지를 모두 만족할 때만 발생합니다. 이를 반대로 생각해 한 가지 조건을 불만족시켜 데드락을 예방합니다.
1. Mutual exclusion 불만족시키기
* 리소스 고유의 특징이라 어떻게 할 수 없습니다
2. Hold and wait 불만족시키기
* 모든 리소스를 한 번에 잡아야 사용할 수 있고, 그렇지 않으면 내려놓아야 합니다
  * 장점: 구현이 쉽습니다
  * 단점: 효율이 낮습니다, starvation이 발생 가능합니다
3. No preemption 불만족시키기
* 역시 리소스 고유의 특지이라 어떻게 할 수 없습니다
4. Circular wait 불만족시키기
* 모든 리소스 타입에 대해 **total ordering**를 매깁니다. 매겨진 숫자의 오름차순대로만 리소스를 가져갈 수 있게 합니다.
* 이렇게 하면 역방향의 waiting이 절대 발생하지 않습니다

Deadlock Prevention 예제 - Circular wait 불만족 시키기
1. two-phase locking (2PL)
2. overlap lock acquistion and release
* 강의노트 참고

### 11.2.2 Deadlock Avoidance
* Deadlock Avoidance: safe state가 예상될 때만 리소스를 할당해줍니다.

* safe state: safe sequence 경우의 수가 한 가지라도 있는 상태를 말합니다.
* safe sequence: 데드락이 발생하지 않고 시스템이 모든 프로세스에게 순차적으로 리소스를 할당해줄 수 있는 경우를 말합니다.

Safe State Example
A. initial state
B. safe state (Deadlock Avoidance 성공 예제)
C. unsafe state (Deadlock Avoidance 실패 예제)
* 강의노트 참고

Avoidance Algorithms
* 문제점
  * 사실 프로세스가 리소스 몇 개를 더 필요로 할 지 알 수 없습니다
  * 리소스 효율성이 떨어집니다
  * 'safe sequence'를 어떻게 찾아야하는 지 생각해보아야 합니다

A. Resource-Allocation Graph
* 버택스(vertex)는 프로세스와 리소스 타입 및 리소스 개수를, 엣지(edge)는 request edge, assignment edge, claim edge를 나타냅니다.
* 만약 request edge와 assignment edge가 cycle을 만들며 데드락이 발생하는 것입니다.

Resource-Allocation Graph Example
* 강의노트 참고

B. Banker’s Algorithm
* Total resources, Allocation, Max, Need, Available resources를 그려서 합니다.
* multiple instances에도 사용가능 합니다

Banker’s Algorithm Example
* 강의노트 참고

### 11.2.3 Deadlock Recovery
* Deadlock Recovery: 데드락이 발생하고 나면 수습하기
* 데드락과 연관된 모든 것을 하나씩 죽이거나, 모두 죽이거나 할 수 있습니다.
* 그러나 실질적으로 잘 쓰기 어렵습니다.

### 11.2.4 Ignoring Deadlock
* Ignoring Deadlock: 다 쌩 까기
* The "Ostrich" algorithm
* **모든 현대 운영체제가 이 접근 방식을 사용하고 있습니다 (일부 중요한 리소스 제외)**
  * 데드락이 거의 잘 발생하지 않기 때문입니다
  * 데드락 핸들링의 비용이 너무 크기 때문입니다
* convenience와 correctness 사이의 Trade-off입니다