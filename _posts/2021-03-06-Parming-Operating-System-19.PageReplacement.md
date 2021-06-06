---
title:  "[운영체제] 19. Page Replacement"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Page Replacement
---

## Preview
* Frame Allocation
* Page Replacement
  * OPT
  * FIFO
  * LRU
  * LRU Approximation Algorithms
  * Enhanced Second-Change Algorithm
  * Counting-based Page Replacement
  * Global vs. Local Page Replacement
*	Page Pinning
* Paging Virtual Memory

<!--19강 Page Replacement-->
## 19.0 Frame Allocation
Frame Allocation
* frame allocation은 제한된 page frames을 프로세스에게 어떻게 분배할 것인가를 의미하며, 다음과 같은 방법들이 있습니다. 각 방법들은 우열을 가릴 수 없고 필요에 따라 적절히 적용해야 합니다.
  * equal allocation은 모든 프로세스에게 동일한 양을 분배하는 방법입니다.
  * proportional allocation은 각 프로세스의 실제 메모리 사용량을 고려하여, 메모리를 많이 쓰는 프로세스에게 더 많이 분배해주는 방법입니다.
  * priority allocation은 우선순위에 따라 분배하는 방법입니다.

## 19.1 Page Replacement
Page Replacement
* page replacement는 메모리가 꽉 찼을 때 어떤 page를 evict할 것인가를 의미하며, page fault rate를 최소화하는 게 목표입니다.
  * page fault 발생 시 디스크에 접근해야해 penalty가 크기 때문입니다
  * 작은 miss rate라도 전체 effective access time을 지배합니다. 강의노트 참고

