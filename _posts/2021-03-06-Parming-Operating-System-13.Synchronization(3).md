---
title:  "[운영체제] 13. Synchronization (3)"
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
*	Recap the last session
* Compiler and Synchronization
* Classical Problems of Synchronization
  * Bounded Buffer Problem
  * Readers-Writers Problem
  * Dining Philosophers Problem
* Preemptive vs. Non-preemptive in Kernel
* Synchronization in Linux

<!--13강 Synchronization (3)-->
## 11.0 Recap the last session
* Synchronization primitives
  * Mutes
  * Semaphore
  * Busy-waithing vs. blocking
  * Monitor
  * Conditional variable
* Deadlock

## 11.1 Compiler and Synchronization
Compiler and Synchronization
* 컴파일러의 최적화로 인해 Synchronization에 문제가 발생할 수 있습니다

Volatile type
* 프로세서는 메인 메모리보다 더 빠르게 접근할 수 있는 메모리인 레지스터를 가지고 있습니다. 컴파일러는 실행을 최적화하기 위해 자주 쓰는 변수를 레지스터에 올립니다.
* 이로 인해 `wait()`를 실행한 뒤 `ready` 값이 레지스터로 올라가게 되면, `signal()`를 실행해도 메인 메모리에 있는 `ready` 값만 변경되기 때문에 무한 루프를 도는 문제가 발생할 수 있습니다.
* 코드로 보면 다음과 같습니다.
  * C언어
    ```c
    bool ready = false;
    
    void wait(void) {
      while (ready == false) // 여기서 무한 루프에 빠집니다
      do_nothing();
    }
    
    void signal(void) {
      ready = true;
    }
    ```
  * 어셈블리어 (절망편)
    ```
    ld ready, $reg0
    again: bne $reg0, false, exit
    loop
    j again
    ```
* volatile type qualifier는 컴파일러에게 변수에 접근할 때마다 메모리에서 읽어오는 인스트럭션을 생성하도록(컴파일하도록) 지시합니다. 이를 통해 위의 문제를 해결할 수 있습니다.
  * 싱글 스레드에선 필요하지 않습니다!

Memory barrier (barrier)
* 컴파일러는 parallelism을 최대화하기 위해 인스트럭션의 순서를 바꿉니다.
* 이로 인해 문제가 발생할 수 있습니다.
* 코드로 보면 다음과 같습니다.
  * C언어
    ```c
    node->value = 5;
    ...
    node->valid = true;
    node->value = 10;
    test_and_set(&list->tail, node);
    ```
  * 어셈블리어 (절망편)
    ```bash <!--걍 색깔 이뻐서 이거 해놓음-->
    node = list->tail;
    assert(node->true == true);
    node->valid = true;
    ```
* memory barrier (barrier)는 컴파일러나 프로세서에게 순서를 재배치하지 않도록 강제합니다. 이를 통해 문제를 해결할 수 있습니다.

## 11.2 Classical Problems of Synchronization
* 11.2.1 Bounded Buffer Problem
* 11.2.2 Readers-Writers Problem
* 11.2.3 Dining Philosophers Problem

### 11.2.1 Bounded Buffer Problem
Bounded Buffer Problem
* Bounded buffer problem은 producer/consumer problem의 일부입니다.
* Producer/consumer problem
  * Producers가 꽉 찬 buffer에 리소스를 더 삽입하려 하거나, Consumer가 빈 buffer에서 리소스를 더 제거하려고 할 때 발생하는 문제입니다.
  * buffer는 pruducers와 consumers에게 공유되는 리소스입니다.
    * unbound buffer와 bound buffer가 있습니다.
  * producers는 buffer에 리소스를 삽입합니다.
  * consumers는 buffer에 리소스를 제거합니다.

Bounded Buffer Problem Solution
* circular buffer를 사용해 해결할 수 있습니다.
  * in, out 포인터의 증가 연산은 `in = (in + 1) % BUFFER_SIZE`로 하면 됩니다.
  * empty buffer와 full buffer의 구분은 한 칸은 비우는 칸으로 사용하면 됩니다.

Bounded Buffer in Shared Memory (Failed)
* C 코드로 보면 다음과 같습니다.
  * Producer
    ```c
    item next_produced;
  
    while (true) {
      while (((in + 1) % BUFFER_SIZE) == out);
      buffer[in] = next_produced;
      in = (in + 1) % BUFFER_SIZE;
    }
    ```
  * Consumer
    ```c
    item next_consumed;
  
    while (true) {
      while (in == out);
      next_consumed = buffer[out];
      out = (out + 1) % BUFFER_SIZE
    }
    ```
* This is not working.
  * count와 in, out의 synchronization이 이루어지지 않습니다.

Bounded Buffer in Shared Memory (Partial Success)
* Implmentation with mutex
  * ```
    Mutex mutex;
    int count;
    struct item buffer[N];
    int in, out;
    ```
  * Producer
    ```c
    void produce(data) 
    {
    again:
      mutex.lock();
      if (count==N) {
        mutex.unlock();
        goto again; // goto 써도 안 죽습니다
      }
      buffer[in] = data;
      in = (in+1) % N;
      count++;
      mutex.unlock();
    }
    ```
  * Consumer
    ```c
    void consume(data) 
    {
    again:
      mutex.lock();
      if (count==0) {
        mutex.unlock();
        goto again;
      }
      data = buffer[out];
      out = (out+1) % N;
      count--;
      mutex.unlock();
    }
    ```
  * This is not working.
    * Producer와 Consumer가 count에 동시접근할 때 발생할 수 있는 race condition 문제는 해결했습니다
    * 하지만 여러 Producers들이 in에, 여러 Consumers이 out에 동시접근헐 때 발생할 수 있는 race condition 문제는 해결하지 못 했습니다.

