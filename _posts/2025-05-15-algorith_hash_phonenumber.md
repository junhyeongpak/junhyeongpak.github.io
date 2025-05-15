---
layout: single
title: "Hash - PhoneNumber"



---

# [프로그래머스 해시 - 전화번호목록]

## 문제 해결 과정

1. 해시 문제가 어떻게 적용되는지 아이디어를 떠오르기 쉽지 않았던 문제임. 이유를 생각해보면 문제 자체가 단순 반복 for문을 쓰려고 하지 않는 문제라 생각해서 떠올리기 쉽지 않았음.
2. GPT를 활용해 힌트를 획득하려고 작업했는데 GPT는 전화번호를 오름차순으로 정렬 후에 startwith()를 활용해서 phone_book[i]와 phone_book[i+1]를 비교하는 방식으로 힌트를 주었음 $\rightarrow$ 그러나 해시 유형의 문제 해결 사고 방식은 아니라고 판단해서 해시를 활용한 힌트를 달라고 요청.
3. GPT 답변: set()을 활용해 해시맵을 만들고 각 전화번호의 접두어를 단위 1부터 늘려가면서 자기자신을 제외하고 확장하도록 유도함. 사고해야할 것은 해시맵의 장점은 탐색, 삽입, 삭제 과정의 비용이 O(1)이라는 것에 있음.

## 필자가 처음 작성한 코드

```
def solution(phone_book):
    phone_book = set(phone_book)
    for i in phone_book:
        length = len(i)
        for j in range(length - 1):
            if i[:j-1] in phone_book:
                return False
    return True
```

위의 코드의 경우 통과는 되었지만 문제는 j = 1인 경우, 빈 문자열은 반환해버림.

## 수정한 코드

```
def solution(phone_book):
    phone_book = set(phone_book)
    for i in phone_book:
        for j in range(1, len(i)):
            if i[:j] in phone_book:
                return False
    return True
```

빈 문자열을 반환하지 않도록 range를 1부터 시작해서 빈 문자열을 반환하지 않도록 유도.

## 회고

해시맵의 장점은 접근, 삽입, 삭제가 O(1)의 시간 복잡도임을 기억.