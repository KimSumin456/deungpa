---
title:  "[운영체제] 11. Synchronization (1)"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Synchronization
---

## Preview
* Introduction [p2]
* The Classic Example [p3], An Example from a Real Program [p6]
* Synchronization Problem [p7]
  * Critical Section [p9]
* Locks [p10]
  * An Initial Attempt [p13]
  * Software-only Algorithm [p15]
  * Peterson’s Algorithm [p16]
  * Disabling Interrupts [p19]
  * Test-And-Set [p20], Compare-And-Swap [p22]
* Wrap up [p23]

<!--11강 Synchronization (1)-->
## 11.0 Introcution
* 시스템에서 프로세스 안의 여러 개의 스레드들이 돌고있다고 가정합니다
* 스레드들은 주소 공간을 공유합니다
* 스레드들은 같은 데이터를 동시에 접근할 수 있습니다
* 스레드가 공유 데이터를 변경하면 문제(Synchronization Issue)가 발생할 수 있습니다

## 11.1 The Classic Example
The Classic Example
* Synchronization Issue in 은행 예제

An Example from a Real Program
* 코드 한 줄이라도도 인스트럭션 여러 줄이 되어 Synchronization Issue가 발생할 수 있습니다

## 11.2 Synchronization Problem
Synchronization Problem
* 문제: Concurrency는 연산 결과를 불확실하게 만듭니다
  * 두 개 이상의 concurrent한 스레드들이 공유 리소스(shared resouce)에 접근하고 조작하며 **race condition**을 발생시킵니다
  * 양자영학에서 불확정성의 원리를 제안한 하이젠베르그에 빗대어 race condition으로 인해 발생하는 문제를 하이젠버그(Heisenbugs)라고도 합니다
* 해결책: 공유 리소스를 제어하기 위한 **synchronization** (or coordination) mechanism이 필요합니다

Synchronization in Operating Systems
* 운영체제는 공유 리소스로 가득 차 있고, concurrent하게 race condition이 발생할 수 있는 최적의 조건을 가지고 있습니다

Critical Section
* **critical section** (or critical region)이란 공유 리소스에 접근하는 코드 부분입니다
* 정확한 실행을 위해 critical section에서 **mutual exclusion**을 보장해야 합니다
  * **mutual exclusion**이란 한 번에 한 스레드만 critical section에서 실행할 수 있어야 한다는 성질(property)입니다
  * 다른 스레드들은 critical section의 입구에서 대기해야 하고, 앞의 한 스레드가 critical section을 떠났을 때 다른 한 스레드가 입장할 수 있습니다

## 11.3 Locks
Locks
* **lock**이란 메모리에서 다음과 같은 두 연산을 통해 mutual exclusion을 제공하는 오브젝트입니다
  * void acquire(): lock이 풀릴 때까지 기다린 후, lock을 잡습니다
  * void release(): lock을 풀고, acquire()에서 기다리는 아무 스레드를 하나 깨워줍니다

Using Locks
* lock을 통해 mutual exclusion property를 제공함으로써 race condition 해결

Requirements for Locks
1. Correctness
* **Mutual exclusion**: 한 번에 하나의 스레드만 critical section에 있어야 합니다
* **Progress**: 만약 여러 개의 스레드들이 같은 critical section에 들어가고 싶어한다면, 반드시 한 스레드는 입장을 할 수 있어야 합니다 (양보만 하다 아무도 안 들어가면 안 됩니다)
* **Bounded wating**: starvation-free(starvation으로부터 자유로워야 합니다. stravation이 발생하면 안 됩니다.); 대기 중인 스레드는 언젠가는 자기 차례가 와서 들어갈 수 있어야 합니다
2. Fairness
* 각 스레드들은 lock을 획득하기 위한 기회를 공정하게 얻어야 합니다
3. Performance
* lock의 time overhead가 너무 크면 안 됩니다.

### 11.3.1 An Initial Attempt
: **Spinlock** 구현 1 (Failed)

```c
struct lock { int held = 0; }

void acquire(struct lock *l) {
  while (l->held);
  l->held = 1;
}

void release(struct lock *l) {
  l->held = 0;
}
```

* `acquire()` 함수를 호출한 스레드는 lock이 release 되기를 **busy-waits** (or spins) 합니다

* Does this work? **No.**
  * T1, T2가 동시에 held 값에 접근하면 mutual exclusion property가 보장되지 않습니다

### 11.3.2 Software-only Algorithm
Implementing Locks
* Software-only algorithms *-> 11.3.2에서 살펴봅니다*
  * Peterson's algorithm *-> 11.3.3에서 살펴봅니다*
  * ...
* Hardware approaches
  * Disable interrupts *-> 11.3.4에서 살펴봅니다*
  * Hardware atomic instructions *-> 11.3.5에서 살펴봅니다*
    * Test-And-Set
    * Compare-And-Swqp

---

Software-only Algorithm
: Spinlock 구현 2 (Faild)
- 가정:
  - load와 store 인스트럭션이 atomic하다
  - my_id는 0 또는 1의 값만 가진다

