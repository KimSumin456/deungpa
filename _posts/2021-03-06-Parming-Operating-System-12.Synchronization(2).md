---
title:  "[운영체제] 12. Synchronization (2)"
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
*	Summary of the last class
* Higher-level Synchronization
  * Mutex Lock
    * Busy-wait
    * blocked
  * Semaphore
    * Implementing Busy-waiting Semaphore, Implementing Blocking Semaphore
    * Types of Semaphores
    * Problems with Semaphores
  * Monitors
  * Condition Variables
  * Pthreads Synchronization
*	Deadlock

<!--12강 Synchronization (2)-->
## 12.0 Summary of the last class
* critical section, race condition
* synchronization
* mutual exclusion, progress, fairness

## 12.1 Higher-level Synchronization
Synchronization Primitives

### 12.1.1 Mutex Lock
Mutex Lock
* 'Mut'ual 'ex'clusive lock
* 연산
  * `acquire()`: lock을 얻습니다
  * `release()`: lock을 놓습니다
* 방식
  * busy-wait (=spinlock)
  * blocked

Spinlock
* busy-wait 방식의 mutex lock을 spinlock이라고 합니다. lock을 얻을 때까지 계속 문고리를 돌리는 방식입니다.
* 장점
  * 구현하기 쉽습니다
    * 따라서 임베디드 시스템에 적합합니다
  * overhead가 작습니다
    * 짧은 critical sections을 보호하기에 적합합니다
    * 반대로 말해 긴 critical sections을 보호하는데 쓰기엔 부적합니다

### 12.1.2 Semaphore
Semaphore
* 여러 개의 스레드를 synchronization 하는 방식입니다.
* 연산
  * 초기 값으로 정수값 S를 가지고 시작합니다
  * `wait()`: S를 1 감소시키고, S >= 0이 될 때까지 기다립니다(blocked 됩니다).
  * `signal()`: S를 1 증가시킵니다

Implementing Busy-waiting Semaphore
```c
struct semaphore {
  int S;
};

void wait(struct semaphore *sem) {
  while (sem->S <= 0); // S - 1 >= 0이 될 때까지 기다립니다 (S는 정수이므로 같은 의미입니다)
  sem->S--; // busy-waiting에서는 나중에 S를 1 감소시키는게 맞습니다
}

void signal(struct semaphore *sem) {
  sem->S++;
}
```
* This is not working (race condition이 발생합니다)
  * lock의 lock이 필요합니다

Implementing Blocking Semaphore
```c
struct semaphore {
  int S;
  struct task *Q;
};

void wait(struct semaphore *sem) {
  sem->S--;
  if (sem->S < 0) {
    add_this_task_to(sem->Q);
    block();
  }
}

void signal(struct semaphore *sem) {
  sem->S++;
  if (sem->S <= 0) {
    P = remove_a_task_from(sem->Q);
    wakeup(P);
  }
}
```
* This is not working (sem->S 값에서 race condition이 발생합니다)

Types of Semaphores
* Binary semaphore (≒ mutex)
  * S의 초기화 값이 1인 세마포어
  * mutual exclusive를 보장합니다
* Counting semaphore
  * S의 초기화 값이 N인 세마포어
  * N개의 스레드만 critical section로 입장할 수 있는 것을 보장합니다
  * **하지만 crticial section 내에서 N개의 스레드들끼리의 mutual exclusive는 보장하지 않습니다**

Problems with Semaphores
* 일반인들에게 구조적으로 안전성을 보장해주지 못합니다. SW Engineer 관점에서 별로 좋지 않습니다.
* 세마포어는 변수 차원이 아니라 섹션 차원에서 보호합니다. 배치를 알아서 잘 해야합니다.
* 기능의 목적이 명확하지 않습니다. 보호가 아니라 제어에 활용되기도 합니다.

### 12.1.3 Monitors
* 프로그래밍 언어 차원에서 공유 데이터 접근 제어를 지원해주는 방식입니다

```c
monitor my_monitor {
  /* Shared variables */
  procedure P1(...) {
    ...
  }
  procedure P2(...) {
    ...
  }
  procedure P3(...) {
    ...
  }
  init_code(...) {
    ...
  }
}
```
* 모니터 안의 variable, function 중 하나만 한 번에 접근할 수 있게 제어해줍니다.
* 보기에 좋고, 쓰기에도 편합니다.
* 그러나 제한적입니다.

### 12.1.4 Condition Variables
* 이벤트를 기다림으로써 스레드가 제어되는 방식입니다. 섹션 차원이 아닌 흐름 차원에서 제어합니다.
* 연산
  * `wait()`: `signal()`을 할 때까지 기다립니다
  * `signal()`: `wait()` 하고있는 스레드들 중 하나를 깨웁니다
    * `signal()`의 유실을 조심해야 합니다.
  * `boradcast()`: `wait()` 하고있는 스레드들 전부를 깨웁니다

### 12.1.5 Pthreads Synchronization
Pthreads
* Pthreads는 스레드  synchronization 관련 라이브러리입니다.

Pthreads Example
* 강의 노트 참고

## 12.2 Deadlock
* 두 개 이상의 태스크가 하나씩만 실행할 수 있는 이벤트를 서로 무한정 기다리게 되는 상황입니다.
* synchronization을 잘못하면 발생할 수 있습니다