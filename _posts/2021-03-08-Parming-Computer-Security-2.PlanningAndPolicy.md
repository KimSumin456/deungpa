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
Security is process, not a product. - Bruce Schneier
* 이 말은 보안 관리보다 보안 기술에 지나치게 집중하는 것은 실수라는 점을 강조합니다.
* Schneier는 BT의 최고 보안 기술 책임자(Chief Security Technology Officer)였습니다.

Humans are the weakest link in any security system. - Kevin Mitnick
* 기업체 중에는 모토로라, 썬 마이크로시스템즈, NFC 등이 그에게 해킹당했습니다.
* Mitnick은 약 5년 간의 복역을 마치고 현재 저술가 및 보안 컨설턴트로 활동하고 있습니다.

Korea is what world hackers call a 'hot place'. - Eugene Kaspersky
* IT 인프라는 매우 활발하면서 정보 보안 수준은 떨어지기 때문입니다.
* Kaspersky는 세계 4위 정보 보안 업체인 러시아 Kaspersky Lab의 창업자 겸 대표이사(CEO)입니다.

### 2.1.2 Management Processes
2.1: Management Is the Hard Part
* 기술은 구체적이다 (Technology Is Concrete)
  * 장비와 전선은 시각적으로 눈에 보인다.
  * 장치와 소프트웨어의 작동은 이해할 수 있다.
* 관리는 추상적이다 (Management Is Abstract)
* 관리가 더 중요하다 (Management Is More Important)
  * Security is a process, not a product. - Bruce Schneier -

### 2.1.3 The Need for a Disciplined Security Management Process
2.1: The Need for Comprehensive Security (Figure 2-3)
* 포괄적인 보안(Comprehensive security): 수비수는 공격이 일어날 수 있는 모든 진입로를 닫아야 합니다.
* 공격수가 공격에 성공하려면 보호되지 않은 진입로 하나만 있으면 됩니다.
  * 아무리 다른 진입로의 보안이 철저하더라도 한 진입로가 뚫리면 말짱 도루묵이라는 뜻입니다.

2.1: Weakest Link Figure (Figure 2-4)
1. 방화벽 관리자는 필터링 규칙을 제정
2. 방화벽은 들어오는 모든 패킷을 검사
3. 방화벽은 각 손실된 패킷에 대한 정보를 로그 파일에 저장
4. 방화벽 관리자가 로그 파일을 읽고 문제를 파악
* 한 구성요소의 실패가 전체 시스템의 실패를 이끈다

2.1: Management Is the Hard Part
* 너무 추상적입니다
* 포괄적인 보안(Comprehensive security)이 필요합니다
  * 그러나 가장 약한 링크(weakest links)가 뚫릴 수 있습니다
* 많은 자원들을 보호해야 합니다

2.1: Security Management Is a Disciplined Process
* 복잡합니다
  * 비공식적으로 관리될 수 없습니다
* 공식적인 프로세스가 필요합니다
  * 보안 관리(security management)에서 계획되는 일련의 작업들
  * 연간 계획
  * 개별 대응책을 기획하고 개발하는 프로세스
  * ... ...
* 지속적인 프로세스
  * 중간에 그만두면 실패입니다
* 준수 규정(Compliance Regulations)
  * 체계적인 보안 관리 프로세스를 채택해야 할 필요성을 제고합니다

### 2.1.4 The Plan-Protect-Respond Cycle
2.1: The Plan-Protect-Respond Cycle for Security Management (Figure 2-6)
* Plan -> Protect -> Respond -> Plan -> ...

2.1: Systems Lifte Cycle (Figure 2-7)
* SLC(Ssystems Life Cycle)는 SDLC(Systems Development Life Cycle)를 넘어서 실제 사용(operational use)까지 포함합니다. SLC thinking은 보안에서 중요합니다.

Deliverables of the SDLC (SDLC의 결과물)
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
전망 (Vision)
* 회사, 직원, 외부에 대한 자신의 역할 이해가 그 밖의 모든 것을 주도합니다.

