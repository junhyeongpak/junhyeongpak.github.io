---
layout: single
title: "Discriminant Analysis"

---

# 판별분석

## 베이즈 정리

"결과를 보고 원인을 추정하는 방식" 즉, 원인을 먼저 먼저 모델링한 확률로부터 결과 확률을 '역산'
더 일반적으로 이야기 하면 "관측된 결과를 바탕으로 어떤 가설이 맞을 확률을 계산하는 방법"

$P(A,B)=P(B|A)P(A)=P(A|B)P(B)$

- A가 관심의 대상이 되는 종속 변수일 때, 베이즈 정리는 P(B|A)를 활용하여 P(A|B)를 측정할 수 있도록 도와줌. 왜나하면 P(A|B)는 바로 측정이 어렵지만, P(B|A)는 상대적으로 측정이 용이하기 때문임.
- Bayes Rule:![image-20250420141908288](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420141908288.png)

	- 사후 확률: P(A|B)
	- 사전 확률: P(A)
	- 주변 확률: P(B)
	- 우도: P(B|A)

## 베이지안 추론 모델론적 관점

$P(\theta|D)=\frac{P(D|\theta)\cdot P(\theta)}{p(D)}$

- 사후 확률: 관측 이후의 믿음 즉, "데이터를 보고 나서 어떤 파라미터가 맞을까? 에 대한 확률"
- 사전 확률: 경험, 직관, 기존 지식으로부터 나오는 초기 가정
- 우도: "이 파라미터로 모델을 만들었을 때, 지금 본 데이터를 설명할 수 있는가?"
- 주변 확률: "관측된 데이터가 전체적으로 얼마나 가능성 있는가?" -> 모든 가능한 파라미터에 대해 데이터를 관측할 전체 확률

## 파라미터 $\theta$ 추정 접근법

- MLE: $\hat{\theta}_{MLE}=arg\, \underset{\theta}{max}P(D|\theta)$
  - 사전 정보 무시
  - 오직 데이터 D만을 고려
  - 확률 모델의 파라미터 최적화하는 고전적 방식
  - 예: 로지스틱 회귀, 선형 회귀 기본형 등
- MAP
  - 데이터 + 사전 믿음을 모두 고려해서 가장 그럴듯한 $\theta$를 찾음.
  - MLE와 달리, Prior $P(\theta)$도 고려
  - 하지만, 불확실성은 고려하지 않음
  - 예: 정규분포 추정 시, 사전 정보를 활용한 파라미터 추정
- 베이지안 추론
  - 특정 값이 아니라, 확률분포 전체를 추정
  - 불확실성을 보존함
  - 예: 베이지안 선형 회귀, 베이지안 신경망 불확실성 추론

## 베이지안 프레임워크

근데 사전확률을 잘 못 선택할 경우 성능에 큰 영향을 미침

- Conjugate Prior

  - 만약 사전 확률과 사후 확률의 분포가 비슷한 영역에 존재하면 사전 확률은 우도 함수에 대한 conjugate가 됨

  - | Likelihood            | Conjugate Prior |
    | --------------------- | --------------- |
    | Bernoulli or Binomial | Beta            |
    | Poisson               | Gamma           |
    | Multinomial           | Dirichlet       |

판별 분석 

배율을 최대화 한다. -> $\frac{집단 간 분산}{집단 내 분산}$을 최대화 하는 방향(판별 함수)를 찾는 것

![image-20250420141204797](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420141204797.png)

- 판별 접근: 입력 x가 $y=C_i$일 확률을 직접 모델링
  - 예시: 로지스틱 회귀, SVM, 신경망
- 생성 접근: 클래스 $C_i$가 입력 데이터를 어떻게 생성했는가?
  - 그리고 베이즈 정리를 통해 우리가 최종적으로 궁금한 $p(y|x)$를 계산
  - 예시: LDA, 나이브 베이즈

## 확률론적 생성모형(Probabilistic Generative Model)

$P(y=k|x)=\frac{P(x|y=k)\cdot P(y=k)}{P(x)}$