* Implementation with semaphores
  * ```c
    Semaphore empty = 0;
    Semaphore full = N;
    struct item buffer[N];
    int in, out;
    ```
  * Producer
    ```c
    void produce(data) 
    {
      wait(&full);
      buffer[in] = data;
      in = (in+1) % N;
      signal(&empty);
    }
    ```
  * Consumer
    ```c
    void consume(data) 
    {
      wait(&empty);
      data = buffer[out];
      out = (out+1) % N;
      signal(&full);
    }
    ```

Bounded Buffer in Shared Memory (Success)
* Implementation with semaphores
  * ```c
    Semaphore empty = 0;
    Semaphore full = N;
    mutext_in = 1; // binary semaphore
    mutext_out = 1; // binary semaphore 
    struct item buffer[N];
    int in, out;
    ```
  * Producer
    ```c
    void produce(data) 
    {
      wait(&full);
      wait(&mutex_in);
      buffer[in] = data;
      in = (in+1) % N;
      signal(&mutex_in);
      signal(&empty);
    }
    ```
  * Consumer
    ```c
    void consume(data) 
    {
      wait(&empty);
      wait(&mutex_out);
      data = buffer[out];
      out = (out+1) % N;
      signal(&mutex_out);
      signal(&full);
    }
    ```
* This is working.

### 11.2.2 Readers-Writers Problem
Readers-Writers Problem
* 공유 리소스를 reader와 writer가 같이 사용하거나, multiple writers가 사용할 때 발생하는 문제입니다.
  * reader는 multiple reader여도 문제가 발생하지 않습니다!

Readers-Writers Problem Solution
* Implementation with semaphores
  * ```c
    // number of readers
    int nr_readers = 0;

    // mutex for nr_readers
    Semaphore mutex = 1;

    // mutex for reading/writing
    Semaphore rw = 1;
    ```
  * Writer
    ```c
    void Writer() 
    {
      wait(&rw);
      …
      do_write();
      …
      signal(&rw);
    }
    ```
  * Reader
    ```c
    void Writer() 
    {
      wait(&rw);
      …
      do_write();
      …
      signal(&rw);
    }
    ```

* 코드의 문제점
  * reader가 자주 도착하면 writer의 starvation이 발생할 수 있습니다.
    * writer가 기다리고 있을 때 reader의 추가 입장은 막는 방식으로 해결할 수 있을 것입니다.

### 11.2.3 Dining Philosophers Problem
* 철학자들이 생각을 하다가 오른손을 안에 넣고 왼손을 안에 놓고 스파게티를 힘껏 먹고 오른손을 밖에 내고 왼손을 밖에 내고를 반복합니다.
 이때 철학자들이 모두 동시에 왼쪽 포크를 집는 순간 ~~벤젠 마냥~~ 데드락이 발생하는 문제입니다.
* The original implementation
  * ```c
    Semaphore forks[N];

    #define L(i) (i)
    #define R(i) ((i + 1) % N)

    void philosopher(int i)
    {
      while (1) {
        think();
        pickup(i);
        eat();
        putdown(i);
      }
    }

    void pickup(int i) {
      wait(&forks[L(i)]);
      wait(&forks[R(i)]);
    }

    void putdown(int i) {
      signal(&forks[L(i)]);
      signal(&forks[R(i)]);
    }
    ```

* A deadlock-free solution
* circular dependancy를 없애면 됩니다.
* 코드로 보면 다음과 같습니다.
  * ```c
    // initialized to 1
    Semaphore forks[N];

    #define L(i) (i)
    #define R(i) ((i + 1) % N)

    void philosopher(int i)
    {
      while (1) {
        think();
        pickup(i);
        eat();
        putdown(i);
      }
    }

    void pickup(int i) {
      if (i == (N-1)) {
        wait(&forks[R(i)]);
        wait(&forks[L(i)]);
      } else {
        wait(&forks[L(i)]);
        wait(&forks[R(i)]);
      }
    }

    void putdown(int i) {
      signal(&forks[L(i)]);
      signal(&forks[R(i)]);
    }
    ```

## 11.3 Preemptive vs. Non-preemptive in Kernel
Preemptive vs. Non-preemptive in Kernel
* Preemptive kernel
  * 커널 모드로 실행되는 동안 프로세스를 미리 준비할 수 있습니다
  * response가 높습니다
  * 구현하기가 어렵습니다
* Non-preemptive kernel
  * 구현이 쉽습니다
  * response가 낮습니다

## 11.4 Synchronization in Linux
* 예전에는
  * Big Kernel Lock (BKL)이 전체 커널을 보호했습니다.
  * 짧은 critical sections을 실행하는 동안 인터럽트, 시스템 콜 등을 일체 사용할 수 없었습니다.
  * Non-preemptive 커널이었습니다.
* 요즘에는
  * BKL이 smaller, fine-grained locks으로 쪼개졌습니다.
  * Fully preemptive 커널입니다.
  * spinlock, atomic operations, semaphores, rw-lock, RCU, ... 등이 다 구현되어 있습니다.