---
title:  "[정보보호]3.Cryptography"
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
### 3.1.1. Encryption for Confidentiality
3.1: Cryptography
* 암호화(Cryptography)는 교환되거나 저장된 메시지를 보호하기 위해 수학적 연산을 사용하는 것입니다.
* 기밀성(Confidentiality)은 당신의 통신을 누군가가 가로채더라도 읽을 수 없는 특성을 의미합니다.

암호의 출현
* 이오니아(그리스 지방) 왕 히스티아이오스 페르시아 왕 아리우스

보안 목표 리마인드 (Remind Security Goals) (3.1: Cryptography)
* 기밀성은 하나의 암호화 보호일 뿐입니다 (Confidentiality is only one cryptographic protection)
* 무결성은 메시지를 변경할 수 없게 하고 변경된 경우 그 변경을 탐지할 수 있는 것을 의미합니다 (Integrity means that the message cannot be changed or, if it is changed, that this change will be detected)
* 가용성 또는 인증은 자신의 신원을 다른 사람에게 증명하여 더 신뢰할 수 있도록 하는 것을 의미합니다 (Availability or Authentication means proving one’s identity to another so they can trust you more)
* 암호화의 CIA라고 알려져있습니다
  * 미국의 그 CIA가 아닙니다

보안 위협 리마인드 (Remind Security Threat)
* 인터셉션은 기밀성에 대한 공격입니다 (Interception: attack on confidnetiality)
* 인터럽션은 가용성에 대한 공격입니다 (Interruption: attack on availability)
* 모디피케이션은 무결성에 대한 공격입니다 (Modification: attack on intergrity)
* 패브릭케이션은 인증에 대한 공격입니다 (Fabrication: attack on authenticity)
* 강의노트 그림 참고

3.1: Cryptography
* 기밀성을 위한 암호화에는 암호화 및 복호화를 위한 암호(수학적 방법)이 필요합니다 (Encryption for confidentiality needs a cipher(mathematical method) to encrypt and decrypt)
  * **암호**는 비밀로 하지 않습니다
* 암호를 사용하는 두 당사자는 비밀 키(secret key) 또는 키(key)를 알아야합니다.
  * 키는 단지 비트(1과 0)들의 긴 스트림입니다
  * **키**는 비밀로 유지되어야 합니다. 
* 암호화 분석가가 키를 해독하려고 시도합니다. (Cryptanalysts attempt to crack(find) the key)

### 3.1.2. Terminology
Crypto Term
* 암호화 or 암호학(Cryptography or Cryptology)
  * (적이라고 할 수 있는) 제 3자의 존재에 대비해 안전한 의사소통을 위한 기술의 실행과 연구
* 암호 분석학(Cryptanalysis)
  * 키에 접근하지 않고 암호화된 정보의 의미를 알아내기 위한 방법의 연구
* 암호화(Cryptology)
  * 위의 두 가지 Cryptography와 Cryptanalysis의 조합
* 암호학자(Cryptographer)
  * 암호화 시스템 및 저술을 사용, 연구 또는 개발하는 사람
* 암호화 분석가(Cryptanalysts)
  * 비밀 코딩 시스템을 분석및 복호화하고 해독하고 군사, 정치, 법률 집행 기관 및 조직에 대한 메시지를 해독

3.1: Symmetric Key Encryption for Confidentiality (Figure 3-1)
* 강의노트 그림 참고

### 3.1.3. The Simple Cipher
3.1: Example Symmetric Key Cipher (Figure 3-2)
* 강의노트 그림 참고

Caesar's Cipher (BC 100-44)
* 영어 알파벳 A..Z를 사용하여 작성된 메시지를 암호화합니다
* 평문 메시지를 암호화하기 위해 각 문자는 k번째 뒤에 있는 알파벳으로 대체됩니다. (단, k는 0에서 25 사이의 정수)
* 암호 메시지를 복호화하기 위해 각 문자는 26-k번째 뒤에 있는 문자로 대체됩니다.
* 예) A->C +2 암호화, C->A +26-2=+24 복호화

Lysander Cipher
* 스키테일(Scytale): 인류 최초의 암호 통신 방법
* 스파르타 + 페르시아 동맹 -> 아테네 공격

### 3.1.4. Cryptanalysis

