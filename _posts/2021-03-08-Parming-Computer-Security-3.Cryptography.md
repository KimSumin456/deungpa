---
title:  "[정보보호] 3. Cryptography"
excerpt: "등록금 파먹기 - 정보보호 파먹기 (Parming Computer Security)"
toc: true
toc_sticky: true

categories:
- 정보보호
tags:
- 등록금 파먹기
- 정보보호
- Cryptography
---

## Preview
<!--Chap3-1-->
1.	What is Cryptography?
2.	Symmetric Key Encryption Ciphers
<!--Chap3-2-->
3.	Cryptographic System Standards
4.	The Negotiation Stage
5.	Initial Authentication Stage
6.	The Keying Stage
7.	Message-By-Message Authentication
<!--Chap3-3-->
8.	Quantum Security
9.	Cryptographic Systems
10.	SSL/TLS
11.	IPsec
12.	Conclusion


<!--3-1강-->
## 3.0 Learning Objectives & Orientation
### Learning Objectives
-	Explain the concept of cryptography.
-	Describe symmetric key encryption and the importance of key length.
-	Explain negotiation stage.
-	Explain initial authentication, including MS-CHAP.
-	Describe keying, including public key encryption.
-	Explain how electronic signatures, including digital signatures, digital certificates, and key-hashed message authentication codes (HMACs) work.
-	Describe public key encryption for authentication.
-	Describe quantum security.
-	Explain cryptographic systems including VPNs, SSL, and IPsec

### Orientation
-	Chapter 1 introduced the threat environment.
-	Chapter 2 introduced the plan-protect-respond cycle and covered the planning phase.
-	Chapters 3 through 9 will cover the protection phase.
-	Chapter 3 introduces cryptography, which is important in itself and which is used in many other protections.

## 3.1.	What is Cryptography?
* 암호학(Cryptography)이란 이동하거나 저장되는 메시지를 보호하기 위해 수학적 연산을 사용하는 것입니다.
 (Cryptography is the use of mathematical operations to protect messages traveling between parties or stored on a computer.)
 
### 3.1.1. Encryption for Confidentiality
* 기밀성(Confidentiality)이란 누군가가 메시지를 가로채더라도 그 메시지를 읽을 수 없는 특성을 의미합니다.
  * 기밀성은 암호학의 본질적인 목적입니다.

### 3.1.2. Terminology
* 평문(Plaintext)이란 원본 메시지를 말합니다. 오늘날 평문은 이미지, 소리, 영상 등 복합적인 데이터가 될 수 있습니다.
* 암호문(Ciphertext)이란 임의의 비트 스트림을 말합니다.
* 암호화(Encryption)란 평문을 암호문으로 바꾸는 암호학적 과정입니다.
* 복호화(Decryption)란 암호문을 평문으로 바꾸는 암호학적 과정입니다.
* 발신자(sender)는 평문을 암호화한 암호문을 수신자(receiver)에게 보냅니다. 도청자(Eavedroppers)가 메시지를 가로채더라도(intercept) 알아볼 수 없습니다. 그러나 수신자(recevier)는 암호문을 복호화한 평문을 볼 수 있습니다.
  * Figure 3-1 Symmetric Key Encryption for Confientiality
  * 강의노트 그림 참고
* 사이퍼(cipher)는 암호화와 복호화에 사용되는 특수한 수학적 과정입니다.
* 키(key)는 비트의 랜덤 스트링입니다.

* Kerchknoff's Law는 기밀성을 위해 **cipher가 아니라 key를 지켜야한다**고 말합니다.

_보안 목표 리마인드 (Remind Security Goals)_
* 기밀성은 하나의 암호화 보호일 뿐입니다 (Confidentiality is only one cryptographic protection)
* 무결성은 메시지를 변경할 수 없게 하고 변경된 경우 그 변경을 탐지할 수 있어야하는 것을 의미합니다 (Integrity means that the message cannot be changed or, if it is changed, that this change will be detected)
* 가용성 또는 인증은 자신의 신원을 다른 사람에게 증명하여 더 신뢰할 수 있도록 해야하는 것을 의미합니다 (Availability or Authentication means proving one’s identity to another so they can trust you more)
* 암호화의 CIA라고 알려져있습니다
  * 미국의 그 정보기관 CIA가 아닙니다

