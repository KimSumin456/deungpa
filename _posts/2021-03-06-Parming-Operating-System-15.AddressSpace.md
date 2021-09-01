---
title:  "[운영체제] 15. Address Spaces"
excerpt: "등록금 파먹기 - 운영체제 파먹기 (Parming Operating System)"
toc: true
toc_sticky: true

categories:
- 운영체제
tags:
- 등록금 파먹기
- 운영체제
- Address Spaces
---

## Preview
*	Part III. Memory Management
* Address in Computers
* MMU translates the LAs to PAs.
  * Fixed Partitions
  * Variable Partitions
  * Segmentation

<!--15강 Address Spaces-->
## 15.1 Part III. Memory Management
* 폰 노이만 구조를 생각해보면 **CPU**를 이때까지 배웠고, **Memory**를 앞으로 배울 것입니다.
  * 프로그램을 실행하기 위해선 code와 data가 반드시 메인 메모리에 올라가야 합니다.
  * 각 프로세스는 자신만의 주소 공간(own address space)를 필요로 합니다.
  * 그러나 메모리는 비싼 시스템 리소스입니다.
  * 따라서 운영체제(operating systems)는 메모리를 효율적으로 관리해야합니다.

* 이전 강의에서 스케줄러는 프로세스에게 CPU(Processor)를 독점해서 사용하는 것 같은 가상 환경을 제공한다고 배웠습니다.
  * 메모리도 못 할 건 없죠.

* 운영체제는 다음과 같은 메모리 관리를 수행합니다
  * Allocate memory to processes
  * Provide separate address spaces to processes
  * Allow processes to relocate (dynamic linking)
  * Provide a physically contiguous address space
  * Fragmentation management (compaction, movable)
  * Caching
  * ...

## 15.2 Address in Computers
* 위치는 하나인데 도로명 주소, 지번 주소, GPS 등 표현은 여러 개인 것처럼, 메모리 주소도 다양한 형태로 표현됩니다.
  * Physical address vs Logical address
  * Absolute address vs Relative address

* Physical address (PA): 메모리 장치에서 볼 수 있는 주소
* Logical address (LA): CPU에서 생성되는 주소 (= Virtual address (VA))
* Memory Management Unit (MMU)는 LA를 PA로 변환합니다
  * 현대 아키텍처들은 MMU를 CPU 코어의 일부로서 가지고 있습니다.

* 프로세서는 LA를 참조합니다
  * 프로세스도 마찬가지로 LA를 참조합니다
* MMU는 LA를 PA로 변환합니다
  * 따라서 LA를 PA로 매핑하기 위한 매커니즘과 데이터 구조가 필요합니다
  * * _※ 이번 강의에서 각 프로세스는 자신만의 logical address space를 가지고 있다고 가정합니다_
* 프로세스마다 가지고 있는 logical address space을 어떻게 physical memory address space에 배치해야 할까요?
  1. Fixed Partitions -> 15.3.1
  2. Variable Partitions -> 15.3.2
  3. Segmentation - 15.3.3

## 15.3 MMU translates the LAs to PAs.
### 15.3.1 Fixed Partitions
Fixed Partitions
* **fixed partition**은 physical memory를 일정한 크기의 파티션으로 나누고, 프로세스에게 파티션 하나를 할당해주는 방식입니다.
* **base register**는 base address(PA의 시작 주소)가 쓰여져 있는 레지스터입니다. 프로세스마다 base register를 가지고 있습니다.
  * 프로세스마다 base address 값이 다르므로 base register도 같이 스케줄링되어야 합니다
* 따라서 **physical address = base address + logical address**로 변환할 수 있습니다

Fixed Partition의 특징
* 구현이 쉽습니다
* 올바른 접근인지 검사하기가 쉽습니다
    * logical address와 파티션 크기를 비교하기만 하면 됩니다
    * logical address > partition size 이면 잘못된 접근입니다
* Internal fragmentation이란 파티션 크기(partition size)를 천편일률적으로 할당하기 때문에 모든 프로세스에게 적합할 수 없어 발생하는 문제가 있습니다

Internal Fragmentation
* **Internal fragmentation**은 fixed partition에서 한 프로세스가 차지하고 남은 공간을 활용할 수 없다는 문제입니다.
  * 메모리를 미리 천편일률적으로 나누었고, 한 파티션은 한 프로세스(인스턴스)만 exclusive하게 사용할 수 있기 때문에 발생합니다.

