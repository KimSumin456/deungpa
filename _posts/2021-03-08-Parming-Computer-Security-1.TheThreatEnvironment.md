---
title:  "[정보보호]1.The Threat Environment"
excerpt: "등록금 파먹기 - 정보보호 파먹기 (Parming Computer Security)"
toc: true
toc_sticky: true

categories:
- 정보보호
tags:
- 등록금 파먹기
- 정보보호
- The Threat Environment
---

## Preview
1. Introduction and Terminology
2. Employee and Ex-Employee Threats
3. Malware
4. Hackers And Attacks
5. The Criminal Era
6. Competitor Threats
7. Cyberware And Cyberterror
8. Conclusion

<!--1-1강-->
## 1.1 Introduction
### 1.1.1 Basic Security Terminology
* Threat Environment
  * Threat Environment (TE)는 기업이 직면한 공격 및 공격자의 유형들로 구성된다.
  * 지피지기 백전불태. 먼저 어떻게 공격 당할 수 있는 지를 알아야 그 다음에 어떻게 방어해낼 지도 계획할 수 있으므로 TE를 이해하는 일은 중요하다.
* Security Goals: CIA
  * Confidentiality: 기밀성. 정보가 컴퓨터에 있거나 네트워크를 통해 이동하는 동안 사람들이 민감한 정보를 읽을 수 없어야 한다는 특성이다.
  * Integrity: 무결성. 정보가 컴퓨터에 있거나 네트워크를 통해 이동하는 동안 공격자가 정보를 변경하거나 파괴할 수 없어야 한다는 특성이다.
  * Availability or Authorization: 가용성 또는 인증. 정보를 사용할 수 있는 권한이 있는 사람이 그렇게 하는 것을 막지 않아야 한다는 특성이다.
* Compromises (= Incidents, Breaches): 성공적인 공격. 위협이 비즈니스에 해를 끼치는 데 성공한 경우를 말한다.
* Countermeasures (= safeguards, protections, controls): 공격을 막는 데 사용하는 방법을 의미한다. Countermeaures의 유형으로는 Preventative(예방), Detective(감지), Corrective(수정)이 있다.
### 1.1.2 The TJX Data Breach (Case 1)
* The TJX Companies, Inc. (TJX)
  * TJX는 여러 국가에 2500개 이상의 소매점을 둔 백화점 회사이다.
* 발단 (Discovery)
  * 2006.12.18. TJX는 "의심스러운 소프트웨어"를 그들의 컴퓨터 시스템에서 발견했다. 이에 보안 전문가들을 호출한 결과, 그들은 침입 및 데이터 손실 가능성이 있음을 확인했다.
 한 달 뒤에야 소비자에게 시스템을 고칠 시간을 확보하고 법집행기관이 조사를 할 수 있도록 이 사실을 알렸다.
  * 조사 결과 2005년과 2006년에 두 차례의 공격이 있었으며, TJX는 4570만 개인 정보 기록이 피해를 입었다고 추정했다. 그들의 45만 5천명의 고객에 대한 훨씬 더 많은 정보가 도난 당했다.
* 침입 (The Break-Ins)
  * 먼저 보안이 약한 소매점의 무선 네트워크로 침입한 후, 메사추세츠의 중앙 처리 시스템까지 들어간 방식이었다.
  * 오랫동안 존재했음에도 불구하고 감지하지 못 했으며, 80 GB 데이터가 유출됐다.
  * 캐나다 개인정보 위원회(Canadian Privacy Commission)은 보관되지 않았어야 할 데이터를 저장하는 열악한 암호화를 지적했다.
  * **TJX는 CIA 목표 중 'Confidentiality'를 달성하지 못했다고 볼 수 있다.**
* **WEP (Wired Equivalent Privacy)**
  * 무선 네트워크의 보안을 위해 1987년에 만들어진 RC4 암호화 기법을 기본으로 사용하는 알고리즘이다.
  * 64비트나 128비트로 사용 가능한데, 64비트는 40비트 만큼을 RC4 키를 사용하기 때문에, 실질적으로 안전성이 2^40^밖에 되지 않아 보안성이 취약하다.
