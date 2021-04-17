---
title:  "[정보보호]2.Planning and Policy"
excerpt: "등록금 파먹기 - 정보보호 파먹기 (Parming Computer Security)"
toc: true
toc_sticky: true

categories:
- 정보보호
tags:
- 등록금 파먹기
- 정보보호
- Planning and Policy
---

## Preview
0. Learning Objectives & Orientation
1. Introduction and Terminology
2. Compliance Laws and Regulations
3. Organization
4. Risk Analysis
5. Technical Security Architecture
6. Policy-Driven Implementation
7. Governance Frameworks
8. Conclusion

<!--2-1강-->
## 2.0 Learning Objectives & Orientation
### Learning Objectives
* Justify the need for formal management processes.
* Explain the plan-protect-respond security management cycle.
* Describe compliance laws and regulations.
* Describe organizational security issues.
* Describe risk analysis.
* Describe technical security infrasturcture.
* Explain policy-driven implemnetation.
* Know governance frameworks.

### Orientation
* The first chapter focused on threats
* The rest of the book focuses on defense
* In this chapter, we will see that defensive thinking is built around the plan-protect-respond cycle
* In this chpater, we will focus on planning
* Chapters 3 to 9 focus on protection
* Chapter 10 focuses on response

## 2.1 Introduction and Terminology
### 2.1.1 Defense
* Security is process, not a product. - Bruce Schneier
  * 이 말은 보안 관리보다 보안 기술에 지나치게 집중하는 것은 실수라는 점을 강조한다.
  * Schneier는 BT의 최고 보안 기술 책임자(Chief Security Technology Officer)였다.
* Humans are the weakest link in any security system. - Kevin Mitnick
  * 기업체 중에는 모토로라, 썬 마이크로시스템즈, NFC 등이 그에게 해킹당했다.
  * Mitnick은 약 5년 간의 복역을 마치고 현재 저술가 및 보안 컨설턴트로 활동하고 있다.
* Korea is what world hackers call a 'hot place'. - Eugene Kaspersky
  * IT 인프라는 매우 활발하면서 정보 보안 수준은 떨어지기 때문이다.
  * Kaspersky는 세계 4위 정보 보안 업체인 러시아 Kaspersky Lab의 창업자 겸 대표이사(CEO)이다.

### 2.1.2 Management Processes
* 2.1: Management Is the Hard Part
  * 기술은 구체적이다 (Technology Is Concrete)
    * 장치 및 전선은 시각화 할 수 있다.
    * 장치 및 소프트웨어 작동은 이해할 수 있다.
  * 관리는 추상적이다 (Management Is Abstract)
  * 관리가 더 중요하다 (Management Is More Important)
    * Security is a process, not a product. - Bruce Schneier -

### 2.1.3 The Need for a Disciplined Security Management Process
* 2.1: The Need for Comprehensive Security (Figure 2-3)
  * 포괄적인 보안(Comprehensive security): 수비자는 공격이 일어날 수 있는 모든 진입로를 닫아야 한다.
  * 공격자가 공격에 성공하려면 보호되지 않은 진입로 하나만 있으면 된다. 아무리 다른 진입로의 보안이 철저하더라도 한 진입로가 뚫리면 말짱 도루묵이다.
* 2.1: Weakest Link Figure (Figure 2-4)
  1. 방화벽 관리자는 필터링 규칙을 제정한다
  2. 방화벽은 들어오는 모든 패킷을 검사한다
  3. 방화벽은 각 손실된 패킷에 대한 정보를 로그 파일에 저장한다
  4. 방화벽 관리자가 로그 파일을 읽고 문제를 찾는다

* 2.1: Management Is the Hard Part
  * 너무 추상적이다
  * 포괄적인 보안(Comprehensive security)이 필요하다
    * 그러나 가장 약한 링크(weakest links)는 뚫릴 수 있다
  * 많은 자원을 보호해야 한다
* 2.1: Security Management Is a Disciplined Process
  * 복잡하다
    * 비공식적으로 관리될 수 없다
  * 공식적인 프로세스가 필요하다
    * 보안 관리에서 계획되는 일련의 작업
    * 연간 계획
    * 개별 대응책을 기획하고 개발하는 프로세스
    * ... ...
  * 지속적인 프로세스
    * 중간에 그만두면 실패다
  * 준수 규정(Compliance Regulations)
    * 체계적인 보안 관리 프로세스를 채택해야 할 필요성 제고

