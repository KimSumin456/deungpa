---
title:  "[운영체제] 18. Demand Paging"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Demand Paging
- VM Features
---

## Preview
* Recap the last sessions
* Demand Paging
  * Swapping
  * Demand Paging
* VM Features
  * Virtual Memory
    * Virtual Memory (VM) Advantages
    * Features and issues in Virtual Memory
  * Features and issues in Virtual Memory
    * Shared Memory
    * Copy-on-Write
      * Where is the operating system in the memory?
    * Thrashing
    * Prepaging
    * Memory-Mapped Files
* Conclusion

<!--18강 Demand Paging and VM Features-->
## 18.0 Recap the last sessions
* Paging
* Page tables
  * Hierarchical page tables
* Translation Lookaide Buffer (TLB)

---
## Demand Paging
## 18.1 Swapping
Swapping
* **Swapping**이란 스토리지(storage device)를 활용해 paging을 하는 방식입니다. 프로세스를 임시로 백업 저장소(backing storage)에 넣어둔(swap out) 뒤, 나중에 다시 메모리로 가져옵니다(bring).
* 장점
  * 실제 메인 메모리(physical memory)의 용량보다 더 많은 양의 프로세스들을 실행할 수 있습니다.
* 단점
  * 시간이 오래 걸리는 overhead가 큽니다
* 해결책
  * 프로세스의 일부분만 swapping 하도록 합니다

## 18.2 Demand Paging
Demand Paging
* **Demand Paging**이란 page 단위(page-level)로 swapping을 하는 paging system입니다. 필요할 때만 page를 메모리로 가져옵니다.
  * 가상 메모리(virtual memory)를 구현하는 주요 기술입니다.
* 그 결과 자주 쓰는 프로세스는 메인 메모리에 남아있고 잘 안 쓰는 프로세스는 swap file로 빠지게 되면서, OS는 메인 메모리를 캐시처럼 사용하게 됩니다.
* 장점
  * I/O 필요가 줄어듭니다
  * 메모리 필요가 줄어듭니다
  * 반응이 빨라집니다
  * 사용자가 많아집니다

Demand Paging 예시
* 메인 메모리가 다 찼으나 page를 더 필요로 하면
1. OS는 page replacement policy에 따라 victim page를 고릅니다.
2. 해당 victim page의 내용을 디스크의 swap file(=paging file)에 써놓습니다.
3. 해당 PTE는 swap file에 있는 swapped out된 page의 swap entry를 가리키도록 업데이트합니다.
4. 메모리에 있는 victim page frame을 회수합니다(비웁니다).
5. 그곳에 P2(처음에 page를 필요로 했던)를 할당합니다.

* swap file에 있는 entry를 필요로 하면
1. P0가 swapped out page를 접근하고자 합니다.
2. PTE는 swap entry에 swapped out 되어있는 page를 가리키고 있습니다.
3. OS는 P0를 위해 위의 예시에서 설명한 대로 page를 evicts합니다.
4. 그곳에 swap entry로부터 swapped out page 내용을 로드합니다.

Page Table Entry의 옵션 비트  
1. valid bit
  * **valid bit**는 PTE가 가리키는 page가 evicted되었는지 여부를 나타내는 옵션 비트입니다. page가 swap out될 때 PFN이 swap entry를 가리키도록 업데이트됨과 동시에, valid bit이 0으로 설정됩니다.
  * 그러면 MMU는 해당 PTE의 valid bit이 clear(0)라면 가리키는 page가 evicted되었음을 알고 **page fault**라는 exception을 OS에게 발생시킵니다.
  * 이에 대해 OS는 **page fault handler**라는 exception handler를 실행시킵니다.
* 나머지 비트들은 다음 강의에 다룹니다.

Pure Demand Paging
* 디스크에 파일로 저장되어 있는 프로그램을 실행시키면 code, data, heap, stack으로 나누어 메모리로 불러올텐데, 처음엔 page table이 비어있는 상태로 시작해서 on demand로 page fault를 띄어나가는 형태로 실행합니다.

Page Replacement Policy and Free Page
* 어떤 page를 evict할 것인가에 대한 알고리즘은 다음 강의에 다룹니다.
* 한편 OS는 page fault가 났을 때 eviction하지 않고도 처리할 수 있도록 어느 정도의 free pages를 가지고 있으려고 합니다.
  * 이러한 연산은 Pager(Linux에선 kswapd)가 수행합니다. 메모리에서 free page를 확보하기 위해 일부 프로세스를 swap file로 빼놓습니다.

Demand Paging과 Locality
* Demand Paging은 the principle of locality에 기반합니다. demand paging이 유의미하기 위해선 locality가 필요합니다.
* Temporal locality란 최근에 참조된 곳이 또다시 참조되는 경향을 의미합니다.
* Spatial locality란 최근에 참조된 곳의 근처가 참조되는 경향을 의미합니다.

