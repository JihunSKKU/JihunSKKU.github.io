---
title: "Homomorphic Encryption Project Diary"
date: 2023-07-01
excerpt: "동형암호 과제 진행사항 기록장"
toc: true
toc_sticky: true
use_math: true

header:
  teaser: /assets/images/encryption.jpg

categories:
  - 학부연구생
tags:
  - homomorphic encryption
  - diary

last_modified_at: 2023-07-14
---

# SecLab에서 진행하는 HE 과제 기록장

## 매주 목요일 자체 스터디 계획

1. 07/13 - Starting with lattigo. Basic understanding of the lattigo package and a simple example tutorial  
    [Lattigo 공식문서](https://homomorphicencryption.org/wp-content/uploads/2020/12/wahc20_demo_christian.pdf)
2. 07/20 - Implementation of statistical operations (addition and substitution) using lattigo
3. 07/27 - Implementation of statistical operations (multiplication and average) using lattigo
4. 08/03 - Implementation of statistical operations (rotation and deviation) using lattigo
5. 08/10, 08/17 - Implementation of column operations using lattigo
6. 08/24, 08/31 - Implementation of Logistic regression using lattigo
7. 09/07 - Implementation of Linear regression using lattigo
8. 09/14, 09/21 - Implementation of K-means clustering using lattigo
9. 09/28 - Implementation of SVM using lattigo

## 07/03

### Homomorphic Encryption 개념 공부

$E(m_1) + E(m_2) = E(m_1 + m_2)$  
$E(m_1) \times E(m_2) = E(m_1 \times m_2)$  
여기서 AND, XOR, 상수곱 등의 모든 논리 연산을 보존하는 것을 완전동형암호 (Fully Homomorphic Encryption, FHE)라 한다.

- 대칭키 암호화 방식 &Rightarrow; 암호화, 복호화 키가 동일
    - 속도가 빠르다.
    - 키를 공유해야 함, 사람이 많을수록 키관리가 힘들다.

- 공개키 암호화 방식 &Rightarrow; 암호화, 복호화 키가 서로 다름
    - 키분배가 필요없다, 기밀성 / 인증 / 부인방지 기능 등을 제공한다.
    - 대칭키 암호화 방식에 비해 속도가 느리다.
    
### RSA 암호

### Privacy Homomorphism [RAD78] (1978)

최초 제안 암호기법이다.

## 07/04

- 네이버 과제 단톡방 개설
- server ID 전달 및 PW 변경
- server에 GO 환경 구축


## 07/06

### cyclotomic field (원분체) 공부

quotient field ($Q$)에서 $1$의 거듭제곱근을 첨가하여 얻은 field이다.

### Bootstrapping 공부

암호문을 재암호화하여 평문을 다시 암호화함으로써 보안한 상태에서 계산을 계속할 수 있는 방법이다.
- homomorphic encryption은 계산의 depth가 증가할수록 오차가 증가하고, 결국 평문을 완전히 복원하지 못할 수도 있다. bootstrapping은 이러한 문제를 해결하기 위해 만들어졌다.
- 암호화된 데이터 -> 암호화 및 복호화 -> 암호문 재암호화
- 암호문의 오차 감소, 연산 cost 증가, 추가적인 암호화 & 복호화 작업 필요


## 07/10

- 연구원 님 포함된 단톡방 개설
- 노션 페이지 개설 및 공유


## 07/12

- 연구원님과 킥오프 미팅
    - 8월 말까지 SCI급 논문 Accept 목표
        - 기존에 작성된 논문을 바탕으로 작성할 예정 : [UniHENN Paper](https://www.overleaf.com/project/63ff24397b3388d69b340ca8)
        - Test 추가 필요 (15p - 1000개의 data)
        - 알고리즘 최적화 필요
        - Experiments의 Table1에서 Flatten 제거
        - TenSEAL보다 더 빠르다는 점에서 novelty 강조
        - Dataset의 크기가 좀 작은 MNIST 등에서만 돌아가는 것을 확인했는데, CIFAR-10과 같은 크기가 큰 dataset에서도 돌아가는지 확인하면 좋을 것 같다. 이는 시간이 부족할 수 있기에 일단 제출 후 피드백이 오기 전까지 하는 방법도 가능
        - 12p에서 Conv2d의 # of Mult.가 1개로 줄어든다면 매우 좋음! (Multiplication의 cost가 매우 높기 때문)

### cyclotomic polynomial에 대한 추가 공부


## 07/13

- 동형암호 스터디 진행
- 강의실 예약 완료
    - 매주 목요일 10:30 ~ 12:00 자체 스터디
    - 매주 목요일 14:00 ~ 19:00 연구원님 세미나 및 회의 진행
- SEAL-Python run을 위한 환경 구축 (승호님의 도움을 받아 겨우..ㅎ)

### ReLU 함수 고안

$$ReLU(x) = max(0, x) = \frac{x + |x|}{2}$$  
여기서 $|x|$를 addition과 multiplication으로 나타낼 수만 있다면..?  
그런데 이는 비선형 함수라서 애초에 두 operation으로 나타내기가 어려울 것 같다는 결론.


## 07/14

- GitHub repository 생성 및 공유
- 정보보호 서약 서명

### [EVA paper review](https://jihunskku.github.io/%ED%95%99%EB%B6%80%EC%97%B0%EA%B5%AC%EC%83%9D/EVA-An-Encrypted-Vector-Arithmetic-Language-and-Compiler-for-Efficient-Homomorphic-Computation/)

## 차후 해야할 일

- HELayer, TenSEAL, PyCrCNN 사용해보기
    - HELayers : 개발과제에서 벤치마킹 대상
    - TenSEAL, PyCrCNN : IEEE ACCESS에서 비교대상


## 07/24

- 기업체와 킥오프 미팅 (16:30)



## 최현민 연구원님의 세미나

### Day 1

- 동형암호 스킴에 대한 전반적인 소개
- Lattigo를 기반으로 한 파라미터 설명
- Lattigo예제를 기반으로 한 알고리즘 설명

### Day 2

- IEEE ACCESS 논문 기반 CNN 알고리즘 이론 설명
- CNN 알고리즘 코드 관련 설명
- 예제를 통한 이해

### Day 3

- CNN 알고리즘 코드 이해 심화
- 기존 CNN 알고리즘에 대한 개선점 논의
- K-means clustering, Linear SVM 구현을 위한 노하우 공개