### 2.1.4 The Plan-Protect-Respond Cycle
* 2.1: The Plan-Protect-Respond Cycle for Security Management (Figure 2-6)
  * Plan -> Protect -> Respond -> Plan -> ...
* 2.1: Systems Lifte Cycle (Figure 2-7)
  * SLC(Ssystems Life Cycle)는 SDLC(Systems Development Life Cycle)를 넘어서 운용 용도(operational use)를 포함합니다. SLC thinking은 보안에서 중요하다.
* Deliverables of the SDLC (SDLC의 결과물)
  * Preliminary Investigation
    * Approved Feasibility Study
  * System Anaylsis
    * Provlem Specifications
  * System Design
    * Design Specifications
  * System Development
    * Coded and Tested System
  * System Implementation
    * System converted Users trained
  * System Maintenance
    * Operational System Documentation completed
  * Preliminary ...
 
### 2.1.5 Vision in Planning
* 전망 (Vision)
  * 회사와 직원 및 외부 세계에 대한 자신의 역할을 이해하는 것이 그 밖의 모든 것을 주도한다.
* 조력자로서의 보안 (Security as an Enabler)
  * 보안은 종종 예방책으로 생각된다.
    * 하지만 보안은 조력자이기도 하다.
  * 보안이 좋으면 불가능한 일을 할 수 있다.
    * 예를 들어 다른 회사와 조직 간 시스템에 참여하기
    * SNMP SET 명령을 사용하여 시스템을 원격으로 관리하기 등
  * 불편을 줄이기 위해선 프로젝트에 일찍 참여해야 한다.

* 사용자의 긍정적인 비전(Positive Vision of Users)
  * 사용자들을 악의적이거나 어리석은 것으로 보면 안 된다.
  * 어리석다는 것은 교육을 제대로 받지 않았다는 뜻이며, 이것은 보안 문제이다.
  * 사용자들의 부정적인 여론을 들어주면 안 된다.

* 보안을 경찰이나 군대로 간주해서는 안 된다.
  * 이는 사용자의 부정적인 여론을 만든다.
  * 경찰은 범죄를 예방하지 않고 단지 처벌할 뿐이다. 그러나 보안은 공격을 방지해야 한다.
  * 군대는 치명적인 힘을 사용할 수 있다. 하지만 보안은 정작 처벌조차 할 수 없다 (그건 HR이 한다)

* 새로운 비전이 필요 (Need New Vision)
  * 미숙한 자손을 양육하는 어머니
* 사용자들이 당신과 함께 협조해주지 않으면 제대로 효과를 낼 수 없다
  * 상담, 상담, 상담 (consultation)

### 2.1.6 Strategic IT Security Planning
* 2.1: Strategic IT Security Planning
* 현재 IT 보안 허점(Gaps) 파악하기
* 원동력 파악하기
  * Threat Environment
  * Compliance laws and regulations
  * Corporate structure changes, such as mergers
* 보호가 필요한 기업 자원 식별하기
  * 모든 리소스를 열거
  * 감도(sensitivity) 별로 각각 평가

* 개선 계획 개발 (Develop Remediation Plans)
  * 모든 보안 허점에 대한 개선 계획 개발하기
  * 보호가 잘 되고 있지 않다면 모든 리소스에 대한 수정 계획을 개발해야 한다
* 투자 포트폴리오 개발 (Develop an Investment Portfolio)
  * 모든 허점을 즉시 막을 수는 없다
  * 우선 가장 큰 수익을 제공할 프로젝트 선택하고
  * 그것을 구현

## 2.2 Compliance Laws and Regulations
### 2.2.1 Legal Driving Forces
* 원동력 (Driving Forces)
  * 기업이 보안 계획, 보호 및 대응을 변경하도록 요구하는 것 (are things that require a firm to change its security planning, protection, and response)
  * 사전적 정의: 무언가를 추진하기 위해 힘을 가하는 행위

* 규정 준수 법률 및 규정 (Compliance Laws and Regulations)
  * Compliance laws and regulations는 기업 보안에 대한 요구사항을 제정한다
    * 문서에 관련된 규정들이 엄격하다
    * 신원 관리 규정이 엄격한 경향이 있다
  * Compliance는 비용이 많이들 수 있다
  * 많은 Compliance laws and regulations이 있으며 그 수가 급증하고 있다