* The Payment Card Industry-Data Secuirty Standard (PCI-DSS)
  * 신용 카드 구매를 받는 회사에 대한 규정
  * 규정을 준수하지 경우 신용 카드 처리 권한을 잃을 수 있다
  * 12가지 필수 제어 목표가 있다
  * TJX는 규정을 준수하지 않는다는 것을 알았었다 (12개의 제어 목표 중 3개만 충족했던 것으로 나중에 확인됐다)
  * Visa는 진행 계획 보고서에 의거해 2005년에 TJX를 연장했었다.
* 후폭풍: 소송 및 조사 (The Fall-Out: Lawsuits and Investiagations)
  * Visa와 MasterCard는 9400만 개의 계정이 도난당한 것으로 추정했다 (TJX의 추정치의 2배)
  * 카드 재발급 및 기타 비용을 충당하기위해 대부분의 은행 및 은행 협회와 함께 6500만 달러 이상을 지불했다
  * 사건을 해결하기 위해 41개 주에서 970만 달러가 들었다
  * 455000명의 피해자들에게 ID 도용 피해 보상을 지급했다
  * 그 외의 피해자들에겐 30 달러 바우처를 제공했다
  * 해킹범 알버트 곤잘레스는 징역 20년을 선고받았다
### 1.1.3 The Sony Data Breaches (Case 2)
* Sony Corporation
  * 1946년에 설립된 일본 다국적 기업으로 전자, 게임 엔테테인먼트 및 금융 서비스에 중점을 둔다.
  * 약 146300명의 직원을 고용하고 있으며 연간 매출을 약 722억 달러이다.
  * 소니는 텔레비전, 디지털 이미징, 오디오/비디오 하드웨어, PC, 반도체, 전자 부품 및 게임 플랫폼으로 널리 알려져 있다.
* 첫 번째 공격 (The First Attack)
  * 2011년 4월 17일 - 19일
  * 대규모 지진, 쓰나미, 원자로 붕괴 몇 주 후에 공격이 발생했다.
  * SQL injection을 사용해 7700만 계정을 도용했따.
  * PlayStation Network (PSN)에 대한 액세스를 사용중지했다.
  * 침입 1주일 후인 4월 26일에 공개적으로 침입을 인정했다.
  * 히라이 가즈오 대표이사(CEO)는 공개 사과를 했다.
  * 해킹 그룹 "Anonymous"가 의심을 받았다.
* 두 번째 공격 (The Second Attack)
  * 2011년 5월 1일 소니 온라인 엔테테이먼트 (Sony Online Entertainment)
  * 유사한 SQL injection 공격이 추가적으로 2460만 계정을 도용하는 데 사용됐다.
  * 모든 소니 온라인 엔테테이먼트 서버에 대한 액세스를 차단했다.
  * 5월 4일에 히라이 가즈오 대표이사(CEO)는 미국 의회에 추가적인 공격을 방지하기위한 절차에 대한 서면 답변을 발표했다.
  * 5월 15일에 일부 PSN 서비스는 온라인으로 시작했다.
* 세 번째 공격 (The Third Attack)
  * 2011년 6월 2일 소니픽쳐스닷컴 (SonyPictures.com) 
  * 유사한 SQL injection 공격이 추가 100만 계정을 도용하는 데 사용했다.
  * 소니픽셔츠닷컴은 즉각적으로 종료되었다.
  * 해킹 그룹 LulzSec은 책임 주장 및 언론 성명을 발표했다.
* **SQL Injection**
  * SQL injection이란 웹 애플리케이션에 조작된(modified) SQL 문을 날려서 데이터베이스를 수정하는 공격이다.
  * 공격자는 예외적인 입력을 보낼 수 있고, 웹 브라우저를 통해 전체 데이터베이스를 읽고 쓰고 삭제할 수 있게 된다.
  * 항상 참(always true)인 값을 입력함으로써 로그인을 통과한다.