_보안 위협 리마인드 (Remind Security Threats)_
* 강의노트 그림 참고
* 인터셉션은 기밀성에 대한 공격입니다 (Interception: attack on confidnetiality)
* 인터럽션은 가용성에 대한 공격입니다 (Interruption: attack on availability)
* 모디피케이션은 무결성에 대한 공격입니다 (Modification: attack on intergrity)
* 패브릭케이션은 인증에 대한 공격입니다 (Fabrication: attack on authenticity)

### 3.1.3. The Simple Cipher
Figure 3-2: Example Symmetric Key Cipher
* 강의노트 그림 참고

### 3.1.4. Cryptanalysis
Cryptanalysis
* cryptanalysis란 암호 해독 및 암호 해독학을 의미합니다.
* cryptanalyst는 암호화를 크랙하고자 하는 사람입니다.
* 가장 간단한 cryptanalysis 방법은 brute-force key cracking입니다. cryptanalysts가 올바른 키를 찾을 때까지 가능한 모든 키를 무차별적으로 대입하는 방식입니다.
  * 키의 길이가 길어질 수록 brute-force key cracking을 어렵게 만듭니다.
* 사이퍼에 규칙성(regularities)이 발생하면 cryptanalyst는 키의 일부를 상당히 빠르게 알아낼 수 있습니다.
* 사이퍼의 구현이 허술해도 키의 일부가 유출될 수 있습니다.

### 3.1.5. Substitution and Transposition Ciphers
오늘날 암호의 구체적인 수학적 과정은 매우 복잡하니다. 그러나 대부분 기본적으로 치환(substitution)과 전치(transposition)라는 두 가지 기본적인 수학적 과정의 변형을 사용한 것입니다.

### 3.1.6. Substitution Ciphers
* 치환 암호(substitution ciphers)는 한 문자를 다른 문자로 대체하는 방식의 암호입니다. 하지만 문자들끼리의 순서는 변하지 않습니다.

### 3.1.7. Transposition Ciphers
* 전치 암호(transposition ciphers)는 문자들끼리의 순서를 바꾸는 방식의 암호입니다. 하지만 문자 자체는 다른 문자로 변하지 않습니다.

Figure 3-3 Transposition Cipher
* 강의노트 그림 참고

### 3.1.8. Real-world Encryption
* 오늘날 실제 암호는 높은 무작위성(randomness)을 제공하기 위해 치환 및 전치 암호를 여러 라운드에 혼합하여 사용합니다.
* 또한 문자 단위가 아니라 비트 단위로 암호화를 합니다.
* 하지만 조직의 보안 전문가가 실제 암호와 내부 과정을 이해할 필요는 없습니다. (그건 연구자(researcher)가 할 일인 듯 합니다)

### 3.1.9. Ciphers and Codes
* 사이퍼
  * 키만 알고있으면 사용 가능합니다
* 코드(codes)
  * 코드 심볼(code symbols)를 사용합니다
  * 한 메시지에 대한 코드를 여러 개 가지고있으면 cryptanalysts가 코드를 크랙하기 어렵게 만들 수 있습니다
  * 대신 코드북(codebooks)들을 미리 가지고 있어야 하고, 하나의 코드북이라도 유출된다면 모든 기밀성을 잃게됩니다

Figure 3-4 Japanese Naval Operational Code JN-25 (Simplified)
* 강의노트 그림 참고

### 3.1.10. Symmetric Key Encryption
* 대칭 키 암호화 사이퍼(symmetric key encryption cipher)
  * 암호화와 복호화를 할 때 모두 하나의 키를 사용합니다.
  * 매우 빠르고, 연산 부담이 적습니다.
  * 그래서 거의 모든 기밀성을 위한 암호화(encryption for confidentiality)들이 대칭 키 암호화 사이퍼(symmetric key encryption)를 사용합니다

* 키 길이(key length)
  * 키의 길이가 N bits일 때 만들 수 있는 키는 2<sup>N</sup>개의 경우의 수가 있습니다.
  * 이때 보통 cryptographer는 2<sup>N</sup>/2 만에 키를 크랙할 수 있다고 알려져 있습니다
  * **따라서 키의 길이가 1 bit 늘어나면, 키를 크랙하는 데 필요한 시간을 2배로 만들 수 있습니다.**
  * 오늘날 strong symmetric keys의 길이는 100 bits 이상으로 고려됩니다

Figure 3-5 Key Length and Exhaustive Search Time
* 강의노트 그림 참고

