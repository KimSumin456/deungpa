---
title:  "[정보보호] 4. Secure Networks"
excerpt: "등록금 파먹기 - 정보보호 파먹기 (Parming Computer Security)"
toc: true
toc_sticky: true

categories:
- 정보보호
tags:
- 등록금 파먹기
- 정보보호
- Secure Networks
---

## Preview
<!--Chap4-1-->
1.	Introduction
2.	Denial-of-Service (DoS) Attacks
<!--Chap4-2-->
3.	ARP Poisoning
4.	Access Control for Networks
<!--Chap4-3-->
5.	Ethernet Security
6.	Wireless Security

## 4.0 Learning Objectives & Orientation
### Learning Objectives
- Describe the goals of creating secure networks.
- Explain how denial-of-service attacks work.
- Explain how ARP poisoning works.
- Know why access controls are important for networks.
- Explain how to secure Ethernet networks.
- Describe wireless (WLAN) security standards.
- Describe potential attacks against wireless networks.
### Orientation
-	Chapter 3 looked at how cryptography can protect data being sent across networks
- Chapter 4 looks at how networks themselves are attacked
- We will look at how attackers can gain unauthorized access to networks
- We will also look at how attackers can alter the normal operation of a network
- We will look at both wired (LAN) and wireless (WLAN) networks

<!--4-1장-->
## 4.1 Introduction
4장에서는 네트워크가 어떻게 공격을 받는지를 알아볼 것입니다.  
예전에는 메시지들이 손, 전화, 라디오에 의해 아날로그한 방식으로 전달되었습니다. 따라서 그 당시 주요 보안 목표는 메시지 비밀을 보호하고(confidentiality), 메시지가 올바른 곳으로부터 오는 것을 보장하고(authenticity), 메시지가 수정되지 않는 것을 보장하는 것이었습니다.  
그러나 현대 전기 통신 네트워크의 출현과, 함께 새로운 보안 문제가 해결되어야 한다는 것이 명백해졌습니다.  
메시지를 전달한다는 의미는 멈추거나, 느려지거나, 수정될 수 있다는 의미가 되었고, 메시지가 전해지는 루트도 수정될 수 있습니다. 또한 공격자는 통신 채널에 대한 접근을 할 수 있습니다.

### 4.1.1 Creating Secure Networks
안전한 네트워크 환경을 만들기 위해 고려해야하는 목표에는 크게 4가지가 있습니다.

#### 1. Availability
: users have access to information services and network resources

#### 2. Confidentiality
: prevent unauthorized users from gaining information about the network

#### 3. Functionality
: preventing attackers from altering the capabilities, or normal operation of the network

#### 4. Acess control
: keep attackers or unauthorized employees from accessing internal resources

### 4.1.2 Future of Secure Networks
#### Death of the perimeter  
The castle model
* Good guys inside, bad guys outsie

#### Rise of the City
The city model
* No distinct perimeter
* Access based on who you are

## 4.2. Denial-of-Service (DoS) Attacks
Denial-of-Service (DoS) 공격은 서버나 네트워크가 사용자들에게 서비스를 제공할 수 없도록 패킷 flooding을 통해 공격합니다.

### 4.2.1 Denial of Service ... But Not an Attack
* 모든 서비스 장애(service interruptions)가 공격에 의한 것은 아닙니다.

#### Faulty coding
* 잘못된(faulty), 조잡한(shoddy) 코딩에 의해 서비스 손실(loss of service)가 발생할 수 있습니다.

#### Referals from large sites
* 대형 사이트가 소형 사이트로 링크를 할 때 급격히 증가한 트래픽에 압도당해 서비스 손실이 발생할 수 있습니다.
* 악의는 없으나 DoS 공격과 같은 영향을 받습니다.

### 4.2.2 Goal of DoS Attacks
* DoS 공격의 최종 목표는 해를 입히는 것입니다. 기업에게 온라인 판매, 평판, 생산성, 고객 충성도와 관련해 손해를 발생시킬 수 있습니다.