* The attackers
  * LulzSec 및 Anonymous 구성원이 모두 관련된 것으로 밝혀졌다.
  * 조치 호츠는 플레이스테이션3를 탈취한 혐의로 소니로부터 고소당했었다.
  * 이에 Anonymous는 조치 호츠를 상대로 낸 소송에 대해 소니에 대한 공격 직전 "OpSony" 작전을 개시한다고 발표했었다.
  * 2011년 9월 22일 코디 크레싱어는 소니 공격에 가담한 혐의로 체포되어 유죄 판결을 받았다.
  * 122년형을 선고 받은 헥터 몬세구르는 다른 공격자들의 신원을 확인한 핵심 정보원이었다.
* 후폭풍: 소송 및 조사 (The Fall-Out: Lawsuits and Investigations)
  * 소니는 1년 무료 신분 도용 상담 서비스, 1개월 무료 게임 이용 및 몇가지 제한된 무료 게임을 제공했다.
  * 현재까지 소니 데이터 침해와 직접적으로 연관된 신용 사기는 없다.
  * "보안 조치가 충분하지 않았기 때문에" 영국에서 395000 달러의 벌금을 부과했다.
  * 소니는 1억 7100만 달러로 손실을 추정한다.
  * 하지만 소니의 평판에 대한 피해는 추정하기 어렵다.

## 1.2 Employee And Ex-Employee Threats
### 1.2.1 Employees and Ex-Employees Are Dangerous
* Employees and Ex-Employees are Dangerous. 현 직원과 전 직원은 위험하다.
  * 내부 시스템에 대한 지식이 있다
  * 시스템에 액세스할 수 있는 권한이 있다
  * 탐지를 피하는 방법을 알고 있다
  * 일반적으로 직원들은 신뢰를 받는다
* IT와 IT 보안 전문가들이 가장 위험도가 큰 직원이다
  * 사무팀 <- IT 개발팀 <- IT 보안팀 <- ??? 그러면 IT 보안팀은 누가 감시할 것인가에 대한 문제가 있다
### 1.2.2 Employee and Ex-Employee Threats의 종류
* Employee Sabotage
  * 하드웨어, 소프트웨어, 데이터의 파괴
  * 컴퓨터에 Plant time bomb 또는 logic bomb
    * 예) logic bomb: while(1) { fork }
* Employe Hacking
  * 해킹이란 권한 없이 또는 권한을 넘어서서 의도적으로 컴퓨터 자원에 접근하는 행위이다.
  * 권한(또는 인증, Authorization)이 핵심(key)이다.
    * 권한이 없다면 단지 보안 테스트(실습)를 하려고 했든, 실제로 백만 달러를 훔치려 했든 간에 처벌은 똑같다.
* Employee Financial Theft
  * 자산의 남용
  * 재산의 도난
* Employee Theft of Intellectual Property
  * IPR - 저작권, 특허, 상호, 상표
  * 영업 비밀 - 계획, 약속, 제품 공식화, 비즈니스 프로세스 및 회사가 경쟁사로부터 비밀로 유지하려는 기타 정보
* Employee Extortion
  * 가해자(Perpetrator)는 피해자(victime)의 이익에 반하는 조치를 취하겠다고 위협하여 돈이나 기타 물품을 얻으려고 한다.
* Sexual or Racial Harassment of Other Employees
  * 이메일을 통해
  * 음란물 게시 등
* Internet Abuse
  * 성희롱 소송이나 바이러스로 이어질 수 있는 음란물 다운로드
  * 저작권 위반 처벌을 받을 수 있는 불법 복제된 소프트웨어, 음악 및 비디오 다운로드
  * 직장에서 과도한 개인 인터넷 사용
* Carelessness
  * 민감한 정보가 포함된 컴퓨터 또는 데이터 미디어의 손실하는 부주의
  * 또는 그러한 정보의 도용을 초래하는 부주의
* Other "Internal" Attackers
  * 계약 근로자
  * 계약 회사의 근로자

## 1.3 Malware
### 1.3.1 Classic Malware: Viruses and Worms
* Malware
  * "유해한 소프트웨어"의 총칭
* Viruses
  * 피해자 컴퓨터에 있는 합법적인 프로그램에 붙어서 실행되는(attach themselves) 프로그램
  * 오늘날 주로 이메일, 또는 인스턴트 메시지(카카오톡, 디스코드 등)나 파일 전송 등으로 전파된다
