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