### 3.1.5. Substitution and Transposition Ciphers, 3.1.6. Substitution Ciphers, 3.1.7. Transposition Ciphers, 3.1.8. Real-world Encryption
3.1: Types of Ciphers
* 대체 암호(Substitution Ciphers)
  * 한 문자(또는 비트)를 다른 문자로 각각 대체하는 방식
  * Figure 3-2에서 본 암호가 대체 암호입니다.
* 전치 암호(Transposition Ciphers)
  * 각 문자(또는 비트)를 대체하는 게 아니라 순서를 변경하는 방식
* 대부분의 실제 암호는 대체 암호와 전치 암호 방식을 모두 사용합니다

3.1: Transposition Cipher (Figure 3-3)
* 강의노트 그림 참고

### 3.1.9. Ciphers and Codes
3.1: Ciphers versus Codes
*	암호(Ciphers)는 바이너리로 표현된 모든 메시지를 암호화할 수 있습니다
    * 이러한 유연성과 컴퓨팅 속도는 오늘날 암호화를 위해 이 암호가 지배적입니다.
* 코드는 더 전문적입니다
  * 코드는 다른 한 가지를 대체합니다
  * 일반적으로 다르고 다양한 세계의 단어입니다
* 코드는 인간에게 편하며, 암호화된 메시지 안에 포함될 수도 있습니다.

Code - 난수표/난수방송?
* 강의노트 그림 참고

3.1: Japaneses Naval Operational Code JN-25 (Simpleified Figure 3-4)
* 강의노트 그림 참고

### 3.1.10. Symmetric Key Encryption
**Symmetric Key Encryption (대칭 키 암호화)**
* 암호화 및 복호화에 단일 키(single key)가 사용됩니다
* 기밀성을 위한 거의 모든 암호화는 대칭 키 암호화를 사용합니다
  * DES, AES, RC4/5

Key length
* 철저한 검색
  * 브루트포스 공격 
* N bits 키이면 2<sup>n</sup> 경우의 수가 있고
  * 2<sup>n</sup>/2 = 2<sup>n-1</sup>이면 크랙 가능하다고 알려져있습니다
* 키의 길이가 1비트 늘어나면 크랙하는데 걸리는 시간을 2배로 늘릴 수 있습니다
* 오늘날 길이가 100비트 이상인 대칭 키는 강력한 대칭 키로 간주됩니다

### 3.1.11. Human Issues in Cryptography
Human Issues
* 암호화는 완벽하지 않기 때문에 알아서 자동으로 보호된다고 생각하면 안 됩니다
  * Japan Navy
  * Enigma

U-505 & Enigma
* 사진

Alan Turing
* 블레츠리 파크(1939) 영국
  * Alan Turing Enigma 해독 (1943) 콜로서스
* 신문
* 위키피디아
  * 당시 동성애는 용납할 수 없는 부도덕한 범죄였다. 튜링은 성기능을 억제하는 호르몬 치료를 강요 받는다. 에스트로겐의 지속적인 주입은 중추신경계 손상과 함께 젖가슴이 부풀어 오르는 변형을 일으켰다. 모멸감에 고통스러워하던 튜링, 결국 1954년 6월 7일 청산가리를 묻힌 사과를 베어 물고 스스로 목숨을 끊는다. 이때 나이 42세였다. 1966년 미국계산기학회는 컴퓨터 분야의 노벨상으로 불리는 '튜링상'을 제정해 그의 업적을 기리고 있다. 애플컴퓨터의 로고도 튜링의 독사과에서 유래했다는 얘기가 있다

3.1: Key Length and Exhaustive Search Time (Figure 3-5)
* 강의노트 그림 참고
* 참고: 공개 키(public key)/개인 키(private key) 쌍은 대게 강력하다고 알려져있는 대칭 키보다도 훨씬 길어야 합니다. 왜냐하면 개인 키는 자주 변경할 수 없으므로, 크랙된다면 참담한 결과가 발생할 수 있기 때문입니다.
* 공개 키(public keys)와 개인 키(private keys)는 최소 512~1,024비트여야 합니다.  

## 3.2 Symettric Key Encrption Ciphers
3.2: Major Symmetric Key Encryption Ciphers (Figure 3-6)
* 강의노트 그림 참고

