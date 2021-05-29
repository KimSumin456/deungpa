---
title:  "[운영체제] 17. Page Tables"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Page Tables
---

## Preview
* Paging and Page Tables
* Linear Page Table
* Hierarchical Page Tables
  * Two-level Page Tables, Three levels?, Four levels?
  * How can translate VPN to PFN?
  * Virtual addresses = <outer page #, page #, page offset>
  * Hierarchical Page Tables Example
    * 32-bit address space, 4KB pages, 4bytes/PTE
    * 53-bit address space, 8KB pages, 8bytes/PTE
    * 48-bit address space, 4KB pages, ?bytes/PTE
  * Pros and Cons
* Hashed Page Table
* Inverted Page Tables
* TLB

<!--17강 Page Tables-->
## 17.0 Paging and Page Tables
Virtual address space for Process A -> Page table for Process A -> Physical Memory
- Page Table을 어떻게 구성할 것인가?

## 17.1 Linear Page Table
Linear Page Table
* Linear Page Table이란 모든 page table entry를 연속된 physical address space에 쫙 펼쳐놓는 방식입니다.

Linear Page Table Structure
* space overhead가 큽니다
  * 32비트 컴퓨터가 32-bit address space with 4KB pages, 4bytes/PTE일 때 프로세스 하나 당 page table이 4MB를 차지합니다
  * 64비트 컴퓨터가 51-bit address space with 8KB pages, 8bytes/PTE일 때 프로세스 하나 당 page table이 16PB를 차지합니다?
  * 하지만 정작 process address space는 sparse합니다
* page tables 자체도 메모리에 저장되어야 하는데, 메인 메모리를 페이지 단위로 쪼개서 관리하고 있으나 page tables이 너무 커서 한 페이지에 넣을 수 없습니다
  * external fragmentation이 발생할 수 있습니다?

## 17.2 Hierarchical Page Tables
Hierarchical Page Tables
* Hierarchical Page Table이란 바깥에 Outer page table을 두고 전체 page table을 나눠서 관리하는 방식입니다. 더 이상 physical address space에 연속적으로 놓을 필요도 없습니다.
* Outer page table -> Page table, Pages of page table  -> Process memory

### 17.2.1 Hierarchical Page Tables 구성
Two-level Page Tables
* 강의노트 참고
* 한 page 안에 4개의 page table entry가 들어갈 수 있다면
* two-level page table은 4개의 leaf page table pages와 1개의 outer page table page로 구성됩니다
  * address space에서 총 5개의 page table이 필요합니다
* 한 leaf page table 안은 4개의 page로 구성되고, 한 page 안은 4개의 page table entry로 구성됩니다
  * address space에서 총 16개의 pages를 할당할 수 있습니다

Three-level Page Tables
* 강의노트 참고
* 한 page 안에 4개의 page table entry가 들어갈 수 있다면
* page table은 총 1 + 4 + 4<sup>2</sup>개, page는 총 4 x 4 x 4 = 4<sup>3</sup>개로 구성됩니다

Four-level Page Tables
* 강의노트 참고
* 한 page 안에 4개의 page table entry가 들어갈 수 있다면
* page table은 총 1 + 4 + 4<sup>2</sup> + 4<sup>3</sup>개, page는 총 4 x 4 x 4 x 4 = 4<sup>4</sup>개로 구성됩니다

한 page 안에 16(=2<sup>4</sup>)개의 page table entry가 들어갈 수 있다면
* three-level page tables이라면
* page table은 총 1 + 16 + 16<sup>2</sup>개, page는 총 16 x 16 x 16 = 16<sup>3</sup>개로 구성됩니다

### 17.2.2 How can translate VPN to PFN?
How can translate VPN to PFN?
* 강의노트 참고
* 이진수를 보고 차례대로 파싱해서 찾아가면 된다

### 17.2.3 Virtual addresses = <outer page #, page #, page offset>
Virtual addresses = <outer page #, page #, page offset>
* 한 page가 2<sup>n</sup>개의 PTE(page table entry)를 가진다면, n개의 bit를 virtual address의 index로 사용할 수 있습니다.

### 17.2.4 Hierarchical Page Tables Example
Hierarchical Page Tables Example
* 강의노트 참고
  * (※ 4bytes/PTE는 PTE 하나가 4B라는 뜻입니다)