```c
int interested[2] = {FALSE, FALSE};

void acquire(int my_id) { /* my_id is 0 or 1 */
  int other = 1 – my_id;
  interested[my_id] = TRUE;
  while (interested[other]);
}

void release(int my_id) {
  interested[my_id] = FALSE;
}
```

* Does this work? **No.**
  * T1, T2가 동시에 acquire를 하면 progress property가 보장되지 않습니다

### 11.3.3 Peterson's Algorithm
: Spinlock 구현 3 - Software-only Algorithm 개선 (Particially Success)

```c
int turn;
int interested[2] = {FALSE, FALSE};

void acquire(int my_id) { /* my_id is 0 or 1 */
  int other = 1 – my_id;
  interested[my_id] = TRUE;
  turn = other;
  while (interested[other] && turn == other);
}

void release(int my_id) {
  interested[my_id] = FALSE;
}
```

* Does this work? **Yes.**
  * 일반적으로 bounded wating도 보장된다고 봅니다

* 2개의 태스크에 대해서만 critical section 문제를 해결할 수 있습니다
* 가정이 많아서 적용할 수 있는 상황이 제한적입니다
  - load와 store 인스트럭션이 atomic하지 않은 경우도 많습니다
  - x86을 제외한 일부 아키텍처에서는 my_id 값을 동시에 대입하면 0도 1도 아닌 값을 가지게 되기도 합니다

### 11.3.4 Disabling Interrupts
Synchronization Hardware
* 현대 컴퓨터 아키텍처는 너무 복잡해서 Software-only Algorithm에서 세우는 가정들이 성립하지 않습니다
  * 심지어 성능을 위해 인스트럭션의 순서를 바꿔서(reordered) 실행하기도 합니다
    * (컴퓨터 구조 강의에서 배웁니다)
* 그리고 두 개 이상의 멀티 스레드 환경에서도 쓸 수 있는 알고리즘이 필요합니다
* 그렇기 떄문에 현대 컴퓨터에서 lock은 Hardware의 도움을 받아서 처리합니다

---

Disabling Interrupts
: critical section에 들어갈 땐 timer interrupt를 꺼버리자

* context switching(timer interrupt -> scheduler -> preemption)이 원인었으니, crticial section에 들어 갈 땐 timer interrupt를 꺼버림으로써 해결하자
* critical section을 atomically 실행함으로써 mutual exclusiveness를 간접적으로 보장합니다
  * atomically(atomic하게)란: all or nothing. crticial section의 처음부터 끝까지를 실행 할 거면 하나가 한 번에 다 하거나, 않을 거면 아예 시작하지도 말거나

* 문제점
  * 커널 모드에서만 interrupt를 제어할 수 있습니다
  * 멀티 프로세서 환경에서 실용적이지 못합니다 (모든 CPU가 interrupt를 다 꺼야하므로 오래 걸립니다)
* 그래서 커널(운영체제) 내에서 제한적인 방식으로만 Disabling interrupt를 통해 mutual exclusion을 보장합니다

### 11.3.5 Test-And-Set, Compare-And-Swap
: 그냥 디지털 회로 차원에서 Atomic instruction을 만들자

Atomic instruction
* Read-modify-write 연산이 atomically 실행되도록 보장되어 있는 인스트럭션
* 모든 현대 컴퓨터들의 lock은 Atomic Instruction을 통해 구현되어 있습니다

---

Test-And-Set instruction
* 새로운 값(new value)으로 업데이트 하는 동시에 메모리에 있던 이전 값(old value)을 반환합니다
* 한국어, 영어, 프랑스어가 아니라 C언어로 이 인스트럭션의 기능(≠동작)을 설명하자면 다음과 같습니다.
* ```c
  int TestAndSet(int *v, int new) {
    int old = *v;
    *v = new;

    return old;
  } 
  ```

Using Test-And-Set
: Spinlock 구현 4 (Sucess)

```c
struct lock { int held = 0; }

void acquire(struct lock *l) {
  while (TestAndSet(&l->held, 1));
}

void release(struct lock *l) {
  l->held = 0;
}
```

* Test-And-Set 인스트럭션을 사용해 간단하게 spinlock을 구현할 수 있습니다

Compare-And-Swap
* 이전 값이 원하는 값(expected value)과 같을 때만 새로운 값으로 업데이트하고 메모리에 있던 이전 값을 반환합니다

Using Compare-And-Swap
: Spinlock 구현 5 (Sucess)

```c
int CompareAndSwap(int *v, int expected, int new) {
  int old = *v;
  if (old == expected)
    *v = new;
  return old;
}

void acquire(struct lock *l) {
  while(CompareAndSwap(&l->held, 0, 1)); // &l->held가 0이면 1로 교체하고 이전 값(0)을 리턴
}
```

## 11.4 Wrap Up
* Synchronization, critical sections, race condition
* Mutual exclusion
* Lock
  * Software-only
    * Peterson’s Algorithm
  * Hardware support
    * Disabling Interrupts
    * Test-And-Set, Compare-And-Swap (Atomic Instruction)