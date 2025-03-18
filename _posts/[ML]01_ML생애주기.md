---
layout: single
title: "ML LIFE CYCLE"

---

# ML 생애주기

---

## ML in AI

---

AI $$ \supset $$ ML $$ \supset $$ DL

AI란 "The science and engineering of making intelligent machines"

|       | Humanly | Rationally |
| ----- | ------- | ---------- |
| Think | ①       | ③          |
| Act   | ②       | ④          |

---

### Think Humanly

"Cognitive thinking machines with minds"

인지과학적 접근으로 인간의 뇌기능 연구에 초점을 둠

- 인간은 어떻게 사고하는가?
- 인간 뇌활동의 원리는 무엇인가?

주요 발전 분야 Cognitive Science, Cognitive Neuroscience, Computational Psychology

-> 다만, 현재까지 인간 수준의 보편적 지능을 설명할 수 있는 이론은 없음

---

### Act Humanly

사람처럼 행동할 수 있는 기계에 초점

Turing이 제안한 AI의 핵심 컴포넌트

- Knowledge
- Reasoning
- Language understanding
- Learning

이 컴포넌트들이 발전해서 하나의 분야로써 자리잡듬 ex) Language Understanding, Knowledge Representation and Reasoning, Machine Learning, Robotics, Computer Vision

---

### Think Rationally

논리적 기계에 초점(로직에 기반한 추론)

- 예)
  - 소크라테스는 인간임
  - 모든 인간은 죽음
  - 그러므로 소크라테스는 죽을 것임
- 모든 지식을 이용해 새로운 지식을 도출

문제점)

- 모든 지능적 활동 및 지식들이 로직에 의해 표현되기 어려움
- 로직이 매우 복잡한 형태를 띔

---

### Act Rationally

목표를 최대로 달성할 수 있도록 행동하는 기계

- 주어진 정보에 기반하여 목표를 최대로 달성하도록 설계
- 목표는 "Utility of Outcome"로 표현됨

문제점)

- 계산 복잡도가 매우 높기 때문에 완벽한 결과를 달성하기 어려움

---

## AI - 컴퓨터 과학분야 초점

"The study and design of intelligent agents, where an intelligent agent is a system that perceives its environment and takes actions that maximize its chances of success"

### 인공지능의 지향점 Function-based Classification

- Weak AI
  - 기계가 intelligence를 표출할 수 있으나, 인간의 마음이나 인지능력은 필수 요소로 갖추지 않음
  - 대부분의 연구분야가 속한 범주
- Strong AI
  - 인간의 intelligence와 같은 수준이거나 그 이상의 능력
  - Artificial General Intelligence

- 3단계 발전 모델 (ANI -> AGI -> ASI)
  - ANI(Artificial Narrow Inelligence): 특화 AI
    - 특정 작업에 특화하여 수행
  - AGI(Artificial General Intelligence): 일반 AI
    - 인간과 동일한 사고, 추론 능력을 갖춘 AI
  - ASI(Artificial Super Intelligence): 초지능 AI
    - 인간을 초월하는 지능을 가진 AI
    - 미래의 인공지능

---

## ML 용어

- Machine Learning (ML)
  - 데이터로부터 학습하는 모델을 구축하는 프로세스
- ML Model
  - 데이터에서 패턴을 학습하는 알고리즘
- ML Project
  - ML 프로젝트 $$ \neq $$ "기계학습 모델 만들기"
  - 여러 단계들로 구성되어 있음

---

## MLOps (ML Operations)

- MLOps
  - Machine Learning 모델이 프로덕션까지 도달하는데 도움을 주는 방법론
  - ML Model의 지속적인 배포 및 자동화를 위한 파이프라인

![생애주기](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwtXsO%2Fbtrs71qoX5a%2FjFvuIcKQRM0VkwbweMoczk%2Fimg.png)