***컴플라이언스 (Compliance)**
* 법규 준수 / 준법 감시 / 내부 통제 등의 의미
* 컴플라이언스 프로그램 (compliance program)
* “사업 추진 과정에서 기업이 자발적으로 관련 법규를 준수하도록 하기 위한 일련의 시스템”
* 컴플라이언스 프로그램을 기업윤리까지 포괄하는 의미로 이해하는 경우도 있고, 
이러한 의미에서 "ethics and compliance program" 이라는 표현이 사용되기도 함

### 2.2.2 Sarbanes-Oxley
* 2002년 Sarbanes–Oxley 법 (Sarbanes-Oxley Act of 2002)
  * 2002년 대규모 기업 금융 사기 (Massice corporate financial frauds in 2002)
  * 법률은 기업이 재무보고 프로세스의 중대한 결함을 보고하도록 요구한다
  * Material deficiency은 significant deficiency 그 자체 또는 significant deficiency들의 조합을 뜻하는 것으로,
연간 및 중간 재무 제표의 심한 왜곡을 감지 및 방지하는 데에 실패할 가능성이 희박하다
  * 심한 왜곡이 실제로 발생하는지 여부는 중요하지 않다. 단지 그것이 발생할 수 있고 감지하지 못 할 가능성이 희박하다는 것이다.
  * material 편차는 ±5%에 불과하다
  * material deficiencies를 보고하는 회사는 일반적으로 주식 가치의 하락을 알아내곤 최고 재무 책임자(CFO, Chief Financil Officer)가 사퇴할 수 있습니다.

### 2.2.3 Privacy Protection Laws
* 개인 정보 보호법 (Data Breach Notification Laws)
  * 2002년 유럽 연합(EU, European Union) 데이터 보호 지침 (The European Union (EU) Data Protection Directive of 2002)
  * 다른 많은 국가들이 강력한 상업 데이터 개인 정보 보호법을 가지고 있다
  * 미국 Gramm–Leach–Bliley Act (GLBA)
  * 의료 기관 내 게인 데이터를 위한 미국 의료 보험 휴대성 및 책임법 (HIPPA)

### 2.2.4 Data Breach Notification Laws
* 데이터 침해 신고법 (Data Breach Notification Laws)
  * 캘리포니아의 SB 1386
  * 개인 정보가 노출된 캘리포니아 시민에게 통보를 하도록 규정한다
  * 기업은 더 이상 데이터 침해를 숨길 수 없다

### 2.2.5 The Federal Trade Commission
* 연방 거래위원회 (Federal Trade commission (FTC))
  * 개인 정보를 보호하지 못한 회사를 처벌할 수 있다
  * 벌금을 부과하고 몇 년 동안 외부 감사를 받도록 한다

### 2.2.6 Industry Accreditation
* 산업 인증 (Industry Accreditation)
  * 병원 등
  * 종종 공인된 보안 요구 사항이 있다

### 2.2.7 PCI-DSS
* PCI-DSS
  * 결제 카드 산업-데이터 보안 표준 (Payment Card Industry-Data Security Standards)
  * 신용 카드를 받는 모든 회사에 적용된다
  * 각각 특정 하위 요구 사항이있는 12개의 일반 요구 사항이 있다

### 2.2.8 FISMA
* FISMA
  * 2002년 연방 정보 보안 관리법 (Federal Information Security Management Act of 2002)
  * 미국 정부 연방 기관에서 사용하거나 운영하는 모든 정보 시스템에 대한 프로세스
  * 또한 미국 정부 기관을 대신하는 계약자 또는 기타 조직
  * <u>인정 후 인증</u>
  * 지속적인 모니터링
  * 보호 대신 문서화에 초점을 맞췄다는 비판이 있다

**Certification and Accreditation**
* 인증은 특정 설계 및 구현이 지정된 보안 집합을 충족하는 범위를 설정하는 인증 프로세스를 지원하기 위해 정보 시스템의 기술적 및 비 기술적 보안 제어 (안전 장치)에 대한 포괄적 인 평가입니다 요구 사항.
  * 인증은 승인 된 기술 집합의 구현을 기반으로 정보 시스템이 허용 가능한 수준의 위험에서 작동하도록 승인되었다는 고위 기관 관리 (DAA (지정 인증 기관) 또는 PAA (Principal Accrediting Authority))의 공식 선언입니다. , 관리 및 절차 적 보안 제어 (안전 장치).