조력자로서의 보안 (Security as an Enabler)
* 보안은 종종 예방책으로서 생각됩니다.
  * 하지만 보안은 조력자이기도 합니다.
* 보안이 좋으면 불가능한 일을 할 수 있습니다.
  * 예를 들어 다른 회사와 조직 간 시스템에 관여하기
  * SNMP SET 명령을 사용하여 그들의 시스템을 원격으로 관리하기 등
* 불편을 줄이기 위해선 프로젝트에 일찍 참여해야 합니다.

사용자의 긍정적인 시각 (Positive Vision of Users)
* 사용자들을 악하거나 어리석게 보면 안 됩니다.
* 어리석다는 것은 교육이 제대로 되지 않았다는 뜻이며 그것은 보안 문제입니다.
* 사용자의 부정적인 시각에 대한 무관용이 필요합니다.

보안을 경찰이나 군대로 간주해서는 안 됩니다. (Should NOt View Security as Police or Military Force)
* 이는 사용자의 부정적인 여론을 만듭니다.
* 경찰은 범죄를 예방하지 않고 단지 처벌할 뿐입니다. 그러나 보안은 공격을 방지해야 합니다.
* 군대는 치명적인 힘을 사용할 수 있습니다. 하지만 정작 보안은 처벌조차 할 수 없습니다 (그건 HR에서 합니다)

새로운 비전이 필요합니다 (Need New Vision)
* 미숙한 자식을 양육하는 어머니

사용자들이 당신과 함께 협조해주지 않으면 효과를 제대로 낼 수 없습니다 (Cannot be Effective Unless Will Work with You)
* 상담, 상담, 상담 (consultation)

### 2.1.6 Strategic IT Security Planning
현재 IT 보안 허점(Gaps) 파악하기

원동력 파악하기 (Identify Cureent IT Security Gaps)
* Threat Environment
* Compliance laws and regulations
* Corporate structure changes, such as mergers

보호가 필요한 기업 자원 식별하기 (Identify Driving Forces)
* 모든 리소스를 열거
* 민감도(sensitivity) 별로 각각 평가

개선 계획 개발 (Develop Remediation Plans)
* 모든 보안 허점에 대한 개선 계획 개발
* 보호가 잘 되고 있지 않다면 모든 리소스에 대한 수정 계획을 개발해야

투자 포트폴리오 개발 (Develop an Investment Portfolio)
* 모든 허점을 즉시 막을 수는 없습니다
* 우선 가장 큰 수익을 제공해줄 프로젝트를 선택하고
* 그것을 구현

## 2.2 Compliance Laws and Regulations
### 2.2.1 Legal Driving Forces
원동력 (Driving Forces)
* 기업이 보안 계획, 보호, 대응을 바꾸도록 요구하는 것 (are things that require a firm to change its security planning, protection, and response)
* 사전적 정의: 무언가를 추진하기 위해 힘을 가하는 행위

규정 준수 법률 및 규정 (Compliance Laws and Regulations)
* Compliance laws and regulations는 기업 보안에 대한 요구사항을 제정합니다
  * 문서에 관련된 규정들이 엄격합니다
  * 신원 관리 규정이 엄격한 경향이 있습니다
* Compliance는 비용이 많이들 수 있습니다
* 많은 Compliance laws and regulations이 있으며 그 수가 급증하고 있습니다

**컴플라이언스 (Compliance)**
* 법규 준수 / 준법 감시 / 내부 통제 등의 의미
* 컴플라이언스 프로그램 (compliance program)
* “사업 추진 과정에서 기업이 자발적으로 관련 법규를 준수하도록 하기 위한 일련의 시스템”
* 컴플라이언스 프로그램을 기업윤리까지 포괄하는 의미로 이해하는 경우도 있고, 
이러한 의미에서 "ethics and compliance program" 이라는 표현이 사용되기도 함