- 분류 문제는 각 클래스 k에 대한 확률을 비교하여 가장 큰 값을 선택함
  - $y_{new}=\underset{y\in Y}{argmax}\, p(y|x)$
  - 따라서, 모든 클래스에 대해서 P(x)는 동일하므로 굳이 계산할 필요 없음
  - $P(y=k|x)\propto P(x|y=k)P(y=k)$
  - 여기서 사전확률 $P(y=k)$는 아래와 같이 계산함
    - $P(y=k)\approx \frac{y=k인 데이터의 수}{모든 데이터의 수}=\hat{\pi}_k$
  - 여기서 Likelihood에 대해서 살펴보면,
    - $P(x|y=k)$가 확률분포 모형을 따른다고 가정함
    - k번째 클래스에 속하는 학습데이터의 분포를 참조하여 결정
    - 판별분석에서는 이를 정규분포로 가정함

# 선형판별분석(Linear Discriminant Anlaysis)

### 기본전제(Assumptions)

- 각 클래스 집단은 다변량 정규분포(Multivariate Normal Distribution)형태의 확률분포를 가짐

- 각 클래스 집단은 비슷한 형태의 공분산(covariance)구조를 가짐

  - 공분산: 2개의 확률변수의 상관정도를 나타내는 값
  - 공분산 행렬:![image-20250420155404879](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420155404879.png)

  - 공분산 패턴:

    - 완전 공분산 정규분포:![image-20250420155451633](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420155451633.png)

      -> 각 독립변수가 서로 연관성이 존재함

    - 대각 공분산 정규분포:

      ![image-20250420155632728](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420155632728.png)

      -> 각 독립변수가 독립이지만 $\sigma_1^2$이 분산이 더 커서 수평적인 형태를 띄고 있음

    - 구형 공분산 정규분포:![image-20250420155723728](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420155723728.png)

      -> 각 독립변수가 분산의 정도도 같고 독립이기 때문에 구형의 형태를 띄고 있음

- 다시 돌아와서, 기본전제(Assumptions)로 각 클래스 집단은 다변량 정규분포 형태의 확률분포를 가지며, 공통된 공분산 구조를 가진다고 가정함

  - 즉, 모든 클래스(k개의 집단)에 대해서,

    $\Sigma_k=\Sigma$

  - 따라서, 해당 공분산을 기준으로 확률밀도함수를 대입하여 베이즈 정리 산식에 대입하고 분모는 모든 클래스에 대해서 동일하므로 임의의 상수 C로 표현 후에 로그를 취하고 클래스 k와 무관한 부분을 제하면 아래외 같은 $\delta_k(x)$가 도출됨

  - $\delta_k(x)=log\,\pi_k-\frac{1}{2}\mu_k^T\Sigma^{-1}\mu_k+x^T\Sigma^{-1}\mu_k$

  - 모든 클래스 k에 대해서 위 식이 성립하고 클래스 $k_1$과 클래스 $k_2$의 경계선. 즉, 두 클래스에 대한 확률 값이 같아지는 지점 $\delta_{k_1}(x) = \delta_{k_2}(x)$으로 판별함수가 x에 대한 선형방정식이 되어, 경계선의 모양이 직선이 됨

  - $w^Tx+C=0$

- LDA는 판별과 차원축소의 기능을 모두 가짐

  ![image-20250420161824103](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420161824103.png)

  2차원의 두 가지 범주(초록, 파랑)를 갖는 데이터를 분류하는 문제에서 LDA는 먼저 하나의 차원(1d)에 projection하여 차원을 축소함

  - LDA는 차원 축소의 개념을 포함
  - 2차원 자료들을 판별 축에 정사영 시킨 분포의 형태를 고려

### LDA의 결정 경계 특징

- Projection축에 직교 하는 축

- 아래의 목표를 달성하도록 projection 시켜야 함

  - 각 클래스 집단의 평균의 차이가 큰 지점을 결정 경계로 지정

  - 각 클래스 집단의 분산이 작은 지점을 결정 경계로 지정

    ![image-20250420162455289](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420162455289.png)

- 사영 데이터의 분포에서 겹치는 영역이 작은 결정 경계를 선택(분산 대비 평균의 차이를 극대화하는 결정경계를 찾음)

  ![image-20250420162517411](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250420162517411.png)

# 이차판별분석(QDA, Quadratic Discriminant Analysis)

## 이차판별분석

- 클래스의 수와 상관없이, 공통 공분산 구조에 대한 가정을 만족하지 못할 경우 적용
- 즉, 클래스 별로 서로 다른 공분산 구조를 가지고 있을 때 활용
- 각 클래스는 다변량 정규분포를 가정
- $\Sigma_k=\Sigma$를 만족하지 않기 때문에, 결정경계는 x에 대한 선형방정식이 아닌 이차식의 형태가 됨