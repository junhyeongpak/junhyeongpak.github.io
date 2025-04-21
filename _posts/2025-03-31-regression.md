---
layout: single
title: "Linear Regression"

---

# 선형회귀

---

## 분류와 회귀

---

### 지도학습

- 분류: 사전에 정의해놓은 가능성 있는 클래스 레이블들 중 하나를 선택
- 회귀: 실수 예측

---

### 선형회귀

종속 변수 한개와 한 개 이상의 독립변수의 관계를 '선형적'으로 모델링하는 접근 방식

- 단순선형회귀: 1개의 독립 변수
- 다중선형회귀: 2개 이상의 독립 변수

---

### 관점

- 지도학습: 종속변수와 독립변수의 관계를 선형적으로 잘 가정하고 그 관계를 잘 표현하는 파라미터를 추정하는 방법
- 회귀: 종속 변수의 값을 잘 예측하는 것

---

### # 1. 지도 학습 문제

![image-20250331173351953](/Users/wnsgud/Library/Application Support/typora-user-images/image-20250331173351953.png)

-> 독립변수와 종속변수간의 관계를 '선형적으로' 잘 가정

### # 2. 파라미터 추정

$h(x)$와 $y$와의 차이가 적게하는 것을 목표로 두고 아래 식 (1)으로 표현할 수 있음

(1) $\underset{\theta_{0},\theta_{1}}{argmin}\frac{1}{2m}\Sigma_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2$

(2) 비용함수 $J(\theta_{0},\theta_{1})=\frac{1}{2m}\Sigma_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)}))^2$

(3) Sum of Squared Error = $\Sigma_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2$

(4) MSE(Mean Squared Error) = $\frac{1}{m}\Sigma_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2$

---

## 경사 하강

경사를 하강하면서 $J(\theta)$를 최소화하는 $\theta$를 찾는 방법

- 경사 하강 알고리즘의 [GOAL] -> $\underset{\theta_{0}, \theta_{1}}{argmin} J(\theta_{0}, \theta_{1})$
- [OUTLINE]
  - Parameters 값 초기화
  - 비용 함수 값이 최소가 될 때까지 파라미터를 지속적으로 업데이트

Repeat until convergence {

​	$\theta_{j}:=\theta_{j}-\alpha\frac{d}{d\theta_{j}}J(\theta_{0},\theta_{1})$

}

단, j = 0과 j = 1을 업데이트 할 때, simultaneous update를 수행해야 함

-> 그렇지 않으면 각 파라미터 값을 업데이트하고 다시 구하게 되므로 꼬여서 제대로 경사 하강이 이루어지지 않을 수도 있음

---

## 경사하강 확인

1. $J(\theta)$값이 iteration이 증가할수록 수렴하는지 확인
2. 수렴조건을 설정 ex) $J(\theta)^{(t)} - J(\theta)^{(t - 1)} <= \epsilon, (\epsilon = 10^{-3})$

단, 어떤 $\theta$를 선택하더라도, $X\theta$는 반드시 X의 Column Space에 존재해야 함.

따라서 X의 Column Space에 존재하는 무수히 많은 점들 ($X\theta$)에 대해서도 Vector y와 가장 가까운 지점에 위치한 point를 생성하는 vector $\hat{y}$를 찾는 문제로 귀결