#### Stop critical services
* 기업의 중요 서비스를 공격해 사용자들의 이용을 방해합니다.
* 회사 인트라넷을 공격해 직원들의 업무를 방해합니다.

#### Degrade services
* 위와 같이 주요 서비스에 대한 전형적인 DoS 공격은 알아내기 쉽고 오래 지속할 수 없습니다.
* 그러나 가장 위험한 공격은 알아차리지도 못하게 하는 공격입니다. 조금씩 서비스를 저하시키는 공격(attack that slowly degrades services)은 서비스에 급격한 변화를 일으키지 않기 때문에 감지하기가 어렵습니다.
* 그래서 네트워크 관리자는 단순히 정말 트래픽이 증가한 건지 점진적인 DoS 공격인지 구별하기 힘들게 되고, 그에 따라 추가적인 대역폭(bandwidth)와 하드웨어 및 소프트웨어를 구매하는 데에 불필요한 지출을 하게 만듭니다.

### 4.2.3 Methods of DoS Attacks
공격자가 DoS 공격을 수행하는 방법에는 크게 4가지가 있습니다.

#### 1. Direct and indirect attacks
* A **direct attack** occurs when an attacker tries to flood a victim with a stream of packets directly from the attackers computer.
* An **indirect attack** tries to flood the victim computer in the same way, but <u>the attacker’s IP address is spoofed (i.e., faked)</u> and the attack appears to come from another computer

Flooding
* Direct or indirect attacks can only succeed if the attacker can flood the victim with more requests than the victim can handle.
* The attacker must have more bandwidth, memory (RAM), and/or CPU power than the victim.
* Given the size of most corporate server farms, it’s unlikely that a single user will be able to generate enough traffic to successfully degrade existing services.
  * Corporate servers can handle more requests than the single attacker can generate

Spoofing
* attackers prefer to use spoofed IP addresses that hide their IP address.
* But the attacker cannot get direct feedback about the attack.
  * They must rely on indirect means of monitoring the attack, such as sending requests to the victim from another computer to test for availability.

Backscatter
* Backscatter occurs when a victim sends responses to the spoofed IP address used by the attacker, and inadvertently floods an unintended victim

Types of Packets Sent
* Sometimes DoS attacks are named after the type of packet sent during the attack, rather than the attack method.
* Some of the DoS attacks explained in thissection can use one or multiple types of packets.
* Below are just a few of the types of packets that could be sent in a DoS attack (Figure 4-4).
  * SYN Flood:  victim is flooded with SYN packets in an attempt to make many half-open TCP (Transmission Control Protocol) connections. Memory is allocated for each false connection causing the victim to run out of memory and crash.
  * Ping Flood: A victim is flooded with ICMP (Internet Control Message Protocol) packets (also known as echo requests) that appear to be normal supervisory traffic. Bandwidth and CPU cycles are consumed to the point where the victim crashes.
  * HTTP Flood: A victim, typically a webserver, is flooded with application layer web requests. The webserver crashes due to insufficient memory and CPU power.

**SYN flood**
1. Attacker sends a TCP SYN segment to a port
2. The application program sends back a SYN/ACK segment and sets aside resources
3. The attacker never sends back an ACK, so the victim keeps the resources reserved
4. The victim soon runs out of resources and crashes or can no longer serve legitimate traffic 

#### 2. Intermediary
* Botmaster controls bots(=intermediaries)

**distributed denial-of-service (DDoS) attack**
1. Intermediaries, typically referred to as bots, are actually compromised hosts running malware controlled by the attacker.
2. The DoS attack begins when the botmaster, the attacker who controls the bots, sends a signal for the bots to attack the victim.
3. An attacker controlling bots in a coordinated attack against a victim

Bots
* Updatable DoS attack programs

Handlers
* **Handler** can update the software to change the type of attack the bot can do
  * May sell or lease the botnet to other criminals
* Handler can update the bot to fix bugs