### 19.1.1 OPT
OPT
* (Belady's Algorithm이라고도 합니다.)
* OPT는 이후에 가장 긴 기간 동안 사용되지 않을 page를 빼는 방식입니다.
  * 하지만 미래의 정보를 필요로하므로 구현하기 어렵습니다.
* 가장 적은 fault가 발생하는 optimal page replacement algorithm임이 수학적으로 증명되어 있습니다.
  * 따라서 다른 알고리즘의 성능을 측정하는 비교 기준으로 사용합니다
* stack algorithm입니다.

OPT 예
* 강의노트 참고

### 19.1.2 FIFO
FIFO (First-In First-Out)
* FIFO는 가장 먼저 할당되었던 page를 빼는 방식입니다.
* locality를 고려하지 않았습니다.
* Belady's Anomaly가 발생합니다.

FIFO 예
* 강의노트 참고

Belady's Anomaly
* Belady's Anomaly란 page frame을 늘렸는데 되려 page fault rate가 증가하는 경우가 때때로 생기는 상황을 말합니다.

### 19.1.3 LRU
LRU (Least Recently Used)
* LRU란 <u>이전에</u> 가장 긴 기간 동안 사용되지 않았던 page를 빼는 방식입니다.
  * 과거의 정보를 필요로 하므로 구현할 수 있습니다
  * 하지만 효과적으로 구현하기 어렵습니다
* stack algorithm입니다.
  * stack algorithm이란 f(n) ⊂ f(n+1)이 성립하는 알고리즘입니다.
  * stack algorithm은 belady's anomaly가 발생하지 않습니다.

LRU 예
* 강의노트 참고

LRU 구현
1. clocks 또는 counters를 사용하는 방법
* page table entry가 참조될 때마다 그 옆에 현재 clock을 적어놓는 방법입니다.
* 메모리 참조(memory reference)는 빠르게 할 수 있지만, 대체(replacement)하는 게 느립니다.
  * 전체 page table 탐색 시간이 O(n)이기 때문입니다
2. 이중연결리스트(doubly linked list) 또는 스택을 사용하는 방법
* page table entry가 참조될 때마다 헤드로 위치를 옮겨놓는 방법입니다.
* 메모리 대체는 빠르게 할 수 있지만, 참조하는 게 느립니다.
  * 이중연결리스트 추가/삭제 연산이 복잡하기 떄문입니다.

### 19.1.4 Additional-Reference-Bits Algorithm
LRU Approximation Algorithms
* LRU는 구현이 어렵기 때문에 LRU를 비슷하게 흉내낸 Approximtation 알고리즘을 훨씬 더 많이 사용하고 있습니다.

Additional-Reference-Bits Algorithm
* Additional-Reference-Bits Algorithm은 PTE의 reference bit을 이용하는 LRU Approximation Algorithms 방법입니다.
* MMU는 PTE를 읽을 때 reference bit을 1로 설정하고, OS는 주기적으로 refercen bit을 오른쪽으로 쉬프트하며 옮겨놓습니다. 그러면 옮겨놓은 reference bit들을 이진수로 보았을 때 가장 큰 값이 가장 최근에 참조된 PTE일 가능성이 높다는 점을 이용합니다.
  * 구현이 쉬우나, 여전히 탐색 오버헤드가 큽니다

### 19.1.5 Second-Change Algorithm
Second-Change Algorithm
* Second-Change Algorithm은 PTE를 원형으로 만들어 이용하는 LRU Approximation Algorithms 방법입니다.
  * clock algorithm이라고도 합니다
* 원형의 page table에는 시계침처럼 임의로 하나의 페이지를 가리키는 clock hand가 있습니다.
* victime page를 선정해야할 때 이 clock hand가 가리키고 있는 page의 reference bit을 보고 0이면 evict하고, 1이면 0으로 만든 뒤 다음 페이지를 가리키고 앞서 말한 과정을 반복합니다.

Enhanced LRU Approximation Algorithms
* 그런데 Second-Change Algorithm에서, 수정되지 않았던 page는 evict될 때 file을 업데이트 않으면 시간을 줄일 수 있을 것입니다.
* 그래서 Enhanced Second-Change Algorithm는 modift bit(= dirty bit)까지 이용하는 Second-Change Algorithm입니다.

### 19.1.6 Counting-based Page Replacement
Counting-based Page Replacement
* 또한 page replacement에서 recentcy말고 다른 척도를 기준으로 삼을 수도 있을 것입니다.
  * Least Frequently Used (LFU)는 가장 조금 참고된 횟수, 즉 가장 작은 reference count를 기준으로 합니다
  * Most Frequently Used (MFU)는 가장 많이 참고된 횟수, 즉 가장 큰 reference count를 기준으로 합니다
* 그러나 구현이 비싸고, 과거 정보에 과적합되기 때문에 유용하지 않을 수 있습니다.

### 19.1.7 Global vs. Local Page Replacement
Global vs. Local Page Replacement
* global replacement란 모든 프로세스가 가지고 있는 페이지가 victime의 대상이 될 수 있는 방식을 의미합니다
  * 장점
    * 구현이 쉽습니다
  * 단점
    * 각 프로세스가 외부 영향을 많이 받아 바운딩되지가 않습니다
    * 어떤 프로세스가 메모리를 독점적으로 많이 사용하고 있는 경우 스케줄링을 비효율적으로 만듭니다
* local replacement란 victim을 유발한 프로세스가 가지고 있는 페이지만 victime의 대상이 되는 방식을 의미합니다
  * 장점
    * 성능이 외부 영향을 받지 않습니다
  * 단점
    * 구현이 어렵습니다. fork 등으로 애매한 경우가 있습니다.
    * 어떤 프로세스가 메모리를 거의 사용하지 않은 채 놀고 있는 경우를 개선하지 못 해 전체적인 성능이 줄어듭니다

## 19.2 Page Pinning
* Page Pinning이란 eviction되면 안 되는 page를 메모리에 고정해두는 일을 말합니다
  * 예를 들어 I/O buffers 등이 있습니다
  * 강의 참고

## 19.3 Paging Virtual Memory
* 강의 참고
  * 아 이거 아는데 시간과 집중력이 없다 ㅈㅅ