* Worms
  * 다른 프로그램에 직접 연결되지 않고 혼자 실행되는 하나의 완전한 전체 프로그램 (Full programs that do not attach themselves to other programs)
  * 바이러스와 마찬가지로 이메일, 인스턴트 메시지, 파일 전송에 의해 전파될 수 있다 
* Blended Threats
  * Malware는 웜(worms), 바이러스(viruses), 모바일 코드(mobile code)가 포함된 손상된 웹페이지 등 여러가지 방법으로 전파된다
* Payloads
  * 피해를 입히는 코드의 조각
    * 악성 코드는 TCP segment의 [ Header | Payload ] Payload에 붙어있다
  * 전파 후 바이러스 및 웜에 의해 구현된다
  * 악성 페이로드는 큰 피해를 입히도록 설계되어있다

### 1.3.2 Trojan Horses and Rootkits
* Nonmobile Malware
  * 점점 늘어나는 공격 기술 중 하나를 통해 사용자의 컴퓨터에 깔려야 한다
  * 해커에 의해 컴퓨터에 깔린다
  * 페이로드의 일부로 바이러스나 웜에 의해 컴퓨터에 깔린다
  * 피해자는 웹사이트나 FTP사이트로부터 프로그램을 다운로드하도록 유인 당할 수 있다
  * 웹페이지에서 실행되는 모바일 코드(mobile code)는 비 모바일 악성 코드(nonmobile malware)를 다운로드 받을 수 있다
* Trojan Horses
  * 이름을 사칭하여 기존 시스템 파일을 대체하는 프로그램
  * Remote Access Trojans (RATs)
    * 피해자의 PC 원격 제어
  * Downloaders
    * 다운로더(≒설치 마법사)가 설치된 후 더 큰 트로이 목마를 다운로드 하는 작은 트로이 목마
  * Spyware
    * 대상에 관한 정보를 수집하여 적에게 제공하는 프로그램
    * 너무 많고 민감한 개인 정보를 저장하는 쿠키
    * 키 입력 로거(Keystroke loggers)
    * 비밀번호 도용(Password-stealing) 스파이웨어
    * 데이터 마이닝 스파이웨어
  * Rootkits
    * super user account(root, administrator, etc.)를 제어한다
    * 파일 시스템 탐색으로부터 스스로를 숨길 수 있다
    * 탐색으로부터 malware를 숨길 수 있다
    * 감지하기 매우 어렵다 (일반적인 바이러스 백신 프로그램은 루트킷을 거의 찾지 못한다)

### 1.3.3 Other Malware Attacks
* Mobile Code
  * 웹페이지에서 실행하는 코드
  * 코드는 웹페이지가 다운로드될 때 자동적으로 실행된다
  * 컴퓨터에 취약점이 있으면 손상을 입힐 수 있다
    * Javascript, Microsoft Active-X controls, etc.
* Dynamic Web Page
  * 클라이언트는 HTTP Requset를 보낸다
  * 서버는 프로그램을 실행한다
    * CGI, ASP, JSP, AJAX
  * 다시 서버는 HTTP 응답을 보낸다
* Active Web Page
  * 클라이언트는 HTTP Request를 보낸다
  * 다시 서버는 HTML Page와 클라이언트 프로그램을 보낸다
    * Applet, ActiveX control
  * Applet
    * 제한이 많다
      * 서명된 것만 동작한다 (Signed applet)
    * 브라우저에 내장된 후 파괴된다
      * 그래서 느리다 (그래서 안 쓴다)
  * Active X
    * 무료다
    * 클라이언트의 컴퓨터에 남아있는다
      * 그래서 빠르다
* Social Engineering in Malware
  * 사회 공학은 보안 정책에 위배되는 작업을 수행하도록 사용자를 속이려고 한다
  * 사회 공학을 사용하는 여러가지 Malware 유형
    * 스팸, 피싱, 스피어 피싱 (개인 또는 특정 그룹을 대상으로 함), 사기 (신분 위장 등), 파밍 (DNS table 바꾸기, 가짜 사이트 등)