Peer-to-Peer Redirect
* Similar to a DDoS attack, a **peer-to-peer (P2P) redirect attack** uses many hosts to overwhelm a victim using normal P2P traffic.
* A P2P redirect attack differs from a traditional DDoS attack in several ways.
  * The attacker does not have to control each of the hosts (i.e., make them bots) used to attack the victim.
  * The attacker just needs to convince the hosts to redirect their legitimate P2P traffic (Step 2) from the P2P server to the victim (Step 3).

#### 3. Reflected Attack
* Similar to the P2P redirect, a **reflected attack** uses responses from legitimate services to flood a victim.

**Distributed Reflected Denial-of-Service (DRDoS) attack**
1. the attacker sends spoofed requests to existing legitimate servers
2. Servers then send all responses to the victim
3. a victim may try to block the servers that are reflecting the attack.

Smurf flood
* A Smurf flood is a variation of a reflected attack that takes advantage of an incorrectly configured network device (router) to flood a victim.
  1. Spoofed ICMP echo requests: The attacker sends a spoofed ICMP echo request to a network device (Step 1) that has broadcasting enabled to all internal hosts (Figure 4-9).
  2. Incorrectly configured router: The network device forwards the echo request to all internal hosts (Step 2).
  3. Broadcasts to internal hosts: All internal hosts respond to the spoofed ICMP(Internet Control Message Protocol) echo request (Step 3) and the victim is flooded.
  4. All internal hosts respond to the spoofed ICMP echo request (Step 3) and the victim is flooded. The attacker benefits from a multiplier effect because a single ICMP request is responded to by multiple hosts.

#### 4. Sending Malformed Packets
* Malformed packet will cause the victim to crash

Ping of death
* ping of death is a well-known older attack that uses an illegally large IP packet to crash the victim’s operating system.
* This flaw has been fixed and the attack is rarely used anymore.
 
SMS of death
* malformed SMS messages (also known as text messages) can be used to crash cell phones in an attack

### 4.2.4 Defending Against Denial-of-Service Attacks
#### Black holing
* Drop all packets from an IP address
* Black-holing an attacker is not a good long-term strategy
  * because attackers can quickly change source IP addresses.
  * An attacker may knowingly spoof attack packets with the IP addresses of a corporate partner

#### Validating the handshake
* Create false opens
  * Only when the firewall gets back an ACK, which happens only in legitimate connections, does the firewall send the original SYN segment on to the server for which it was intended.
  * Do not set aside(별도의) resources until sender acknowledges

#### Rate limiting (속도 제한)
* For more subtle DoS attacks, Set reasonable limits on certain types of traffic
* But Can frustrate legitimate users

DoS Protection Is a Community Problem
* If an organization’s access line to the Internet becomes overloaded, it cannot solve the problem itself (문제 자체를)
* Organization’s ISP or other upstream agencies must help

## 4.3. ARP Poisoning
Normal ARP Operation
* Resolves IP addresses into MAC addresses
* Hosts build ARP tables
  * Send ARP requests
    * Receive ARP responses
* Only host with specified IP address responds
* Switches forward packets based on MAC addresses
* All hosts trust ARP replies
* ARP replies can be spoofed

### 4.3.1 ARP Poisoning
* ARP 스푸핑(ARP spoofing)은 근거리 통신망(LAN) 하에서 주소 결정 프로토콜(ARP) 메시지를 이용하여 상대방의 데이터 패킷을 중간에서 가로채는 중간자 공격 기법이다. 이 공격은 데이터 링크 상의 프로토콜인 ARP 프로토콜을 이용하기 때문에 근거리상의 통신에서만 사용할 수 있는 공격이다.
* 이 기법을 사용한 공격의 경우 특별한 이상 증상이 쉽게 나타나지 않기 때문에 사용자는 특별한 도구를 사용하지 않는 이상 쉽게 자신이 공격당하고 있다는 사실을 확인하기 힘들다.
* 출처: 위키백과

