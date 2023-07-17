---
title: "EVA: An Encrypted Vector Arithmetic Language and Compiler for Efficient Homomorphic Computation"
date: 2023-07-14
excerpt: "Homomorphic Computation paper (CKKS)"
toc: true
toc_sticky: true
use_math: true

header:
  teaser: /assets/images/encryption.jpg

categories:
  - 학부연구생
tags:
  - Homomorphic Encryption
  - paper review
last_modified_at: 2023-07-14
---

# EVA: An Encrypted Vector Arithmetic Language and Compiler for Efficient Homomorphic Computation

[Paper Link](https://arxiv.org/abs/1912.11951)

## 2.2. Challenges in Using FHE

### Depth of Computation

Ciphertext의 computation은 homomorphic addition 연산의 수에 비례하여 초기에 작은 Error가 선형적으로 증가하며, 평가 회로(evaluation circult)의 multiplication depth에 지수적으로 증가합니다.   
Error가 지나치게 커지면 암호문은 손상되어 올바른 비밀 키로도 decryption 할 수 없게 됩니다.   
이 한계는 암호화 매개 변수 $Q$의 크기에 의해 결정됩니다.  
따라서 회로의 낮은 depth를 위해 회로를 최적화해야 효율적인 homomorphic evaluation를 지원할 수 있습니다.

### Relinearization

각 ciphertext는 2 or more polynomial으로 구성됩니다(최초 암호화된 암호문은 2 polynomial로만 구성됩니다).  
$k$ and $l$ polynomial으로 이루어진 두 암호문의 곱셈은 $k+l+1$ polynomial으로 이루어진 암호문을 생성합니다.  
다항식의 수가 무한정 증가하는 것을 방지하기 위해, 다항식의 수를 다시 2개로 줄이는 작업인 'relinearization'이 수행됩니다.  
각각의 다항식 수에서 2로의 relinearization은 별도의 공개키가 필요합니다.  
Relinearization은 비용이 많이 들며, 그들의 최적 배치는 NP-hard 문제입니다.

### CKKS and Approximate Fixed-Point

CKKS에서의 error는 두 가지 주요한 원인이 있습니다.

1. 값의 인코딩으로 인한 손실성(lossy) error
2. homomorphic operation마다 추가되는 noise가 메시지와 혼합되는 error

이를 해결하기 위해, CKKS는 각 암호문에 비암호화된 scaling factor를 연관시켜 fixed-point 표현(representation)을 채택합니다.  
충분히 큰 scaling factor를 사용하면 오차를 숨길 수 있습니다.

<br>

CKKS는 암호문의 fixed-point 표현을 축소하는 작업인 'rescaling'이라는 연산을 제공합니다.  
상대적으로 낮은 스케일인 $2^{10}$와 곱해진 $0.25$의 인코딩이 포함된 암호문 $x$를 고려해보겠습니다.  
$x^2$는 스케일 $2^{20}$과 곱해진 $0.0625$를 인코딩합니다.  
추가적인 지수는 $Q$의 적당한 값을 빠르게 초과하게 되며, 이는 비현실적으로 큰 암호화 매개 변수를 선택해야 함을 의미합니다.  
$2^{10}$으로 두 번째 지수를 rescaling하면 고정 소수점 표현이 값 $2^{10}$의 스케일로 잘립니다.

<br>

또 다른 complication(복잡성)은 rescaling 이후의 암호문이 근본적으로 다른 암호화 매개 변수로 암호화된다는 점에서 발생합니다.  
어떤 binary homomorphic operation을 적용하기 위해서는 두 암호문이 동일한 level(즉, 동일한 $Q$)에 있어야 합니다.  
또한, 덧셈과 뺄셈은 fixed-point arithmetic(산술)의 특성으로 인해 암호문이 동일한 스케일로 인코딩되어야 합니다.  
CKKS는 메시지를 스케일링하지 않고 암호문의 레벨을 낮추기 위한 modulus switching operation을 지원합니다.  
(그러나 레벨과 스케일을 맞추기 위해 적절한 rescaling과 modulus switching을 삽입하는 것은 전문가들에게도 상당히 어려운 과정입니다.)

<br>

가장 효율적인 CKKS 구현에서 (so called RNS-variants [[1]](https://eprint.iacr.org/2018/931.pdf)), truncation(절단)은 $Q$의 prime factor로 암호화된 값을 나누어서 수행됩니다.  
이러한 소수 인수에는 고정된 순서가 있으며, 따라서 주어진 레벨(즉, $Q$에 남은 prime factor의 개수)에서 rescaling에 사용할 수 있는 유효한 divisor는 하나뿐입니다.  
이는 너무 일찍 rescaling을 수행하면 fixed-point 표현이 너무 작아져 근사 error가 메시지를 파괴할 수 있다는 점에서 선택적으로 rescaling 지점을 선택하는 것을 복잡하게 만듭니다.

| Type | Description |
| :---- | :---- |
| **Cipher** | An encrypted vector of fixed-point values |
| **Vector** | A vector of 64-bit floating point values |
| **Scalar** | A 64-bit floating point value |
| **Integer** | A 32-bit signed integer |