<!--1-2강-->
## 1.4 Hackers And Attacks
### 1.4.1 Traditional Motives
* Traditional Hackers
  * 과거 해킹의 동기는 스릴감, 실력 자랑, 힘의 과시, 다른 해커들 사이에서 평판을 높이기 위함 정도였다
  * 종종 그 여파로 손상이 있는 정도였고, 자잘한 범죄에 연관되는 경우가 많았다

### 1.4.2 Anatomy of a Hack
* ※ 잠깐 용어
  * Exploit: 공격을 할 수 있는 소스코드
  * Spoofing: 내가 공격을 해도 공격을 받는 사람이 모르게 숨기는 행위
  * Sniffing: 지나가는 패킷을 캡쳐하는 행위

* 정찰 (Reconnaissance probes)
  * 어찌됐든 아무리 뛰어난 해커라도 IP가 있어야 할 수 있다. 따라서 막무가내로라도 IP 주소를 알아내야 한다.
  * 먼저 예비 피해자를 찾아내기 위해 IP 주소를 스캔한다.
  * 그 예비 피해자 호스트에서 어떤 서비스가 열려 있는지 알아보기 위해 포트도 스캔한다
* *Probe and Exploit Attack Packets (Figure 1-11)*
  1. 아무데나 IP 주소 스캐닝 패킷을 보낸다
  2. 응답이 오면 그 IP 주소에 호스트가 있음을 확인한다
  3. 운영 중인 애플리케이션을 알아내기 위해 포트 스캐닝 패킷을 보낸다
  4. 예를 들어 80번 포트라는 응답이 오면 특정 IP 주소가 웹서버임을 알아낸다
  5. 그럼 알아낸 IP 주소로 익스플로잇 패킷(exploit packet)을 보낸다
* 착취 (The exploit)
  * attacker's exploit: 공격자가 컴퓨터에 침입하기 위해 사용하는 특정 공격 방법
  * exploiting the host: 익스플로잇(exploit)을 실현하는 행위
* *Source IP Address Spoofing (Figure 1-12)*
  1. 공격자 A가 자신의 IP 주소가 대신 B의 IP 주소를 발신 IP 주소(source IP address)로 한 패킷을 C에게 보낸다
  2. B는 C에게 응답을 보낸다
  * 이렇게 함으로써 공격자 A는 자신의 신원을 숨길 수 있다

* *Chain of attack computers (Figure 1-13)*
  * 공격자는 피해자 컴퓨터의 체인을 타고 공격한다.
  * 프로브 및 익스플로잇 패킷(probe and exploit packets)에는 체인에 있는 마지막 컴퓨터의 소스 IP 주소가 포함된다.
  * 최종 공격 컴퓨터는 피해자 컴퓨터의 응답을 받아 공격자에게 다시 전달한다.
  * 잘 하면 피해자는 최종 공격 컴퓨터부터 공격을 추적 해낼 수 있다.
  * 그러나 공격은 일반적으로 몇 대의 컴퓨터에서만 추적 할 수 있다.
  1. Attacker -> Compromised attack host -> Compromised attack host -> Target host
* **Cyber Kill Chain**
  1. Reconnaissance: 정보 수집
  2. Weaponization: 수집된 정보를 가지고 취약점에 가장 효과적인 공격을 모색
  3. Delivery: USB 또는 이메일 통해서 전달
  4. Exploitation: 익스플로잇 설치 및 실행
  5. Installation: 실제 말웨어 설치
  6. Command & Control (C2): C2 서버에서 추가 정보 파악
  7. Actions On Objectives: 실제 행동 개시

### 1.4.3 Social Enginerring in an Attack
* Social Engineering
  * 사회 공학은 자주 해킹에 사용된다.
    * 전화를 걸어 암호 및 기타 기밀 정보를 요청한다
    * 흥미로운 제목으로 이메일 공격 메시지를 보낸다
    * 편승(Piggybacking)
    * 어깨 너머 훔쳐보기(Shoulder surfing)
    * 위장(Pretexting)
    * 기타
  * 기술적 약점보다 인간의 약점에 초점을 맞추기 때문에 잘 성공한다.