ARP(Address Resolution Protocol) Poisoning
* Reroute for a man-in-the-middle attack
  * **ARP poisoning only works on LAN traffic**
  * Rerouting traffic using ARP poisoning is an attack on both the <u>functionality and confidentiality</u> of a network.
  * An ARP DoS attack is an attack on the <u>availability</u> of a network by rerouting traffic to a nonexistent host, and thereby forcing it to be dropped.
* Continuous stream of spoofed ARP replies
* False ARP replies redirect traffic
* Gateway and hosts are poisoned
  * All hosts send traffic through the attacker
  * The gateway sends all traffic through the attacker

### 4.3.2 ARP DoS Attack
ARP DoS Attack
* Continuous stream of spoofed ARP replies to all hosts
  * Hosts should send to nonexistent MAC address
* Directs traffic to a nonexistent host
  * Packets are dropped when no recipient is found

### 4.3.3 Preventing ARP Poisoning
Preventing ARP Poisoning
* Static tables
  * Difficult to manage in large organizations
* Limit local access
  * Most large corporations do a pretty good job of keeping the bad guys out

Example: SLAAC Attack
* IPv6의 우선순위가 높은 점을 이용해 갈취(?)
* Introduction of IPv6 router to IPv4 network
  * Traffic is automatically rerouted
* Hosts are dual stacked and don't notice the attack
* Alternate DNS server can be used to redirect all internal hosts

## 4.4. Access Control for Networks
* Corporate LANs must also provide access controls that allow only authenticated and authorized personnel on the network.
* The remainder of this chapter will focus on securing wired (Ethernet) and wireless networks.

### 4.4.1 LAN Connections
* Computers connect to the LAN through Ethernet switches. Some do so via 4-pair UTP cords connected to wall jacks.
* Although all-wireless LANs are possible, most wireless communication in LANs is used to link wireless clients to the firm’s wired Ethernet network. 

### 4.4.2 Access Control Threats
* Traditionally, Ethernet LANs offered no access control security. Any intruder who entered a corporate building could walk up to any wall jack and plug in a notebook computer.
* Wireless LANs have even deeper access threats. A drive-by hacker can sit in a car outside the corporate walls.

### 4.4.3 Eaversdropping Threats
* For both wired LANs and wireless LANs, once intruders gain access, they can use a packet sniffer to intercept and read legitimate traffic.

## 4.5. Ethernet Security
### 4.5.1 Ethernet and 802.1X
* The 802.1X standard provides access control to prevent illegitimate clients from associating with a network.
* the name of the 802.1X standard is Port-based Access Control.
* is implemented on specific ports of an Ethernet workgroup switch. 
* The heavy authentication work is done on a central authentication server, rather than on the switch.
  * reduced cost
  * consistency
  * immediacy