Demand Paging과 Hardware
* Demand Paging을 위해선 하드웨어가 다음과 같은 기능을 제공해줘야 합니다.
* valid/inavlid bit를 가지고 있어야 합니다
* 보조 기억장치(Secondary memory, swap device with swap space)를 가지고 있어야 합니다
* 인스트럭션 재시작이 가능해야 합니다
  * OS가 fix up 해준 PTE로 page fault를 일으킨 인스트럭션부터 재시작을 할 수 있어야 합니다 

---
## VM Features
## 18.3 Virtual Memory
Virtual Memory
* 이때까지 배운 운영체제가 메모리를 관리하는 개념이 Virtual Memory System입니다. Virtual Memory를 통해서 OS가 프로세스에게 메모리를 가상화해서 보여주고 abstract해줍니다.
* 프로세스들은 각자 자신의 Virtual address만 알고있고, MMU와 TLB, OS가 PTE를 통해 Physical address로의 mapping을 제공해줍니다.

### 18.3.1 Virtual Memory (VM) Advantages
Virtual Memory (VM) Advantages
* physical memory로부터 logical memory를 분리할 수 있습니다.
* 프로세스들은 contiguous한 logical address만 보면 되고, OS가 알아서 관리해줍니다.
* 필요없는 프로세스들은 swap시킬 수 있습니다

### 18.3.2 Features and issues in Virtual Memory
Features and issues in Virtual Memory _=> 18.4_
* 그리고 Shared Memory를 통해 수많은 기능을 제공해줍니다.

## 18.4 Features and issues in Virtual Memory
### 18.4.1 Shared Memory
Shared Memory
* virtual memory를 통해 IPC(Inter Process Communication) 중 **shared memory** 방식을 쉽게 구현할 수 있습니다.
  * 서로 다른 프로세스의 PTE가 하나의 page frame 가리키게만 하면 됩니다.

### 18.4.2 Copy-on-Write
Copy-on-Write ★
* 게다가 copy가 아닌 shared memory를 통해 fork를 효과적으로 구현할 수 있습니다. 단, fork 후 write를 할 때는 copy-on-write를 해야합니다.
* **copy-on-write**란 fork 후 write를 해야할 땐 MMU가 page fault를 날리면, OS가 원래 가리키던 page를 copy한 뒤 그곳으로 mapping을 바꿔주고, write를 허용해주는 방식입니다. 이때 원래 가리키던 page의 map count는 1 감소시킵니다.
  * map count란 page 자신을 가리키고 있는(mapping하고 있는) PTE의 개수입니다.

Copy-on-Write 사례
* map count가 0이 되면 page를 반환해야합니다.
* copy-on-write를 통해 page owner가 바뀔 수 있습니다
* copy-on-write는 fork 말고도 OS가 다양한 용도로 사용합니다.
* copy-on-write는 malloc에도 활용됩니다.
  * 사실 malloc을 하면 바로 메모리 할당을해주지는 않고 메모리 디스크립터에는 써놓습니다. MMU가 read를 하고자 할 땐 OS가 zero page를 mapping해주어 0을 읽어가고, write를 하고자 할 때가 되서야 그때 메모리를 새로 할당하고 덧붙여(populate)줍니다.

Where is the operating system in the memory? Kernel address space.
* 실제 프로세스의 주소 공간은 user address space와 kernel address space로 나누어져 있습니다. 모든 프로세스들은 같은 kernel address space를 공유하고 있기 때문에, 시스템 콜을 통해 OS를 부를 수 있는 것입니다.

Paging Virtual Memory, Frame Allocation, Page Replacement
* 다음 강의에 자세히 다룹니다.

### 18.4.3 Thrashing
* **Thrashing**이란 현재 돌고있는 모든 프로세스들의 working set의 합이 현재 컴퓨터의 physical memory보다 커지는 순간 성능이 갑자기 뚝 떨어지는 상황을 말합니다.
  * memory print란 전체 메모리 사용량을 의미하고, **working set**이란 memory print 중 자주 사용하는 부분을 말합니다
* working set보다 작은 physical memory를 가지고 있으면 아무리 locality가 뛰어나도 잦은 paging이 발생하여 성능이 collapse하게 됩니다.

### 18.4.4 Prepaging
* **Prepaging**이란 spatial locality를 고려해 어떤 페이지를 메인 메모리로 페이징할 때, 그 주변 페이지도 같이 페이징하는 일을 말합니다.
  * Prefetching이라고도 하며, Linux에선 fault-around scheme이라고 합니다.

## 18.5 Conclusion
* 다음 시간에 Memory-mapped file, Allocating kernel memory, Page pinning을 배울 것입니다.