### 1.4.4 Denial-of-Service Attacks
* Denial-of-Service (DoS) Attacks
  * 합법적인 사용자가 서버 또는 전체 네트워크를 사용할 수 없도록 만드는 공격이다
  * 일반적으로 피해자에게 대량의 공격 메시지를 보내는 방식이다
  * Distributed DoS (DDoS) 공격 (Figure 1-15)
    * 공격자는 봇을 제어하고, 봇은 공격 패킷을 피해자에게 쏟아보낸다
* *Distributed Denial-of-Service (DDoS) Flooding Attack (Figure 1-12)*

### 1.4.5 Skill Levels
* Skill Levels
  * Expert attackers
    * 전문 공격자는 사실 강력한 기술력과 끈질긴 끈기가 필요하다
    * 전문 공격자는 일부 작업을 자동화하기 위해 해커 스크립트를 만든다
    * 바이러스 및 기타 악성 소프트웨어를 작성하기 위한 스크립트도 사용할 수 있습니다.
  * Script kiddies
    * 스크립트 키즈들은 그러한 스크립트를 사용해 공격한다
    * 스크립트 키즈들은 기술력이 낮다
    * 스크립트 키즈들은 숫자가 많기 때문에 위험하다
      * 실제로 초등학교 여름방학에 학생들이 PC방에 가서 여러가지 공격이 늘어난다고도 한다

### 1.4.6 서비스거부(DoS) 공격 유형
* 대역폭 잠식 (flooding) 공격
  * 서버와 연결되어 있는 특정 네트워크 구간의 Bandwidth를 고갈시키기
* 서비스 / 장비 부하 유발 공격
  * TCP/IP 자체의 취약성을 이용하기
  * Ack으로 대답 안 하고 Syn 요청만 계속 보내기
* 특징 서비스 방해 공격
  * 메일 서버, 웹 서버 등 특정 취약점 공격하기

### 1.4.7 서비스거부(DoS) 공격 방어
* DNS sink hole
  * 좀비 PC도 통신을 하려면 어쨌든 DNS를 거쳐가야 한다. 이때 DNS가 좀비 PC의 IP 변환 요청을 받으면 싱크홀 서버의 IP로 응답함으로써
 추가적인 피해 및 확산을 방지하는 기법
* 사이버 공격의 패러다임이 바뀌면서 DoS 공격은 줄어들고 있다.
  * 상대방 조직의 수준을 확인하고 및 마비시키려는 목적 -> 악성 코드를 통해 금전적 이익을 취하려는 목적

### 1.4.8 최근 공격 사례
1. 7.7 대란
2. 3.4 DDoS 공격
3. 2011.04. 농협전산망 장애
4. 2013.03. 사이버테러 (TN, KBS, MBC, 농협, 신한은행)
5. 2014.12. 한수원 해킹

## 1.5 The Criminal Era
* The Criminal Era
* 오늘날 대부분의 공격자는 전통적인 범죄 동기를 가진 직업 범죄자들이다.
* IT 공격에 기존의 범죄 공격 전략(사기 등)을 접목한다.

* 많은 사이버 범죄 조직은 국제적이다.
  * 이는 기소를 어렵게 만든다.
  * 한 국가의 시민이 다른 국가의 공격자에게 부정한 상품을 전달해주는 중간 유통업자로 만든다.
* 사이버 범죄자들은 블랙 마켓 포럼을 사용한다.
  *  신용 카드 번호 및 신원 정보
  *  취약점
  *  익스플로잇(exploit) 소프트웨어 (종종 업데이트 계약 포함)

* Fraud
  *  사기에서 공격자는 피해자가 스스로 재정적 이익에 반하는 행동을 하도록 피해자를 속인다.
  *  범죄자들은 네트워크를 통해 전통적인 사기와 새로운 사기를 수행하는 방법을 배우고 있다.
  *  또한 클릭 사기(click fraud)와 같은 새로운 유형의 사기가 있다.

* Financial and Intellectual Property Theft
  * 다른 범죄자 또는 경쟁자에게 판매 할 수있는 돈이나 지적 재산을 훔친다.