### 4.5.2 The Extensible Authentication Protocl (EAP)
* 확장 가능 인증 프로토콜(Extensible Authentication Protocol, EAP은 네트워크와 인터넷 연결에 사용되는 인증 프레임워크이다. RFC 3748(구 RFC 2284)에 정의되어 있으며 RFC 5247에 의해 업데이트된다. EAP는 EAP 방식들에 의해 생성되는 자료와 파라미터의 전송 및 이용을 제공하기 위한 인증 프레임워크이다. RFC가 정의한 방식들, 벤더에 특화된 방식들, 새로운 제안들이 다수 존재한다. EAP는 **유선 프로토콜이 아니며** 인터페이스와 포맷의 정보를 정의하기만 한다. EAP를 사용하는 각 프로토콜은 프로토콜 메시지 내의 사용자 EAP 메시지로 캡슐화하는 방법을 정의한다.
* 출처: 위키백과
* 802.1X relies on another protocol, the Extensible Authentication Protocol (EAP), to govern the specifics of authentication interactions.
* an authentication framework frequently used in wireless networks and Point-to-Point connections
* an authentication framework providing for the transport and usage of keying material and parameters generated by EAP methods.
* **EAP is not a wire protocol; instead it only defines message formats.**
* Each protocol that uses EAP defines a way to encapsulate EAP messages within that protocol's messages.

1. EAP Start
2. EAP Request
3. EAP Response
4. EAP Request
5. EAP Response EAP Success
6. Authentication Success Notification (outside of the EAP protocol)

호스트 - wall jack - switch - server -> EAP 시작

장점: 인증 정보 하나만 저장하면 돼서 관리 편함, verifier 역할 분담

EAP 종류 다양, 환경에 맞게 선택
provider의 특성과 요구에 따라 달라질 수 있음

### 4.5.3 RADIUS Servers
* RADIUS는 네트워킹 프로토콜로 사용자가 네트워크에 연결하고 네트워크 서비스를 받기위한 중앙 집중화된 인증, 인가, 회계 (AAA, 회계 Accounting은 인증, 인가 후 각종 사후 처리를 맡는다.) 관리를 제공한다. RADIUS는 1991년 서버 접근 인증, 회계 프로토콜로써 Livingston Enterprises, Inc. 에서 개발했다. 그리고 후에 IETF표준으로 등재되었다.
* EAP와 함께 인증을 위해 서버가 사용하는 프로토콜
* Remote Authentication Dial In User Service (RADIUS) is a networking protocol that provides centralized Authentication, Authorization, and Accounting (AAA) management for computers to connect and use a network service.
* EAP is only used in the first A (Authentication) in AAA(Authentication, Authorization, and Auditing)
* UDP 위에, ... 인증서버는 인터넷 구간에서 radius를 같이 사용한다

## 4.6. Wireless Security
* wireless security는 공격 루트가 정해져있지 않고, 보이지 않기 때문에 더 취약하다 (보안 이슈가 많다)

Evil twin 공격
* 시그널이 강할 수록 더 많은 기기를 유인된다는 점을 이용해 진짜 AP 옆에 Rogue AP를 심어놓는 공격
* 해결책
  * MAC 주소를 관리, 업무 외 잡일 금지
  * VPN으로 encryption을 통한 보안 터널 만들기
    * end-to-end
    * password

DoS
* wireless network에서는 bandwith, server 뿐만 아니라 physically jamming도 가능하다는 점이 있다
  * deassocication을 보낸다

802.11i
* 한마디로 802.11의 secure version. WPA1/2를 포함하는 개념이다
  * 802.1x mode는 인증 프레임 구조다
* AP까지만 포함하는 outer mode와, 서버까지 포함하는 inter mode가 있다
* 인증 서버 없이 클라이언트-AP가 1:1로 매번 new session key를 이용해 인증하는 personal mode와, 인증 서버가 있는 enterprise mode가 있다
* WEP: RC4 40bit -> WPA1: RC4 128bit -> WPA2: AES
  * RSN - RSNA (RSNA는 기관이름이다)

Wireless IDS도 가능하다
* AP로 데이터를 수집하고, 특히 Rogue AP를 찾아내기도 한다

* Wireless network는 주파수에 실어보내니 어려워 보이는 코딩한다고 해서 암호화가 있는 게 아니다. 즉 자체 보안성은 없다.
* SSID나 MAC 주소도 결국 패킷에서 알아낼 수 있기 때문에 이를 통해 보안을 하는 게 그렇게 좋은 방법은 아니다

<!--### 4.6.1 Wireless Attacks
### 4.6.2 Unauthorized Network Access
### 4.6.3 Evil Twin Access Points
### 4.6.4 Wireless Denial of Service
### 4.6.5 Wireless LAN Security with 802.11i
### 4.6.6 Core Wireless Security Protocols
### 4.6.7 Wired Equivalent Privacy (WEP)
### 4.6.8 Cracking WEP
### 4.6.9 Perspective
### 4.6.10 Wi-Fi Protected Access (WPA™)
### 4.6.11 Pre-Shared Key (PSK) Mode
### 4.6.12 Wireless Intrusion Detection System
### 4.6.13 False 802.11 Security Measures
### 4.6.14 Implementing 802.11i or WPA is Easier

## 4.7 Conclusion-->