### 3.1.11. Human Issues in Cryptography
* 발신자나 수신자가 키를 비밀로 유지하지 못하면, 도청자는 키를 알아내고 모든 메시지를 읽을 수 있게 됩니다
* cryptography는 자동으로 보호를 해주는 마법이 아닙니다. 오직 기업이 암호화의 기술적 강점을 compromise하지 않는 조직 프로세스를 시행하는 경우에만 작동합니다.
 (The reality of cryptography is that it is not an automatic protection. It only works if companies have and enforce organizational processes that do not compromise the technical strengths of cryptography.)

## 3.2 Symettric Key Encrption Ciphers
symmetric key 암호화를 사용하고자 할 때, 여러가지 사이퍼들 중 하나를 선택해야 합니다.
각 사이퍼들은 강도, 속도, 컴퓨팅 요구사항 면에서 다른 특징들을 가지고 있고, 이를 잘 알고 목적에 맞게 사용할 수 있어야 합니다.
우리는 RC4, DES, 3DES, AES를 배울 것입니다.

Figure 3-6 Major Symmetric Key Encryption Ciphers

### 3.2.1. RC4
* RC4는 오늘날엔 매우 취약한 사이퍼입니다.
* 속도가 매우 빠르고, 요구 사양이 낮습니다(적은 RAM을 요구합니다).
  * 따라서 작은 디바이스에서 사용하기에 유용합니다. 그래서 초기 802.11 무선 액세스 포인트에서 기본적으로 쓰였고, 무선 LAN을 위한 WEP 암호화 시스템의 기본으로 사용되었습니다.
* 넓은 범위의 key 길이를 사용합니다.
  * 그러나 초기에 RC4의 키는 국가 수출 제한(national export restrictions) 때문에 40bit밖에 사용할 수 없었습니다. 그 결과 40bit의 RC4가 WEP의 표준 키 길이가 되었습니다.
* 안타깝게도 RC4는 사용하기에 매우 위험한 사이퍼입니다.

### 3.2.2. The Data Encryption Standard (DES)
* DES는 NIST가 제정한 암호화 표준입니다. 브루트 포스 공격을 제외하고는 모든 공격에서 살아 남았고, 호환성이 좋으며, 하드웨어 가속기에 의해 지원되기 때문에 여전히 널리 사용됩니다.
* DES 키는 56bit입니다. 남은 8bit로는 잘못된 키를 감지하는 데 쓸 수 있습니다.
  * 56bit는 주요 비즈니스 거래와 영업 비밀의 보안에 사용하기엔 너무 짧지만, 일반적인 가정의 소비자들이 사용하기엔 속도와 사양 면에서 적당합니다.

Figure 3-7 DES Block Encryption
* DES는 한 번에 64bit씩 통으로 block encryption을 합니다.

### 3.2.3. Triple DES (3DES)
* 3DES는 key size를 확장한 느린 DES입니다
* 168bit 3DES는 DES를 3번 연속 적용한 알고리즘이며 매우 강력합니다
* 112bit 3DES는 두 개의 키(첫 번째 키와 세 번째 키가 같습니다)만을 사용하는 3DES입니다
* 그러나 DES도 속도가 느리니, 3DES는 매우 느리며 비용도 비쌉니다

### 3.2.4. Advanced Encryption Standard (AES)
* AES는 사양이 적당하여 휴대용 기기에도 사용할 수 있습니다
* AES는 128, 192, 256bit 등 여러 키 길이를 제공합니다
  * 128bit의 AES를 브루트포스로 크랙하는데 100조년이 넘게 걸릴 정도로 충분히 강력합니다
* 현재 많은 암호화 시스템이 AES를 지원하고 있으며, 앞으론 AES가 기밀성을 위한 암호화에 가장 많이 쓰이게(dominate) 될 것입니다.
* 
### ~~~3.2.5. Other Symmetric Key Encryption Ciphers~~~

<!--3-2강-->
## 3.3. Cryptographic System Standards
개인과 기업은 보안에 대해 잘 알지 못 하므로, 웬만하면 전체적인 암호화 시스템을 제공해줘야 합니다.

### 3.3.1. Cryptographic System
* 암호화 시스템(cryptographic system)은 다이얼로그(dialogues)를 보호하기 위한 일련의 암호화 대응책입니다.
* 두 당사자(parties)가 암호화 시스템을 사용해 통신을 할 때엔 구체적인 암호화 시스템 표준(cryptographic system standard)이 필요합니다.
  * 널리 사용되는 암호화 시스템 표준으로는 SSL/TLS와 IPsec가 있습니다.