* Extortion
  * 돈을 지불하지 않으면 DoS 공격이나 훔친 정보를 공개하겠다고 위협한다.

* Stealing Sensitive Data about Customers and Employees
  * 카딩(Carding) (신용 카드 번호 도용)
  * 은행 계좌 도용
  * 온라인 주식 계좌 도용
  * 신분 도용
    * 자동차 또는 집 구입과 같은 대규모 거래에서 피해자를 대표하기에 좋은 신원 정보를 훔친다.

* Corporate Identity Theft
  * 전체 기업의 아이덴티티를 훔친다.
  * 회사를 대신하여 신용 카드를 발급 받는다.
  * 대규모 거래에서 기업을 사칭한다.
  * 기업의 소유권도 가질 수 있다.

## 1.6 Competitor Threats
* Commercial Espionage
  * 기밀성에 대한 공격
  * 공공 정보 수집
    * 회사 웹 사이트 및 공개 문서
    * 직원의 Facebook 페이지 등
  * 영업 비밀 스파이 활동
    * 회사가 그러한 비밀에 대해 합당한(reasonable) 보호를 실시했던 경우에만 유출에 대한 소송을 제기할 수 있다.
    * 합리성(Reasonableness)은 비밀과 산업 보안 관행의 민감성을 반영한다.
  * 영업 비밀 도용 접근법
    * 가로 채기, 해킹 및 기타 전통적인 사이버 범죄를 통한 도난
    * 직원에게 뇌물 공세
    * 전 직원을 고용하고 영업 비밀을 요구하거나 수락
  * 국가 정보 기관이 상업적 스파이 활동에 참여

* Denial-of-Service Attacks by Competitors
  * 가용성(availability)에 대한 공격
  * 희귀하지만 파괴적일 수 있음

## 1.7 Cyberwar And Cyberterror
* Cyberware and Cyberterror
  * cyberwar: 국가 정부의 공격
  * cyberterror: 조직화된 테러리스트의 공격
  * 악몽 위협(Nightmare threats)
    * 범죄자에 의한 공격보다 훨씬 더 큰 공격 가능성
* Cyberwar
  * 국가 정부의 컴퓨터 기반 공격
  * 스파이 활동
  * 금융 및 통신 인프라를 손상시키는 사이버 전용 공격
  * 기존의 물리적 공격을 강화하기 위해
    * 물리적 공격과 함께 (또는 물리적 공격 대신) IT 인프라 공격
    * 적의 명령과 통제 체제 마비시키기
    * 선전(propaganda) 공격에 참여
* Cyberterror
  * 테러리스트 또는 테러리스트 그룹의 공격
  * IT 자원(resources)를 직접 공격할 수 있다
  * 인터넷을 사용하여 채용 및 조직력 강화
  * 인터넷을 사용하여 물리적 공격 강화
    * 최초 대응자 간의 커뮤니케이션 붕괴
    * 사이버 공격을 사용하여 물리적 공격 테러를 증가
  * 공격 자금을 위해 컴퓨터 범죄로 전환

* 추가 자료
  * 국제정치 전문가 Hoseph Nye의 컬럼: Cyberspace Wars
  * 2011년 5월, 미 WSJ 보도: 전쟁행위로의 사이버 공격 논의
  * 사이버 위협 및 공격의 개요
    * 사이버 공격 (Cyber Attack)
      * 인터넷을 통해 다른 컴퓨터에 불법 접속하여 손상을 입히려는 행동
      * 특정 서버를 정해 그 서버만을 대상으로 불법 접속
      * 불특정 다수 컴퓨터의 시스템 약점을 악용하여 무차별적으로 악성 데이터 전송
    * 사이버 전쟁 (Cyber Warfare)
      * 다른 국가의 시스테믈 대상으로 한 정치적 성격을 가진 사이버 공격
      * 2011년 6월 미국 국방부는 국가 기간시설을 흔들 수 있는 적성국가의 사이버 공격을 '전쟁행위'로 간주,
 미사일 등 무력으로 대응한다는 방침을 세움
  * 3.20 APT 사이버테러

## 1.8 Conclusion