### 15.3.2 Variable Partitions
Variable Partition
* **variable partition**은 physical memory를 프로세스에게 필요한 만큼만 할당해주는 방식입니다.
  * fixed partitioning의 문제를 개선하고자 한 방식입니다.
* **limit register**는 partition size가 쓰여져 있는 레지스터입니다. 프로세스마다 limit register를 가지고 있습니다.
* **hole**은 할당(allocation)되어 있지 않은 메모리 공간을 말합니다.

Variable Partition의 특징
* 장점
  * logical address >= partition size 이거나 physical address >= limit register 이면 잘못된 접근입니다
  * internal fragmentation이 없습니다
    * 단, sparce address space가 아닐 때의 기준입니다
* 단점
  * 그러나 external fragmentation이 있습니다
    * internal fragmentation보다 더 골 때리는 문제입니다
  * allocation strategies도 생각해야 합니다
  * 프로세스가 얼마 만큼의 메모리 공간을 필요로 할 지 미리 알기 힘듭니다
    * 미래의 정보를 사용하는 방식의 알고리즘은 역시 구현이 힘듭니다
    * grow, shrink 등의 추가 인터페이스를 필요로 할 것입니다

External Fragmentation
* **external fragmentation**은 variable partition에서 티끌 모아 태산인 자잘한 hole들을 활용할 수 없다는 문제입니다.
  * allocation과 free를 반복하다 보면 hole이 발생할 수 밖에 없기 때문에 발생합니다.

Allocation Strategies
* **allocation strategies**는 어떤 hole을 프로세스에게 할당해줄 것인가에 관한 문제입니다
  * (프로세스에게 크기가 적합한 hole 중에서)
  * first fit: 맨 첫 번째 hole을 할당하는 방식입니다.
  * best fit: 가장 작은 hole을 할당하는 방식입니다.
  * worst fit: 가장 큰 hole을 할당하는 방식입니다.
    * best fit을 썼을 때 external fragmentation이 빈번하게 발생한다고 알려져 있습니다
    * **worst fit을 썼을 때 external fragmentation이 가장 적게 발생한다고 알려져 있습니다**
* first fit policy를 썼을 때 N번의 블록을 할당하면 0.5 N번의 external fragmentation이 발생한다고 알려져있습니다

### 15.3.3 Segmentation
Segmentation
* **segmentation**은 프로세스의 주소 공간을 logical segments로 나누고, 그 segment들을 adjacent(not contiguous)하게 할당하는 방식입니다.
  * variable partition의 확장판입니다
  * segemnt에는 code, data, stack, heap, ... 등이 있습니다
* 메모리를 **a collection of variable-sized segments**라고 볼 수 있습니다

Segment ID는 명시적(explicit) 또는 암시적(implicit)으로 표현할 수 있습니다
* explicit: <segment ID, offset>
  * segment마다 base address가 있고 거기서부터의 offset으로 표현하는 방법입니다
  * 예) <0x01, 0x2a31>, <0x21, 0x23c2>
* Logical Address: <segment ID, offset>
  * 앞에서부터 n 비트만큼을 segment ID라고 암묵적으로 사용하는 방식입니다
  * 예) 0x012a31, 0x2123c2

* 프로세스마다 자신만의 segment table을 가지고 있습니다. segment table에서는 segment마다 ID와 base address를 가지고 있고, direction과 protection도 설정할 수 있습니다.
  * 프로세스와 같이 스케줄링(또는 context switch) 되어야 합니다.
* segment table은 <u>레지스터(Segment-table Base Register, STBR)</u>에 둘 수도 있고 <u>메모리</u>에 둘 수도 있습니다

Segmentation Example
* 강의노트 참고

Segmentaiton 특징
* 장점
  * sparse allocation이 가능합니다
    * 각 segemnt를 dynamically relocate할 수 있습니다
      * segment table만 고치면 됩니다
    * sparse address space는 메모리 용량 관리에 유용합니다
  * segment를 쉽게 보호할 수 있습니다
    * segment마다 개별적인 protection이 가능합니다
      * 예를 들어 read-only 등의 설정을 할 수 있습니다
* 단점
  * segment table을 구성하고 관리해야 합니다
    * 레지스터에 두는 방법은 context switch 오버헤드가 큽니다
    * 메모리에 두는 방법은 시간이 오래 걸립니다
  * 여전히 external fragmentation이 발생할 수 있습니다
    * 여전히 exclusive한 메모리 리소스를 variable size로 allocation과 delocation을 반복하는 형태이기 때문입니다