**인증과 인정**
* 인증은 제품, 서비스, 시스템 또는 조직이 설정된 표준이나 기술규정에 적합하다는 것을 보증해주는 절차
* 인정은 인증을 수행하는 기관을 평가하여 그 능력을 보증하는 절차

## 2.3 Organization
### 2.3.1 Chief Security Officers
* 최고 보안 책임자 (CSO, Chief Secyruty Officer)
  * 최고 정보 보안 책임자(CISO, Chief Information Security Officer)라고도 한다

### 2.3.2 Should You Place Security withins IT?
IT 보안 부서는 어디에 있어야 하나? (Where to Locate IT Sscurity?)
* IT 부서 내부 (Within IT)
  * 장점
    * 기술 공유가 가능하다
    * IT 부서 책임자 (CIO, Chief Information Officer)가 보안을 담당한다
  * 단점
    * 독립성 없음
    * 아무도 지켜 보는 사람이 없다
* IT 부서 외부
    * 독립성 있다
    * 관찰자를 관찰할 수 있다 ?
      * IT 부서와 IT 부서 책임자(CIO)에게 호각(호루라기)을 불 수 있다
    * 기술 공유가 불가능하다
    * 책임소재가 불분명해진다 (사고 발생 시 서로 남의 부서 탓)
      * 벅은 아무데도 멈추지 않는다
    * 하지만 이것이 가장 일반적으로 권장되는 방법이다
* 하이브리드
  * 계획, 정책 수립 및 감사는 IT 외부에 배치
  * 방화벽 운영 같은 운영쪽 업무는 IT 내에 배치

### 2.3.3 Top Management Support
* 최고 경영진의 지원 (Top Management Support)
  * 예산
  * 갈등 중재
  * 본인이 먼저 본보기가 되기
    * 보안 절차를 스스로 따르기

### 2.3.4 Relationships with Other Departments
다른 부서와의 관계 (Relationships with Other Departments)
* 특별한 관계 (Special relationship)
  *  윤리, 규정 준수(compliance) 및 개인 정보 보호 책임자
  *  인사부 (교육, 고용, 해고, 제재 위반자)
  *  법무부
  *  감사부
     *  IT 감사, 내부 감사, 재무 감사
     *  다음 중 하나에 보안 감사를 배치할 수 있따
     *  이는 보안 기능으로부터 독립성을 제공한다
* 시설(건물) 관리
* 균일한 보안
* 모든 기업 부서
  * 단순히 벽에 정책을 던져서는 안 된다
* 비즈니스 파트너
  * IT 기업 시스템을 함께 연결해야 한다
  * 이를 수행하기 전에, 보안 평가에 있어 내사(내부 조사)를 진행해야 한다

### 2.3.5 Outsourcing IT Security
IT 보안 아웃소싱 (Outsourcing IT Security)
* 오직 이메일 또는 웹서비스로만
* 관리 보안 서비스 공급자 (Manged Security Service Providers (MSSPs))
  * 대부분의 IT 보안 기능을  MSSP에게 아웃소싱
    * 침입 탐지 및 취약성 테스트
    * 그러나 일반적인 정책은 아니다
  * 장점
    * 전문성과 실무 기반 지식
    * 독립성
  * 기업이 MSSP를 사용해야 하는 이유가 무엇인가?

2.3: Managed Security Service Provider (MSSP) (Figure 2-12)
1. Logged events
2. Encrpted and compressed log data
3. Analysis
4. Small number of alerts
5. Vulnerability test
* MSSP는 실무기반 경험을 가지고 있다. MSSP는 자기네 보안 직원을 감싸는 독립성을 가지고 있다. 그러므로 계약은 로그 판독 요구사항(log reading requirements)를 주의깊게 명시해야 한다.

What are Managed Security Services (MSS)?
* MSS는 실시간 모니터링, 보호, 에스컬레이션 및 대응 프로세스를 통해 보안 서비스의 현장 및 원격 모니터링 및 관리를 제공한다
* 제공되는 많은 관리 서비스는 다음과 같다
  * 방화벽, 침입탐지시스템(IDS), 가살 사설망(VPN), 라우터, 안티 바이러스/콘텐츠 검사, 주기적인 취약성 또는 침투 연구/테스트

Who are the players in the MSSP space?
* IBM, HP, ... 많다

## 2.4 Risk Analysis

## 2.5 Technical Security Architecture
## 2.6 Policy-Driven Implementation
## 2.7 Governance Frameworks
## 2.8 Conclusion