### 3.3.2. Initial Handshaking Stages
* 두 당사자(디바이스들 또는 프로그램들)가 암호화 시스템 표준을 통해 통신을 시작하면, Figure 3-8과 같이 three handshaking satges를 거치게 됩니다.

Figure 3-8 Cryptographic System Stages
1. Negotiation
* 이 단계에서는 먼저 사용될 암호화 방법과 옵션을 협상합니다.
* **cipher suite**란 특정 암호화 시스템 표준에 대한 특정 옵션 집합입니다.
  * SSL/TLS 연결을 하기 전에 두 당사자는 반드시 통신 세션에 대한 구체적인 cipher suite를 협상해야 합니다.
2. Initial Authentication
* 메시지는 임포스터에 의해 전송될 수도 있으므로, 통신을 시작하기 전에 두 당사자는 서로의 신원을 **인증**해야 합니다.
  * 당사자들끼리 서로를 인증하는 일을 mutual authentication이라고 합니다. 그러나 서버에 로그인을 한다던지 한 당사자만 인증을 하는 경우도 있습니다.
* Initial Authentication 단계는 Negotiation 단계 이후에 수행합니다!
  * 두 당사자가 먼저 협상을 하지 않으면, 인증은 시작할 수 조차 없기 떄문입니다.
3. Keying
* **keying**이란 키나 비밀들을 안전하게 보내는 일을 말합니다.
* Initial Authentication 단계 이후에 Key 단계를 수행합니다!
  * 키가 도용당하면 안 되기 때문입니다.

### 3.3.3. Ongoing Communication
Ongoing Communication
* three handshaking stages를 끝내고 난 뒤 통신이 시작되고 두 당사자는 많은 메시지를 주고받습니다.
* 두 당사자는 일반적으로 message-by-message 기준으로 진행되고 있는 통신 중에 몇 가지 암호화 보호 기능을 적용합니다.
  * 먼저 발신자는 **electronic signature**를 각 메시지에 추가합니다. 이렇게 하면 수신자가 message-by-message 인증을 할 수 있고, 중간에 임포스터가 가짜 메시지를 끼워넣으려는 시도를 방지할 수 있습니다.
  * 또한 우수한 electronic signature 기술은 무결성을 제공합니다. 즉 공격자가 메시지를 캡처하고 변경하면 이를 알아채고 인증 프로세스가 메시지를 거부할 수 있습니다.
  * 그리고 발신자는 기밀성을 위해 메시지 및 전자 서명을 암호화합니다.

## 3.4. The Negotiation Stage
이제부터 three handshaking stages의 각 stage들을 좀 더 자세히 살펴보도록 하겠습니다

### 3.4.1 Cipher Suite Options
* 앞서 언급했 듯이 cipher suite는 특정 암호화 시스템 표준에 대한 특정 보안 방법과 옵션의 집합입니다.
  * 초기 인증(initial authentication), 키 교환, 진행 중인 메시지의 기밀성, 인증 및 무결성을 위한 특정 방법과 옵션이 포함되어 있습니다.
* Figure 3-9는 SSL/TLS 표준에서 제공하는 선택적 암호 집합의 하위 집합들을 보여줍니다. 보안 강도가 제일 약한 것부터 오름차순으로 적혀있습니다.

Figure 3-9 Selected SSL/TLS Cipher Suites

### 3.4.2 Cipher Suite Policies
* SSL/TLS cipher suite에 따라 강도(strengths)가 다양하기 때문에 기업은 위험에 기반한 정책을 개발해야 하며, 응용 프로그램이 직면한 위험에 적합한 강도를 가진 cipher suites만 허용해야 합니다.
* IPsec 암호화 시스템 표준은 중앙에서 보안 방법 및 옵션에 대한 정책을 설정하고, 모든 통신 파트너에게 적용할 수 있습니다.

## 3.5 Initial Authentication Stage
초기 인증 방법에는 여러가지가 있습니다. 그 중 서버의 비밀번호 인증 확인을 기반으로 하는 MS-CHAP 하나만 살펴보겠습니다.

### 3.5.1 Authentication Terminology
* **supplicant**이란 자신의 신원을 증명하려는 당사자를 의미합니다. 상대방은 **verifier**이라고 합니다.
  * suuplicant는 credentials(proofs of idenity)를 verifier에게 보냅니다.
  * 상호 인증에서는 두 당사자가 supplicant와 verifier를 번갈아 맡습니다.
 
Figure 3-10 Authentications: Supplicant, Verifier, and Credentials