>  (출처: https://abluesnake.tistory.com/126)

---

## MLOps의 6단계

- [1단계]: 문제 정의 - ML로 해결가능한 문제 정의 및 데이터 확보방안

  - 문제 정의
    - ML로 해결할 수 있는 문제를 정의하고 가설 설정
    - 가설 검증을 위한 데이터셋 확보
  - 비즈니스 임팩트 함께 고려
    - 이윤을 창출할 수 있는 문제 정의는 ML 프로젝트로 확장

- [2단계]: 데이터 준비 - 데이터 수집 및 탐색

  - 데이터셋 공유 및 재사용을 위한 버전관리 필요
    - 데이터셋이 문제정의에 따라 다양하게 가공되어 사용 가능
    - 데이터셋이 추가되어 별도의 관리가 필요
  - 데이터 탐색
    - Python, R 등 데이터 시각화를 위한 다양한 패키지 이용 가능
    - 데이터 탐색을 위한 시각화 방식에 대한 고민 필요
    - Feature 중요도 검색
      - 데이터로부터 제공되는 속성들 중에서 문제해결에 영향을 미치는 요인을 탐색
      - Ex) 소득 이진 분류(고소득자/저소득자)를 위한 데이터셋
        - 어떤 데이터 속성이 소득에 미치는 영향이 큰가를 탐색
        - 교육수준 > 나이 > 주당 근무시간
  - 데이터 가공
    - 데이터 가공 방법은 모델 성능을 좌우하는 중요한 부분

- [3단계]: 모델 설계 - 모델학습과 실험

  - 모델 학습 - 모델 만들기
    - 모델학습을 위한 입력조건: 데이터, 학습 알고리즘, 하이퍼파라미터
      - 학습 알고리즘: 입력 데이터로부터 패턴을 찾아냄
      - 하이퍼파라미터: 최적의 성능을 내기 위한 알고리즘의 속성
    - 모델: 데이터/알고리즘/하이퍼파라미터를 가지고 연산을 거쳐 만들어지는 산출물
  - 실험 - 다양한 실험을 통해 최적 모델을 찾아가는 것
    - 입력조건(데이터/알고리즘/하이퍼파라미터)을 바꾸는 과정
    - 비교평가: 다양한 모델에 따른 성능비교 및 학습조건 비교(데이터/알고리즘/하이퍼파라미터)
    - 최적 모델: 만족할만한 성능을 제공하는 모델(best model)
    - 최적화:
      - 문제해결을 위해 모든 경우 수를 탐색하지 않고 최적화된 방법으로 데이터/알고리즘/하이퍼파라미터를 찾아내는 것
      - 일반적으로 기존 연구 결과를 참조하거나 개인 노하우를 활용
  - Auto ML (Automated ML):
    - 모델 학습/최적화/비교평가 자동화: 빠르게 최적 모델을 찾아내는 지능화된 학습방법
    - 모든 경우의 수를 실험하지 않고, 입력 조건에 따른 ML 파이프라인 성능을 예측하여 성능이 좋을 것으로 예상되는 입력 조건을 통해 모델 학습을 자동으로 진행
  - 모델 검증
    - 예측성능
      - 모델의 예측값이 실제갑소가 얼마나 가까운가 측정
      - 일반화의 정도: 적정 수준의 적합화
    - 처리성능
      - 모델이 예측값을 계산해 내는데 소요되는 시간 및 사용하는 컴퓨팅 자원
      - 서비스가 배포된 뒤 얼마나 안정적으로 운영되고 있는지 확인하는 지표

- [4단계]: 배포/서빙 - 모델을 통한 서비스 운영

  - 배포/서빙
    - 가장 좋은 모델을 선택하고 검증과정을 거친 후, 이를 패키징하여 서비스로 배포하는 것
    - 서비스 패키징: 컨테이너 이미지 제작 기술
      - 컨테이너 기술은 모델 학습 환경과 실제 서비스되는 예측 환경을 동일하게 맞추기 위해 필요
      - 환경: 모델 버전, Python 패키지 버전, 추론 로직 등을 포괄
    - 배포/서빙: 컨테이너를 서버에서 실행하여 서비스를 운영하는 것

- [5단계]: 모니터링 - 지속적인 서비스 모니터링

  - 모니터링: 데이터 드리프트
    - 데이터의 패턴 특성이 시간이 지나면서 변하는 현상
    - 학습 데이터와 예측 데이터의 차이(패턴, 분포가) 커질수록 에측 성능이 저하될 가능성
    - 지속적으로 데이터 드리프트를 모니터링하면서 모델의 재 학습 시점을 판단

- [6단계]: 모델 재 학습 및 재 배포

  - 지속적으로 데이터 드리프트를 모니터링하면서 모델의 재학습 시점으로 판단되면 모델 수집된 데이터를 추가하여 모델을 재학습하고 재배포한다.

    



