---
layout: single
title: "Linear Regression"


---

# 로지스틱 회귀

## 분류

사전에 정의해 놓은, 가능성 있는 여러 개의 클래스들 중에서 하나를 선택

- 이진 분류: 2개의 클래스 label
- 다중 분류: 3개 이상의 class label

### 분류문제에 선형회귀를 적용할 수 있을까?

![image-20250418155442686](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250418155442686.png)

- 이진분류에서 종속변수 y의 값:
  - y = 0 또는 y = 1
- 선형회귀에서 가설함수 $h_{\theta}(x)$의 값:
  - $h_{\theta}(x) > 1$또는 $h_{\theta}(x)<0$의 경우가 존재
- 로지스틱 회귀:
  - $0 \le h_{\theta}(x) \le 1$
  - 분류로 적용 가능

## 로지스틱 회귀

- 실제로 많은 자연, 사회 현상에서는 특정 변수에 대한 확률 값이 선형이 아닌 S-커브 형태를 따르는 경우가 많음
- x값으로 어떤 값이든 받을 수 있지만, 출력결과(y)는 항상 0~1 사이의 값이 됨(누적분포함수) 요건을 충족
- 시그모이드(sigmoid function)라고 명명하기도 함

### 로지스틱 회귀 가설함수 해석

- 입력값 x넣었을 때, y = 1일 추정 확률
- 예시로 $x_0, x_1$이 각각 1과 종양크기 일 때, $h_\theta(x)=0.7$이라면 악성 종양일 확률을 70%라고 해석할 수 있음
- $h_{\theta}(x)=P(y=1|x;\theta)=g(\theta^Tx)$
- 단, $g(z)=\frac{1}{1+e^{-z}}$

## 비용함수(Cost Function)

- 로지스틱 회귀에서는 더 이상, 선형 회귀에서 사용했던 비용함수를 사용할 수 없음
- 왜냐하면, 로지스틱 함수가 non-linear하므로 더이상 convex하지 않아 수많은 local optima를 야기시키기 때문임
- $J(\Theta)=\frac{1}{m}\underset{i=1}{\overset{m}{\Sigma}}Cost(h_\theta(x^{(i)}), y^{(i)})$

![로지스틱비용](/Users/wnsgud/blog/junhyeongpak.github.io/img/로지스틱비용.png)

- If y = 1) $h_\theta(x)$값이 1로 가야 하므로 $Cost(h_\theta(x), y)=-log(h_\theta(x))$
- If y = 0) $h_\theta(x)$값이 0으로 가야 하므로 $Cost(h_\theta(x), y)=-log(1-h_\theta(x))$

## 비용함수와 Cross-Entropy의 연관성

### Cross-Entropy

- 하나의 확률 분포를 다른 확률분포로 인코딩할 때 필요한 평균 정보량
- $H(p, q)=-\underset{i=1}{\Sigma}p(i)\,log\,q(i)$
- 분류에서 p(i) = 1을 정답클래스로 할 때 나머지는 0이 되면서 해당 클래스의 $log\,q(i)$만 남게됨

## MLE(Maximum Likelihood Estimation) 유도

- 로지스틱 회귀는 우도(likelihood)를 최대화하는 방식으로 학습
  - $L(\theta)=\prod_{i=1}^{m}\hat{p_i}^{y_i}(1-\hat{p_i})^{1-y_i}$
- Log Likelihood:
  - $\log(L(\theta))=\Sigma_{i=1}^m[y_i\,\log(\hat{p_i})+(1-y_i)\log(1-\hat{p_i})]$
- 그러나 비용함수는 최소화 시키는 것이 국룰이기 때문이 -를 붙여서 최소화 시킴
  - Negative Log Likelihood = $-\log(L(\theta))=-\Sigma_{i=1}^m[y_i\,\log(\hat{p_i})+(1-y_i)\log(1-\hat{p_i})]$

- 로지스틱 회귀의 비용함수는
  - $J(\Theta)=\frac{1}{m}\Sigma_{i=1}^m[y^{(i)}\,\log(h_{\theta}(x^{(i)}))+(1-y^{(i)})\log(1-h_\theta(x^{(i)}))]$

- 따라서 $\underset{\Theta}{arg\,min}J(\Theta)$를 목표로 함

## 경사하강

- 결론적으로 로지스틱 회귀의 경사하강 업데이트 방식은 선형 회귀와 동일함 
- 단, simultaneous update로 진행시켜야 함

## Logit

- 목적은 (0, 1)에 존재하는 확률을 $(-\infty, \infty)$로 표현하여 실수로 매핑하여 확률의 정도의 크기를 확인하기 위해서 도입. 따라서 모델의 해석에 도움을 줌

- $logit(p)=log(odds)=log(\frac{p}{1-p})$

- $p=P(y=1|x)=\sigma(\theta^Tx)=\frac{1}{1+e^{-\theta^Tx}}$

- $logit(p) = \theta^Tx$

  ![Logit](/Users/wnsgud/blog/junhyeongpak.github.io/img/Logit.png)

- 예를 들어 설명 변수 $x_1$이 1 증가하면 odds는 $exp(\beta_1)$배로 변함
- 그러나 초기 확률에 따라 실제 확률 변화가 달라지므로 유의해야 함

## 다중분류(Multiclass Classification)

- $h_\theta^{(i)}=P(y=i|x;\theta) \,(i=1,2,3,.., k)$
- 각 클래스 i에 대하여 로지스틱 회귀를 훈련하고 y = i일 확률을 예측함
- 새로운 입력 x에 대한 분류를 위해, $h_\theta^{(i)}(x)$를 최대화하는 i를 선택
  - $\underset{i}{argmax}\,h_\theta^{(i)}(x)$
  - 비용함수
    - K($\ge$3)개의 클래스에 대한 확률을 동시에 예측
    - Softmax함수를 사용해 확률 계산 $P(y=k|x)=softmax(z_k)=\frac{exp(\theta_k^Tx)}{\Sigma_{j=1}^kexp(\theta_j^Tx)}, \, z_k=\theta_k^Tx$
  - 예측결과: 확률이 가장 높은 예측값으로 선택 $\hat(y)=\underset{k}{argmax}\,P(y=k|x)$
  - $Cost(h_\theta(x^{(i)}), y^{(i)})=-\Sigma_{k=1}^Ky_{i, k}\log P(y=k|x_i)$
  - 따라서, $J(\Theta)=-\Sigma_{i=1}^m\Sigma_{k=1}^Ky_{i,k}\log P(y=k|x_i)$