* (조건)32-bit address space, 4KB pages, 4bytes/PTE일 때
* (문제)Page offset, Page #, Outer page #의 비트 구성을 구할 수 있습니다.
  * page offset: pages의 크기가 4KB = 2<sup>2</sup> x 2<sup>10</sup>B = 2<sup>12</sup>B이므로 12bit입니다
  * page #: PTE의 개수가 pages의 크기 / bytes/PTE = 4KB / 4B = 2<sup>10</sup>개 이므로 10bit입니다
  * Outer page #: page #와 똑같이 10bit입니다 (32 - 12 - 10 = 10으로 딱 맞습니다)

* (조건)53-bit address space, 8KB pages, 8bytes/PTE일 때
* (문제)Page offset, Page #, Outer page #의 비트 구성을 구할 수 있습니다.
  * page offset: pages의 크기가 8KB = 2<sup>3</sup> x 2<sup>10</sup>B = 2<sup>13</sup>B이므로 13bit입니다
  * page #: PTE의 개수가 pages의 크기 / bytes/PTE = 8KB / 8B = 2<sup>10</sup>개 이므로 10bit입니다
  * Outer page #: page #와 똑같이 10bit입니다 (53 - 13 - 10 - 10 - 10 = 10으로 딱 맞습니다. 4-level page table이네요)

* (조건)Page offset가 12bit, Page #가 9bit, Outer page #가 9bit일 때
* (문제)address space, pages, bytes/PTE의 크기 구성을 구할 수 있습니다.
  * virtual address space: 구조를 보면 총 48bit이므로 48-bit virtual address space입니다
  * pages: page offset이 12bit이므로 하나의 page는 2<sup>12</sup>B = 4KB입니다
  * PTE: page #들이 9bit이므로 PTE의 개수는 2<sup>9</sup>개, PTE 하나의 크기(bytes/PTE)는 page 크기 / PTE 개수 = 2<sup>12</sup>B  / 2<sup>9</sup>B = 2<sup>3</sup>B = 8B입니다

### 17.2.5 Pros and Cons
Pros
* sparse-address space에 알맞습니다
* physical memory를 관리하기 쉽습니다
* 하드웨어(특히 MMU)를 구현하기 쉽습니다
* external fragmentation이 발생하지 않습니다

Cons
* 구현하기 복잡합니다
* 메모리를 여러 단계에 걸쳐 lookup하므로 시간이 매우 오래 걸립니다

## 17.3 Hashed Page Table
* Hashed Page Table이란 radix tree가 아니라, hash table 형태로 구현한 page table입니다
* virtual address(logical address)의 VPN으로 해쉬 함수를 돌리면 h(VPN)이 hash table의 index가 됩니다
* 해당 index의 체이닝에서 노드를 탐색하면 그 안에 VPN과 PFN 매핑이 적혀져 있는 것을 보고 찾아갑니다

## 17.4 Inverted Page Tables
* Inverted Page Table이란 PFN으로부터 VPN과 PID를 찾겠다는 방식입니다
* Cons
  * 구현이 어렵습니다
  * 성능이 안 좋습니다
  * 그래서 실제로 사용되지 않습니다

## 17.5 TLB
* TLB는 Hierarchical Page Table의 느린 속도 문제를 개선하기 위한 해결책입니다. 메모리는 locality of reference(최근에 접근한 주소에 또 접근할 가능성이 크다)가 크다는 점을 이용하여, 한 번 변환한 VPN -> PFN의 정답을 외워놓는 방식입니다.
  * 요즘 컴퓨터는 보통 32~1024개의 cache(TLB entry)를 가지고 있습니다
* 동작 방식은 다음과 같습니다
  * MMU는 address translation을 할 때 먼저 TLB를 훑어봅니다
  * TLB hit가 나면 바로 그 정보를 이용해 virtual address를 physical address으로 변환합니다
  * TLB miss가 나면 메모리에서 page table을 찾고, TLB를 업데이트하고 virtual address를 physical address으로 변환합니다
* **단, 프로세스가 스케줄링되면 page table도 바뀌니, TLB를 다 비워야 합니다**
  * 각 프로세스는 자신만의 VA to PA mapping, 즉 page table을 가지고 있다고 했습니다
* 어떤 TLB는 address-space Identifier (ASIDs)를 함께 기록함으로써 프로세스가 스케줄링 돼도 TLB를 안 비우고 같이 적는 것을 허용하기도 합니다.