### 2.2.2 Sarbanes-Oxley
2002년 Sarbanes–Oxley 법 (Sarbanes-Oxley Act of 2002)
[사베인스 옥슬리법 - 위키백과](https://ko.wikipedia.org/wiki/%EC%82%AC%EB%B2%A0%EC%9D%B8%EC%8A%A4_%EC%98%A5%EC%8A%AC%EB%A6%AC%EB%B2%95)
* 2002년 거대 기업들의 잇달은 회계부정 사건들에 대한 반응으로 발효되었습니다 (Massice corporate financial frauds in 2002)
* 이 법률은 기업이 재무정보 공시(financial reporting process)에서 물자 하자(material deficiencies)를 보고하도록 요구합니다
* 물자 하자(Material deficiency)는 중대한 하자 그 자체 또는 중대한 하자들의 조합입니다.
중대한 하자(significant deficiency)는 연간/중간 재무제표의 허위 기재가 감지/방지되지 않을 가능성을 희박하게 만듭니다.
* 허위 기재가 실제로 발생하는지 여부는 중요하지 않습니다. 단지 그것이 발생할 수 있고 감지하지 못 할 가능성이 희박하다는 것입니다.
* 물자 편차(material deviation)는 ±5%에 불과합니다
* 물자 하자를 보고하는 회사는 일반적으로 주식 가치의 하락을 알아내서 최고 재무 책임자(CFO, Chief Financil Officer)가 사퇴할 수 있습니다.

### 2.2.3 Privacy Protection Laws
개인 정보 보호법 (Data Breach Notification Laws)
* 2002년 유럽 연합(EU, European Union) 데이터 보호 지침(The European Union (EU) Data Protection Directive of 2002)
* 미국 Gramm–Leach–Bliley Act (GLBA)
* 의료 기관 내 게인 데이터를 위한 미국 의료 보험 휴대성 및 책임법 (HIPPA)
* 이 외에 다른 많은 국가들도 강력한 상업 데이터 개인 정보 보호법을 가지고 있습니다

### 2.2.4 Data Breach Notification Laws
데이터 침해 신고법 (Data Breach Notification Laws)
* 캘리포니아의 SB 1386
* 캘리포니아 시민에게 그들의 개인 정보가 노출되었을 시 통보를 하도록 규정합니다
* 기업은 더 이상 데이터 침해를 숨길 수 없습니다

### 2.2.5 The Federal Trade Commission
연방 거래위원회 (Federal Trade commission (FTC))
* 개인 정보를 보호하지 못한 회사를 처벌할 수 있습니다
* 벌금을 부과하고 몇 년 동안 외부 감사를 받도록 합니다

### 2.2.6 Industry Accreditation
산업 인증 (Industry Accreditation)
* 병원 등
* 종종 공인된 보안 요구 사항이 있습니다

### 2.2.7 PCI-DSS
PCI-DSS
* 결제 카드 산업-데이터 보안 표준 (Payment Card Industry-Data Security Standards)
* 신용 카드를 받는 모든 회사에 적용됩니다
* 각각 특정 하위 요구 사항이있는 12개의 일반 요구 사항이 있습니다

### 2.2.8 FISMA
FISMA
* 2002년 연방 정보 보안 관리법 (Federal Information Security Management Act of 2002)
* 미국 정부 연방 기관에서 사용하거나 운영하는 모든 정보 시스템에 대한 프로세스
* 또한 미국 정부 기관을 대신하는 계약자 또는 기타 조직에서도
* <u>증명(인증), 그 다음 후 승인(인정) (Certification, followed by accreditation)</u>
* 지속적인 모니터링
* 보호 대신 문서화에 치중했다는 비판이 있습니다

**Certification and Accreditation**
* 인증은 특정 설계 및 구현이 특정 보안 요건을 충족하는 범위를 설정하는 인증 프로세스를 지원하기 위한 정보 시스템의 기술적 및 비기술적 보안 통제(안전장치)에 대한 포괄적인 평가
* 인정은 정보 시스템이 승인된 일련의 기술, 관리 및 절차적 보안 통제(세이프가드)의 구현에 기초하여 허용 가능한 위험 수준에서 운영되도록 승인된다는 고위 기관 관계자(DAA) 또는 PAA(Principal Accrediting Authenticated Accrediting Authority))