### 3.5.2 Hashing
* 해싱(hashing)은 암호화는 아니지만 암호 시스템이 작동하는 방법의 중요한 부분 중 하나입니다
  * MS-CHAP initial authentication을 살펴보기 전에 해싱의 작동 방식과 특징을 살펴보겠습니다
* 해싱을 직접 해볼 수 있는 가장 간단한 방법은 메시지의 비트들을 매우 큰 이진수 하나라고 생각하고, 그 수를 더 작은 숫자로 나누는 방법이 있습니다.
  * 예를 들어 어떤 메시지의 비트가 6457<sub>10</sub>이고 해시 번호가 236인 경우, 해시 값은 6457 % 10 = 85입니다.
  * 실제 해싱은 이보다 더 복잡하지만, 이 예는 해싱의 좋은 맛보기입니다.
* 해싱의 결과는 원래의 바이너리 메시지보다 훨씬 더 짧습니다.
  * 반면에 암호화는 평문과 거의 같은 길이의 암호 텍스트를 생성합니다.
* 해싱은 되돌릴 수 없습니다(irreversible). 즉 dehashing 알고리즘 같은 건 없습니다. 햄버거를 소로 되돌릴 수 없는 것과 같습니다.
  * 복호화를 할 수 있는 암호화와는 다른 점입니다.
* 해싱은 반복할 수 있습니다(repeatable). 서로 다른 두 사람이 동일한 해시 알고리즘을 동일한 비트 문자열에 적용하면 항상 정확히 동일한 해시를 얻게 됩니다.
  * 이건 암호화와 같은 점입니다.
* 오늘날 가장 널리 사용되는 해시 함수는 128비트 해시를 만드는 MD5일 것입니다. 또한 SHA-1, 224, 256, 384, 512 등을 포함한 SHA(Secure HAsh Algorithm) 변형 제품군들도 있습니다.
 하지만 최근 MD5와 SHA-1에서 약점이 발견되었습니다. 따라서 오늘날에는 MD5를 절대 사용해서는 안되며, 강력한 버전의 SHA만 사용해야합니다.

### 3.5.3 Initial Authentication with MS-CHAP
* initiala authentication 방법 중 하나인 MS-CHAP를 살펴보겠습니다. MS-CHAP(Microsoft Challenge Handshake Authentication Protocol)은 Microsoft Windows Server operating system에 사용자가 로그인할 때 널리 쓰이는 방법입니다.
 비밀번호(password)를 반복 사용하며 supplicant와 verifier끼리만 공유하고 있습니다.

Figure 3-12 Microsoft Challenge Handshake Authentication Protocol  

1. On The Supplicant's Machine: Hashing  
(1) 먼저 verifeir(verifier server)는 supplicant's PC로 challenge message를 암호화화(encryption for confidentiality) 없이 그냥 보냅니다.  
(2) **challenge message**는 간한 랜덤 비트 스트링입니다.  
(3) 그럼 supplicant의 PC는 그 challenge message에 자신(applicant)의 password를 덧붙여서 더 긴 비트 스트림을 만든 뒤, 해싱을 한 **response message**를 만듭니다.  
(4) supplicant'의 PC는 이 response message를 서버로 암호화 없이 그냥 보냅니다.  
2. On The Verifier Server  
(5) 그럼 verifier는 그 response message를 테스트하기 위해, 스스로 client가 한 것과 똑같이 response message를 만들어봅니다. (해싱이 반복할 수 있어 가능합니다)  
(6) 만약 verifier가 자체 해싱한 결과가 supplicant의 response message와 같다면, 서버는 인증된 사용자를 로그인 시켜줍니다.  

## 3.6 The Keying Stage
### 3.6.1 Session Keys
* authentication stage 다음에, 두 파트너는 한 개 이상의 대칭 키(symmetric keys for confidentially)를 반드시 교환해야 합니다. 그 키들을 **session keys**라고 합니다. single communication session을 위해서만 쓰이기 때문에 이렇게 부릅니다.
 즉 만약에 두 파트너가 다시 communicate를 시작한다면, 그들은 이전과는 다른 session key를 교환할 것입니다.
* 우리는 기관(organization)에서 널리 쓰이는 keying 방법인 public key encryption for confidentiality와 high cost and short message lengths 두 가지를 살펴보겠습니다.