### 3.2.1. RC4
RC4
* 가장 널리 사용되는 소프트웨어 스트림 암호이고 대중적인 프로토콜에 사용되기도 합니다
* RC4는 소프트웨어의 단순함과 속도가 뛰어나지만, 새로운 시스템에서의 사용에 반대하는 단점이 있습니다.
* 출력 키스트림(output keystream)의 시작 부분이 삭제되지 않거나, 무작위가 아니거나, 관련 키가 사용될 때 특히 취약합니다. RC4를 사용하는 일부 방법은 WEP와 같은 매우 안전하지 않은 암호 시스템으로 이어질 수 있습니다.
  * RC4는 1987년 RSA Security의 Ron Rives에 의해 설계되었습니다. 

Advantage
* 빠르고 효율적인 메모리 사용
* 선택적인 키 사이즈
  * 수출 제한에 의해 빈약한 WEP
강의노트 그림 참고

### 3.2.2. The Data Encryption Standard (DES)
DES
* 예전에 주로 사용되었던 전자 데이터 암호화를 위한 알고리즘
* 1970년대 초 IBM에서 개발되었으며, Horst Feistel의 초기 디자인을 기반으로 개발되었습니다. 
  * 이 알고리즘은 민감하고 분류되지 않는 전자 정부 데이터의 보호를 위한 후보를 제안하라는 NBS(National Bureau of Standards)의 공모전에서 제출된 것입니다.
* 1976년 국가안보국(National Security Agency, NSA)과 협의한 후, NBS는 결국 약간 수정된 버전을 선택했으며, 1977년 미국의 공식 연방정보처리표준(Federal Information Processing Standard, FIPS)으로 출판되었습니다.

3.1: DES Block Encryption (Figure 3-7)
* 강의노트 그림 참고
* DES 암호는 메시지를 한 번에 64비트 씩 암호화 합니다. 코드북 모드(codebook mode)에서 두 개의 입력을 필요로 합니다.

Block Cipher Mode
* 강의노트 그림 참고
* Cipher Block Chaining (CBC) mode encryption

DES
* 강의노트 그림 참고
* DES 알고리즘의 일반적 모형
  * 평문: 64bit
  * 키: 56bit + 8bit(패리티)
* 처리 단계
  * 초기 순열 단계
  * 16라운드 반복
  * 좌우 교환 단계
  * 역 초기 순열 단계
* DES의 기본 구조 (single round)
  * 강의노트 그림 참고
DES S-box
* 강의노트 그림 참고
DES P-box
* 강의노트 그림 참고

### 3.2.3. Triple DES (3DES)
DES의 변형 (Variants of DES)
* DES는 충분히 안전하지 않습니다.
* 한때 큰 키 공간(key space)이었던 2<sup>56</sup>이 이젠 너무 작습니다.
* 그 대안으로 2001년 NIST는 Advanced Encryption Standard (AES)를 발표했습니다.
* 그러나 상거래 및 금융 분야의 사용자들은 DES를 포기할 준비가 되어있지 않습니다.
* 해결 방편으로 여러 keys와 함께 여러 DES를 사용합니다.

Double-DES (2-DES)
* 두 가지 키가 있는 2-DES
* Encryption: C = E<sub>K2</sub>(E<sub>K1</sub>(P))
* Decryption: P = D<sub>K1</sub>(D<sub>K2</sub>(C))
* Key length: 56 x 2 = 112 bits
* This should have thwarted brute-force attacks?
  * Wrong!

Double-DES Attack
* 2-DES:
  * C = E<sub>K2</sub>(E<sub>K1</sub>(P))
  * D<sub>K2</sub>(C) = D<sub>K2</sub>(E<sub>K2</sub>(E<sub>K1</sub>(P)))
  * D<sub>K2</sub>(C) = (E<sub>K1</sub>(P))
* 알려진 (P, C) 쌍이 주어지면 다음과 같이 공격합니다:
  * 2<sup>56</sup>키 K1으로 P를 암호화 한다
  * 2<sup>56</sup>키 K2으로 C를 복호화 한다
  * 만약 E<sub>K1</sub>(P) = D<sub>K2</sub>(C)라면, 다른 (P', C') 쌍으로 시도한다
  * 만약 먹힌다면, 높은 확률로 (K1', K2') = (K1, K2)이다
  * O(2<sup>56</sup>)의 연산을 수행한다. 1-DES를 공격하는 것에 지나지 않습니다.
* 강의노트 그림 참고
  * 즉 2<sup>56</sup> table이 2개인 효과일 뿐이다
    * 2<sup>56</sup> x 2 = 2<sup>57</sup>

Triple-DES
* Triple Data Encryption Algorithm (TDEA or Triple DEA) 블록 암호(block cipher)
  * 데이터 암호화 표준 (Data Encryption Standard, DES) 암호 알고리즘을 각 데이터 블록에 세 번 적용합니다