**인증과 인정**
* 인증은 제품, 서비스, 시스템 또는 조직이 설정된 표준이나 기술규정에 적합하다는 것을 보증해주는 절차
* 인정은 인증을 수행하는 기관을 평가하여 그 능력을 보증하는 절차

## 2.3 Organization
### 2.3.1 Chief Security Officers
최고 보안 책임자 (CSO, Chief Secyruty Officer)
* 최고 정보 보안 책임자(CISO, Chief Information Security Officer)라고도 합니다

### 2.3.2 Should You Place Security withins IT?
IT 보안 부서는 어디에 있어야 하는가? (Where to Locate IT Sscurity?)
* IT 부서 내부 (Within IT)
  * 장점
    * 기술 공유가 가능하다
    * IT 부서 책임자 (CIO, Chief Information Officer)가 보안을 담당한다
  * 단점
    * 독립성 없음
    * 아무도 지켜 보는 사람이 없다
* IT 부서 외부
    * 독립성 있다
    * 관찰자를 관찰할 수 있다
      * IT 부서와 IT 부서 책임자(CIO)에게 호각(호루라기)을 불 수 있다
    * 기술 공유가 불가능하다
    * 책임소재가 불분명해진다 (사고 발생 시 서로 남의 부서 탓)
      * 책임은 어디에도 없다!
    * 하지만 이것이 보통 가장 권장되는 방법이다
* 하이브리드
  * 계획, 정책 수립 및 감사는 IT 외부에 배치
  * 방화벽 운영 같은 운영쪽 업무는 IT 내에 배치

### 2.3.3 Top Management Support
최고 경영진의 지원 (Top Management Support)
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
     *  다음 중 하나에 보안 감사를 배치할 수 있습니다
     *  이는 보안 기능으로부터 독립성을 제공합니다
* 시설(건물) 관리
* 균일한 보안
* 모든 기업 부서
  * 단순히 정책을 벽에 던져서는 안 됩니다
* 비즈니스 파트너
  * IT 기업 시스템을 함께 연결해야 합니다
  * 이를 수행하기 전에, 보안 평가에 있어 내사(내부 조사)를 진행해야 합니다

### 2.3.5 Outsourcing IT Security
IT 보안 아웃소싱 (Outsourcing IT Security)
* 오직 이메일 또는 웹서비스로만
* 관리 보안 서비스 공급자 (Manged Security Service Providers (MSSPs))
  * 대부분의 IT 보안 기능을  MSSP에게 아웃소싱
    * 침입 탐지 및 취약성 테스트
    * 그러나 일반적인 정책은 아닙니다
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
* MSSP는 실무기반 경험을 가지고 있습니다. 단 MSSP는 자기네 보안 직원을 감싸는 독립성을 가지고 있습니다. 그러므로 계약은 로그 판독 요구사항(log reading requirements)를 주의깊게 명시해야 합니다.

What are Managed Security Services (MSS)?
* MSS는 실시간 모니터링, 보호, 에스컬레이션 및 대응 프로세스를 통해 보안 서비스의 현장 및 원격 모니터링 및 관리를 제공합니다
* 제공되는 많은 관리 서비스는 다음과 같습니다
  * 방화벽, 침입탐지시스템(IDS), 가살 사설망(VPN), 라우터, 안티 바이러스/콘텐츠 검사, 주기적인 취약성 또는 침투 연구/테스트

Who are the players in the MSSP space?
* IBM, HP, ... 많다

