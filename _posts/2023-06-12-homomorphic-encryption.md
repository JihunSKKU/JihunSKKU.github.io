---
title: "Homomorphic Encryption (동형 암호)"
date: 2023-07-03
excerpt: "동형암호 기초 지식들"
toc: true
toc_sticky: true
header:
  teaser: /assets/images/notebook.jpg

categories:
  - 학부연구생
tags:
  - homomorphic-encryption
last_modified_at: 2023-07-03
---

# 동형암호란? (Homomorphic Encryption)

## Homomorphic Encryption 종류

1. 유한동형암호 (Somewhat Homomorphic Encryption, SHE)

암호문에 난수화된 에러를 포함하는 것으로써, 다수의 연산후에는 에러가 증폭되어 그 크기가 일정 수준을 넘어서면 정확한 복호화가 불가능한 한계가 있다.

2. 완전동형암호 (Fully Homomorphic Encryption, FHE)

Gentry는 SHE에 재부팅(bootstrapping)이라는 과정을 통해 대수연산(Addition, Multiplication)이 이론산 무한번 가능하게 만들었으며, 이를 FHE라 부른다.

## Homomorphic Encryption 분류

1. 1세대

2009년 Gentry에 의해 처음 제안된 동형암호를 1세대로 구분한다.

2. 2세대

2011년 Brakerski-Gentry-Vaikuntanathan에 의해 발표된 논문에서는, 곱셈시 생기는 잡음의 크기를 줄이는 기법이 제안되어, 재부팅없이 가능한 곱셈 횟수를 암호문 길이에 대해 기하급수적으로 늘릴 수 있게 되었다. 소위 모듈러스, 혹은 키 교환(modulus/key-switching) 이라 부르는 과정이며 이러한 과정을 도입한 스킴들을 2세대 동형암호라 부른다.

- The Brakerski-Gentry-Vaikuntanathan (BGV, 2011) scheme,\[[2](https://eprint.iacr.org/2011/277)\] (Brakerski-Vaikuntanathan 의 기법에 기반한 설계);\[[3](https://eprint.iacr.org/2011/344)\]

- The NTRU-based scheme by Lopez-Alt, Tromer, and Vaikuntanathan (LTV, 2012);\[[4](https://eprint.iacr.org/2013/094)\]

- The Brakerski/Fan-Vercauteren (BFV, 2012) scheme,\[[5](https://eprint.iacr.org/2012/144)\] (Brakerski 의 스케일보존 암호시스템에 기반한 설계);\[[6](https://eprint.iacr.org/2012/078)\]

- The NTRU-based scheme by Bos, Lauter, Loftus, and Naehrig (BLLN, 2013),\[[7](https://eprint.iacr.org/2013/075)\] (LTV 스킴과 Brakerski의 스케일보존 암호시스템에 기반한 설계);\[[6](https://eprint.iacr.org/2012/078)\]

3. 3세대

2013년 Gentry-Sahai-Water 에 의해 발표된 논문에서는 이 곱셈과정의 잡음을 한층 더 줄이고 동형곱셈시 비용이 많이 드는 재선형화(relinearization) 과정을 없애는 기술을 소개하였다. 이를 활용하는 동형암호를 3세대 동형암호라고 부르는데, 특히 평문을 1 비트로 제한하는 대신 매우 빠른 재부팅을 가능하게 한 Ducas-Micciancio14의 FHEW스킴과 Chillotti-Gama-Georgieva-Izabachene16의 TFHE스킴이 이에 속한다.

4. 4세대

2016년 Cheon-Kim-Kim-Song\[[8](https://link.springer.com/chapter/10.1007/978-3-319-70694-8_15)\] 은 덧셈과 곱셈 외에 반올림이라는 세 번째 연산이 암호화상태에서 가능한 혜안(HEaaN)이라는 동형암호를 발표하였다. HEAAN의 최초 버전은 깃허브에 2016년 5월 15일 공개되었으며\[[9](https://github.com/snucrypto/HEAAN)\] 나중에 부트스트래핑 알고리즘을 갖춘 HEAAN 신버전이 출시되었다.\[[10](https://eprint.iacr.org/2018/153)\] 현재 최신 버전은 버전 2.1이다.

기존의 동형암호도 반올림연산을 수행할 수는 있으나 재부팅에 준하는 매우 복잡한 연산을 수행하여야 하는 반면, 혜안 스킴에서는 이를 덧셈 수준으로 빠르게 처리할 수 있어 산술연산이 대폭 개선되었다. 실제로 비트당 30분이 걸리던 재부팅연산이 2019년에는 0.5ms가 걸리게 되어 300만배의 개선을 이루었고, 이는 매년 8배의 고속화에 해당하는데 이중 최근 3년간의 개선은 혜안 스킴에 힘입은 바가 크다. 이에 따라 기계학습 등 근사연산을 활용하는 응용분야의 상용화가 가능해지게 되었고, 이를 4세대 동형암호로 부른다.

# Reference

1. 위키백과, [동형암호](https://ko.wikipedia.org/wiki/%EB%8F%99%ED%98%95%EC%95%94%ED%98%B8)
2. Z. Brakerski, C. Gentry, and V. Vaikuntanathan. [Fully Homomorphic Encryption without Bootstrapping](https://eprint.iacr.org/2011/277), In ITCS 2012
3. Z. Brakerski and V. Vaikuntanathan. [Efficient Fully Homomorphic Encryption from (Standard)](https://eprint.iacr.org/2011/344) LWE. In FOCS 2011 (IEEE)
4. A. Lopez-Alt, E. Tromer, and V. Vaikuntanathan. [On-the-Fly Multiparty Computation on the Cloud via Multikey Fully Homomorphic Encryption](https://eprint.iacr.org/2013/094). In STOC 2012 (ACM)
5. Fan, Junfeng; Vercauteren, Frederik (2012). [“Somewhat Practical Fully Homomorphic Encryption”](https://eprint.iacr.org/2012/144).
6. Z. Brakerski. [Fully Homomorphic Encryption without Modulus Switching from Classical GapSVP](https://eprint.iacr.org/2012/078), In CRYPTO 2012 (Springer)
7. J. Bos, K. Lauter, J. Loftus, and M. Naehrig. [Improved Security for a Ring-Based Fully Homomorphic Encryption Scheme](https://eprint.iacr.org/2013/075). In IMACC 2013 (Springer)
8. Cheon, Jung Hee; Kim, Andrey; Kim, Miran; Song, Yongsoo (2017). 〈Homomorphic encryption for arithmetic of approximate numbers〉. 《Takagi T., Peyrin T. (eds) Advances in Cryptology – ASIACRYPT 2017》. ASIACRYPT 2017. Springer, Cham. 409–437쪽. [doi:10.1007/978-3-319-70694-8_15](https://link.springer.com/chapter/10.1007/978-3-319-70694-8_15).
9. Andrey Kim; Kyoohyung Han; Miran Kim; Yongsoo Song. “[An approximate HE library HEAAN](https://github.com/snucrypto/HEAAN)”.
10. Jung Hee Cheon, Kyoohyung Han, Andrey Kim, Miran Kim and Yongsoo Song. [Bootstrapping for Approximate Homomorphic Encryption](https://eprint.iacr.org/2018/153). In EUROCRYPT 2018(springer).

[참고자료 1](https://koreascience.kr/article/JAKO201326952133126.pdf)

[RSA 암호](https://ko.wikipedia.org/wiki/RSA_%EC%95%94%ED%98%B8)