### 3.6.2 Public Key Encryption for Confidentiality
* 비록 대칭 키 암호화(symmetric key encryption) 기밀성을 위한 암호화를 지배하고 있지만, 그 외 다른 계열의 암호들도 때때로 기밀성을 위해 사용됩니다. 공개 키 암호화(public key encryption)은 비대칭 키 암호화(asymmetric key encryption)이라고도 하며, symmetric session keys와 다른 기밀들을 위한 키 교환에서 사용됩니다.

Two Keys
* 공개 키 암호화에서 각 파티(part)는 개인 키(private key)와 공개 키 (public key) 이렇게 두 개의 키를 가집니다. 공개 키는 누구나 알 수 있으며, 개인 키는 각 파티마다 비밀로 유지해야합니다.
* Figure 3-13은 어떻게 서로 다른 두 종류의 키가 기밀성을 위해 사용되는지 보여줍니다.

Process
* Figure 3-13에서 앨리스는 밥에게 메시지를 안전하게 보내고 싶어합니다. 그래서 앨리스는 메시지의 평문을 밥의 공개 키로 암호화해서 보냅니다. 그리고 밥은 암호문을 그만의 개인 키로 복호화해서 읽습니다.
  * 즉 발신자는 수신자의 공개 키를 사용해 암호화하고, 수신자는 수신자의 개인 키를 이용해 복호화합니다.
  * 따라서 누구든지 공개 키를 사용하여 메시지를 암호화한 뒤 전송할 수 있으며, 사전 키 교환이 필요하지 않습니다.
* **우리는 단순히 "the public key", "the private key"라고 말할 수 없다는 점을 유의해야합니다. 왜냐하면 양쪽 모두 public key와 private key를 각자 가지고 있기 때문입니다.

Figure 3-13 Public Key Encryption for Confidentiality

Padlock and Key Analogy (자물쇠와 열쇠 비유)
* 공개 키 암호화는 자물쇠와 열쇠에 비유할 수 있습니다. 밥의 공개 키는 자물쇠이고 밥의 개인 키는 열쇠입니다. 밥은 자물쇠를 연 상태로 앨리스에게 나눠주고, 앨리스는 그 자물쇠로 상자를 잠그고 밥에게 보내면, 누가 가로채더라도 밥만이 그 상자를 열 수 있는 것입니다.
* 생략

High Cost and Short Mesage Lneghts
* 대칭 키 암호화는 빠르고, 저렴합니다. 하지만 session keys의 분산을 필요로 합니다.
* 공개 키 암호화는 keys의 분산을 필요로 하지 않고, 사전 keying을 필요로 하지 않습니다. 하지만 느리고, 비싸고, 시간이 오래 걸립니다.
* 그 결과, 암호학에서 공개 키 암호화는 매우 짧은 메시지를 암호화할 때만 사용합니다.

RSA and ECC
* 널리 쓰이는 공개 키 암호화 두 가지가 있습니다.
* 하나는 RSA 암호화로, 공개 키 암호화를 지배하고 있습니다.
* 다른 하나는 ECC(Elliptic Curve Cryptography)로, 더 효율적이라서 사용률이 증가하고 있습니다.

Key length
* 공개 키 암호화는 대칭 키 암호화와 달리 공개 키-개인 키 쌍이 거의 변경되지 않습니다. 따라서 보안에 더 유의해야 합니다.
* RSA의 경우 공개 키의 길이는 최소 1024비트이며, ECC는 512비트입니다. 이렇게 키 길이가 길면 공개 키 암호화 속도가 느려지므로 이래서 구현 비용이 많이 든다는 것입니다.

### 3.6.3 Symmetric Key Keying Using Public Key Encryption
* 공개 키 암호화와 대칭 키 암호화는 라이벌처럼 보일 수 있지만, 실제로는 상호 보완적인 관계입니다.
* 예를 들어 Figure 3-14와 같이 공개 키 암호화는 대칭 세션 키를 안전하게 전송하는 걸 도와줍니다.

Figure 3-14 Public Key Keying for Symmetric Session Keys

### 3.6.4 Symmetric Key Keying Using Diffie-Hellman Key Agreement
* 또 다른 인기있는 keying 방법으로는 Diffie-Hellman key agreement가 있습니다. 공개 키 암호화보다 더 빠릅니다.
* Figure 3-15에서 어떻게 Diffie-Helman key agreement가 keying을 수행하는지 설명하고 있습니다.
* 생략

Figure 3-15 Keying Using Diffie-Hellman Key Agreement

### 3.7 Message-By-Message Authentication
* 다음에 언젠가 계속