<!--2-2강-->
## 2.4 Risk Analysis
### 2.4.1 Reasonable Risk
현실 (Realities)
* 절대 위험을 제거할 수 없습니다
* "정보 보증(Information assurance)"은 불가능합니다
* 위험을 제거할 수 없지만 관리할 수는 있습니다.

정보보증(IA)
* 정보보호(민간) + 중요 정보통신 기반 시설 보호, 침입 탐지 및 대응, 기반 시스템 복원(국가보안)
  * -> 국가 기반 시설의 기밀성, 가용성, 신뢰성 보장

### 2.4.2 Classic Risk Analysis Calculations
고전적인 위험 분석 계산 (Classic Risk Analysis Calculations)
* 발생 가능한 손실(loss)을 계산
* 대책(countermeasure)이 손실 가능성을 얼마나 낮출 지를 계산
* 그 대책이 투자하는 비용만큼의 이익을 생성하는지 여부를 결정합니다

고전적인 위험 분석 계산 방법
* **AV x EF = SLE**
  * AV(Asset Value): 자산가치
  * EF(Exposure Factor): 노출계수
    * compromise가 발생할 시 AV 대비 loss의 비율
  * SLE(Single Loss Expectancy): 단일예상손실
    * compromise가 발생할 시 예상되는 loss
* **SLE x ARO = ALE**
  * ARO(Annualized Rate of Occurrence): 연간발생률
    * compromise의 연간 발생 확률
  * ALE(Annualized Loss Expectancy): 연간예상손실
    * 이러한 유형의 compromise로 인해 예상되는 연간 손실

2.4: Classic Risk Analysis Calculations (Figure 2-14)  
**고전적인 위험 분석 계산 방법 예제(표) 참고**

### 2.4.3 Problems with Classic Risk Analysis Calculations
매해 일정하지 않은 현금유동성 (Uneven Multiyear Casch Flows)
* 공격 비용과 방어 비용 모두에 관해
  * 초기: 높은 대책(countermeasure), 낮은 이익(benefit)
  * 진행할 수록: 감소, 증가
  * 연령: 높음, 낮음
* 할인된 현금 흐름을 사용하여 투자 수익률(Return On Investment, ROI)을 계산해야 합니다.
  * **순현재가치(NPV) 또는 내부수익률(ROI)**
    *	ROI: 투자수익률,IRR: 내부수익률, NPV: 순현재가치
    *	ROI = 총이익/총투자비용

총사고비용 (Total Cost of Incident (TCI))
 * 고전적인 위험 분석(Classic Risk Analysis Calculations)에서 노출 계수(EF)는 자산이 손실되는 비율을 추정합니다.
   * 그러나 대부분의 경우 자산 손실로 인한 피해가 발생하지 않습니다.
   * 예를 들어, 개인식별정보가 도난당한 경우 발생하는 비용은 크지만 자산은 남아 있습니다.
 * 따라서 사고의 총 비용(Total Cost of Incident, TCI)을 계산해야 합니다.
   * 수리, 소송 및 기타 여러 요인의 비용을 포함합니다.

대책과 리소스 간의 다대다 관계 (Many-to-Many Relationships between Countermeasures and Resources)
* 고전적인 위험 분석은 하나의 대책이 하나의 리소스를 보호한다고 가정합니다.
  * 그러나 방화벽과 같은 단일 대책은 종종 많은 리소스를 보호합니다(클라이언트 및 서버용 f/w).(1:다)
  * 그리고 서버의 데이터와 같은 단일 리소스는 종종 여러 대책(f/w를 사용하는 서버, IDS, 호스트 보안, VPN 통신 등)에 의해 보호됩니다.(다:1)
* 따라서 고전적인 위험 분석은 확장이 어렵습니다.

연간 발생률 파악 불가능 (Impossibilit of Knowing the Annualized Rate of Occurrence)
* 단순히 이것을 추정 할 수 있는 방법이 없습니다.
  * 이것이 고전적인 위험 분석의 가장 큰 단점입니다.
* 결과적으로, 기업은 고전적인 위험 분석 대신 종종 위험 수준별로(by risk level) 자원을 평가합니다.