* 원래 DES 암호의 키 크기인 56 비트는 일반적으로 알고리즘이 설계되었을 때는 충분했습니다.
  * 그러나 컴퓨테이셔널 파워가 증가함에따라 무차별 암호 대입 공격(brute-force attacks feasible)이 가능해졌습니다.
* Triple DES는 완전히 새로운 블록 암호 알고리즘을 설계할 필요 없이 이러한 공격으로부터 보호하기 위해 DES의 키 크기를 늘리는 비교적 간단한 방법을 제공합니다.

* 일반적인 T-DES:  E<sub>K1</sub>(D<sub>K2</sub>(E<sub>K1</sub>(P)))
* 2개의 키를 사용하여 Encrypt-Decrypt-Encrypt (EDE)로 암호화하는 이유 (3개의 키를 사용하여 EEE로 하지 않는 이유)
  * 키의 길이는 112비트면 충분히 안전함로 2<sup>168</sup>까지 필요없기 때문에
    * 연산 속도, 키 관리 문제 부담에서 벗어남
  * Single DES와의 Backward compatible를 위해서
    * 만약 K1=K2=K라면  E<sub>K1</sub>(D<sub>K2</sub>(E<sub>K1</sub>(P))) = E<sub>K</sub>(D<sub>K</sub>(E<sub>K</sub>(P))) = E<sub>k</sub>(P)
* 오늘날 3DES는 널리 사용되고 있으나, AES의 등장으로 3DES는 시간이 지날수록 사라져 갈 것으로 예상됨

### 3.2.4. Advanced Encryption Standard (AES)
AES
* 전자 데이터의 암호화를 위한 사양입니다.
  * 미국 정부에 의해 채택되었으며 현재 전 세계적으로 사용되고 있습니다.
  * AES에서 설명하는 알고리즘은 대칭 키 알고리즘(symmetric-key algorithm)입니다. 즉, 데이터를 암호화하고 복호화하는 데 동일한 키가 사용됩니다.
* 미국에서 AES는 NIST(National Institute of Standards and Technology)에서 US FIPS PUB 197 (FIPS 197)로서 발표되었습니다. 이는 2001년 11월 26일에 15개의 경쟁 디자인이 제시되고 평가되어 가장 적합한 것으로 선정되기 전에 5 년간의 표준화 과정을 거친 후 발표된 것입니다.
  * 2002년 5월 26일 상무부 장관(Secretary of Commerce)의 승인을 받아 연방 정부 표준으로 발효되었습니다.
  * 다양한 암호화 패키지에서 사용할 수 있습니다. AES는 NSA(National Security Agency)에서 일급 비밀 정보(top secret information)에 대해 승인한 최초의 공개 접근 및 개방 암호(first publicly accessible and open cipher)입니다.

* 원래 Rijndael이라고 불리는 이 암호는 벨기에 암호학자(cryptographers) Joan Daemen과 Vincent Rijmen에 의해 개발되어 AES 선택 프로세스(selection process)에 제출되었습니다.
* Rijndael(네덜란드어 발음: [ˈrɛindaːl])이라는 이름은 두 발명가의 이름에 대한 연극입니다.
* 엄밀히 말하자면,
  * AES는 표준의 이름이며 설명 된 알고리즘은 Rijndael의 (제한된) 변형입니다.
  * 그러나 실제로 알고리즘을 "AES"라고도 합니다.
  * AES 후보
    * CAST‑256, CRYPTON, DEAL, DFC, E2, FROG, HPC, LOKI97, MAGENTA, MARS, RC6, Rijndael, SAFER+, Serpent 및 Twofish

Advantage
* 선택 가능한 3개의 키 길이 ( 128 / 192 / 256 )
* 임베디드 시스템에도 효과적
* RAM 요구 사양도 양호

AES Cipher - Overview
* 강의노트 그림 참고

AES Encryption Process - Round F: S - box, Shift Row, Mix column, Add round key
* 강의노트 그림 참고

### ~~~3.2.5. Other Symmetric Key Encryption Ciphers~~~

<!--3-2강-->
## 3.3. Cryptographic System Standards
### 3.3.1. Cryptographic System
Cryptographic System Stages

### 3.3.2. Initial Handshaking Stages
Cryptographic System Stages (Figure 3-8)

그림

### 3.3.3. Ongoing Communication
Cryptographic System
