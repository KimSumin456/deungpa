---
title:  "[운영체제] 16. Paging"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Paging
---

## Preview
* Paging
* Page Tables
  * Paging and Page Tables
  * Address Translation, Address Translation Example
  * PTE
* Buddy System Allocator


<!--16강 Paging-->
## 16.1 Paging
Paging
* **Paging**은 프로세스의 Virtual address space를 일정한 크기의 page로 나누고, 컴퓨터의 Physical memory를 같은 크기의 frame(또는 page frame)으로 나누어 non-contiguous하게 매핑하는 메모리 관리 기법입니다.
  * page와 frame의 size는 대게 4KB가 적당하다고 알려져 있습니다.

Paging 특징
* 여전히 internal fragmentation은 발생할 수 있습니다
  * 한 프로세스 당 최대 'one-page size - 1byte' 만큼, 평균적으로 '1/2 one-page size'만큼 internal fragmentation이 발생합니다. 하지만 큰 문제는 아닙니다.
    * 예) 프로세스 개수 x 1/2 x one-page size = 1000 x 1/2 x 4KB = 2MB 밖에 되지 않습니다.
  * external fragmentation은 발생하지 않습니다 (그러나 현실적으론 발생하기도 합니다)
* page, frame size를 작게하면 internal fragmentation은 줄일 수 있겠으나 page, frame 및 page table entry의 개수가 늘어납니다.
  * 그래서 경험적으로 4KB가 적당하다고 알려져 있는 것입니다.

## 16.2 Page Tables
Page Tables, Page Table Base Register (PTBR) *-> 16.2.1 Paging and Page Tables*
* 각 프로세스는 자신만의 page table을 가지고 있습니다
* **Page Table**은 Virtual Page Number (VPN)을 Physical Frame Number (PFN)으로 매핑해줍니다
* **Page Table Base Register**은 각 page table의 base address를 가리킵니다. 따라서 프로세스와 같이 스케줄링되어야 합니다.

Map VPN to PFN *-> 16.2.2 Address Translation, Address Translation Example*
* **Virtual address은 <Virtual Page Number (VPN), Offset>로 구성됩니다**
* **Physical address은 <Page Frame Number (PFN), Offset>로 구성됩니다**
* 주소를 변환할 때 VPN은 PFN로 매핑하고, Offset은 그대로 사용하면 됩니다
  * VPN이 page table에서 일종의 index입니다.
* 보통 VPN이 PFN보다 크기가 큽니다

Page Table Entry (PTE) *-> 16.2.3 PTE*
* 한 **Page Table Entry**가 한 virtual address space의 page가 필요로 하는 정보(죽, PFN의 정보)를 담고있습니다.

**Page Table은 OS에 의해 관리되고, MMU에 의해 접근됩니다.**

### 16.2.1 Paging and Page Tables
* 강의노트 그림 참고
* Virtual address -> Page Table -> Physical address (= Memory, 즉 RAM)

### 16.2.2 Address Translation, Address Translation Example
* 강의 참고
* (조건) Virtual address가 4GB, Physical address가 1BM, Page size가 4KB일 때,
* (문제) VPN, PFN, Offset의 길이(bit 개수)와 Page table의 size를 구할 수 있습니다
* Virtual address: 4GB = 2<sup>2</sup> x 2<sup>30</sup> = 2<sup>32</sup> 이므로 32bit입니다
* Physical address: 1MB = 2<sup>0</sup> x 2<sup>20</sup> = 2<sup>20</sup> 이므로 20bit입니다
* Page size: 4KB = 2<sup>2</sup> x 2<sup>10</sup> = 2<sup>12</sup> 이므로 12bit입니다
* Offset: offset이 한 page 내에서의 위치를 나타내는 index이므로 똑같이 12bit입니다
* VPN: Virtual address = <VPN, Offset>이므로 32 - 12 = 20bit입니다
* PFN: Physical address = <PFN, Offset>이므로 20 - 12 = 8bit입니다
* Page table: 총 entry의 개수가 VPN만큼, 한 entry의 길이가 PFN만큼인 것이므로 2<sup>20</sup>개 x 8bit = 2<sup>20</sup> x 1B = 1MB입니다

### 16.2.3 PTE
Paging 장점
* external fragmentaiton이 발생하지 않습니다 (그러나 현실적으론 발생합니다)
* 프로세스 A가 B의 Page table에 접근할 수 없습니다. 즉 프로세스마다 address space의 독립성(isolation)을 쉽고 정교하게 구현할 수 있습니다

PTE
* 생략

Protection
* 생략

## 16.3 Buddy System Allocator
Buddy System Allocator의 필요성, 등장 배경
* Paging은 Logicaaly contiguous하지만, 현실적으로 I/O buffers, in-kernel data structure 등에서 physically contiguous가 필요한 경우가 있습니다.
  * 그래서 현실적으로 external fragmentation이 발생할 수 있다는 것입니다
* 따라서 우리는 external fragmentation을 제어하고 감소시킬 수 있는 메커니즘이 필요합니다

Buddy System Allocator
* Allocation
  * 먼저 physically-contiguous pages로 구성된 일정한 2<sup>n</sup> 크기의 한 덩어리(청크)를 할당합니다
  * 현재 가지고 있는 크기의 청크를 요청받으면, 그대로 할당해줍니다
  * 더 작은 크기의 청크를 요청받으면, 가능한 작은 청크를 buddy로 이분해나간 뒤 2<sup>n - a</sup>크기의 청크를 할당해줍니다
* Free
  * 자신의 buddy가 free하지 않다면, 자신만 free임을 표시하고 끝냅니다.
  * 자신의 buddy가 free하다면, 합병합니다. 그리고 상위 buddy가 free한지 확인하며 재귀적으로 앞의 과정들을 반복합니다.
* 따라서 어떤 page(청크)의 buddy가 누구인지를 찾아낼 수 있어야하는 게 구현의 핵심입니다.