"냉정한 사고"가 가지는 문제 (Problems with "Hard-Headed Thinking")
* 보안 이익(Security benefits)은 정량화하기 어렵습니다.
* "정량적인 수치(hard numbers)"만 바라는 경우 보안에 적은 투자(underinvest)를 합니다
  * "숫자는 생각을 몰아냅니다."

### 2.4.4 Responding to Risk
위험 감소 (Risk Reduction)
* 대부분의 사람들이 고려하는 접근 방식
* 피해를 줄이기 위한 대책 설치
* 위험 분석이 대책을 정당화하는 경우에만 의미가 있습니다.

위험 감수 (Risk Acceptance)
* 손실로부터 보호하는 것이 너무 비싸고 효과는 작다면 손실이 발생할 때 그냥 감수합니다.
* 운석 충돌에 대비하여 지붕을 무장하지 않는 것과 같습니다. (사서 고생 X)

위험 양도 (보험) (Risk Transference (insurance))
* 보안 관련 손실에 대한 보험 구매
* 드문 공격엔 적합하지만, 만약 공격이 발생하면 매우 큰 피해를 입을 수 있습니다.
* 자연 재해, 사이버 전쟁/테러와 같은 취약한 보안으로 인해 발생한 손실에 대해선 보험 처리되지 않습니다.

위험 회피 (Risk Avoidance)
* 위험한 행동을 하지 말기
* IT 보안에 분노를 일으킬 수 있습니다.

복기: 위험에 직면했을 때 네 가지 선택 사항 (Recap: Four Choices when You Face Risk)
* 위험 감소 (Risk reduction)
* 위험 수용 (Risk acceptance)
* 위험 양도 (Risk transference)
* 위험 회피 (Risk avoidance)

## 2.5 Technical Security Architecture
## 2.6 Policy-Driven Implementation

## 2.7 Governance Frameworks
2.7: Governance Frameworks (Figure 2-25)
* IT Governance Frameworks: 기업이 IT 보안 계획, 구현, 모니터링 및 점진적 개선에 접근하는 체계적인 방법을 제공함으로써 기업을 돕습니다.

**정보기술 거버넌스 (IT Govenrnance)**
* IT Governance
  * 조직의 정보기술이 조직의 전략과 목표를 유지하고 확대하는 것을 보장하는 리더쉽, 조직구조 그리고 프로세스로 구성
  * 단순한 관리(Management)가 아닌 기업을 움직이는 힘, 즉 지배구조
  * IT 전략의 개발 및 추진을 관리하고 이를 통해 비즈니스와 IT를 융합시키기 위해 이사회, 경영진, IT 관리자가 추진하는 조직 기능
  * 기업 거버넌스의 통합적이 부분이며 조직의 전략과 목표달성을 뒷받침하는 조직 구조와 프로세스, 그리고 리더십으로 구성
* IT Governance의 필요성
  * 조직이 IT에 의존할수록 IT 환경의 취약성은 조직 전체의 문제로 다가오게 되고 의존성이 커짐에 따라 IT 투자를 통한 비즈니스 가치 창출과 IT 관련 리스크 관리, 예방 및 대처를 위해서 IT Governance가 필요
* IT Management의 문제점
  * 이사회, 최고 경영층과 IT 관리자 사이의 괴리
  * 이사회, 최고 경영층의 관심이 부족
  * 기업 전략과의 연계가 미약
  * IT 관리자의 책임만 있고, 권한은 부족

2-25: Governance Frameworks
* Governance Framework
  * 계획, 구현 및 감독 방법을 구체화합니다.
  * COSO
  * CobiT
  * **ISO/EIC**
  * ITIL

### 2.7.1 COSO
### 2.7.2 CobiT

### 2.7.3 The ISO/IEC 27000 Family
2.7: The ISO/IEC 27000 Family of Security Standards
* 참고

## 2.8 Conclusion
