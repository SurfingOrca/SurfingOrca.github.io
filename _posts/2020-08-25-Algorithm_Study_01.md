---
title: Algorithm_Study_01
excerpt: "1. 파이썬으로 풀어본 첫 번째 알고리즘 문제!"

toc: true
toc_label: "Table of Contents"
toc_sticky: true
categories:
  - Study
tags:
  - Algorithm
  - Python
last_modified_at: 2020-08-27
---

## 1. 파이썬으로 풀어본 **첫 번째 알고리즘 문제!**

파이썬으로 풀어본 첫 번째 알고리즘 문제.

프로그래머스에 가입하면 무료로 다양한 알고리즘 문제를 풀어볼 수 있다.

알고리즘에 대해서 이해할 때 다음과 같이 이해했다.

- 어떤 **문제**를 해결하기 위해 **공간 & 시간복잡도**를 최대한 **낮춰** 문제를 **해결**하는 방법
- 즉, **가장 효율적인 문제 해결 방법론**

> 알고리즘을 잘 이해하고 넘어가면 나중에 복잡한 문제(데이터 분석, EDA, Feature Engineering 등)를 해결하는데 보다 빨리 효과적으로 해결할 수 있다.

처음 컴퓨터 언어를 배우는 사람이라면 꼭 알고리즘 스터디를 진행하길 권유한다.

덤으로 그 언어와 빨리 쉽게 친해질 수 있을 것이다. ~~상대적으로 쉽다는게 함정...~~

## 2. 문제

### 1. 문제 설명

- 두 정수 `a, b`가 주어졌을 때 `a`와 `b` 사이에 속한 모든 정수의 합을 리턴하는 함수, `solution`을 완성하세요.
- 예를 들어 `a = 3, b = 5`인 경우, `3 + 4 + 5 = 12`이므로 `12`를 리턴합니다.

### 2. 제한조건

- `a`와 `b`가 같은 경우는 둘 중 아무 수나 리턴하세요.
- `a`와 `b`는 `-10,000,000` 이상 `10,000,000` 이하인 정수입니다.
- `a`와 `b`의 대소관계는 정해져있지 않습니다.

### 3. 입출력 예

|a &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; |b &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; |return &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; |
|---:|---:|---:|
|3|5|12|
|3|3|3|
|5|3|12|

[표 1]

## 3. 문제 해석

- 본 문제는 **2개의 정수**가 주어질 때 **그 사이의 값들**을 효율적으로 **반환**할 수 있는가를 테스트한다.
- 예를 들어 `3`과 `5`가 주어진다면, `3, 4, 5`를 **반환**할 수 있어야 한다.



## 4. 파이썬 문법

### 1. 사용한 조건문

> **`if`**

- 만약 `a`가 가지고 있는 값이 정수 `5`라면, < `a`는 `5`를 가지고 있는 **변수**입니다. > 를 출력하라.

    ```python
    if a == 5:
    	print('a는 5를 가지고 있는 변수입니다.')
    ```

### 2. 사용한 함수

> **`range`**

- 연속된 정수를 만들어라.

    ```python
    # range([시작:int, default = 0,] 끝:int [, 스텝:int, default = 1])
    # 끝은 숫자는 포함하지 않는다.

    >>> range(5)
    range(0, 5)

    >>> list(range(5))
    [0, 1, 2, 3, 4]

    >>> range(1, 5)
    [1, 2, 3, 4]

    >>> list(range(0, 7, 2))
    [0, 2, 4, 6]
    ```

> **`sum`**

- 합을 구하라.

    ```python
    # sum(iterable)
    # iterable: 반복가능한 형태, 즉 리스트, 튜플, 딕셔너리 등의 형태를 말한다.
    # range 역시 iterable 이다.

    >>> sum(5)  # 숫자는 iterable이 아니다.
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: 'int' object is not iterable

    >>> sum(range(5))  # range는 iterable이며, 끝은 포함하지 않고 나머지 숫자를 반환한다.
    10

    >>> sum([1, 2, 3, 4, 5])  # 리스트는 iterable이다.
    15

    >>> sum([5])  # 리스트는 iterable이기 때문에 하나의 숫자만 들어있어도 합계가 가능하다.
    5

    >>> sum((1, 2, 3, 4, 5))  # 튜플은 iterable이다.
    15
    ```

## 5. 문제 풀이

```python
# def는 define a function, 즉 **함수를 정의한다** 의 약자이다.
# solution이라는 함수를 정의하는데 이 함수는 매개변수 (parameters) a, b를 받는다.
# a, b는 정수를 받을 것이다. a, b중 어떤 숫자가 더 큰지는 현재 알 수 없다.
# 정의된 solution 함수를 사용자가 사용할 때 a, b 값이 정해진다.

def solution(a, b):

# 사용자가 제공한 a, b값 중 어떤 값이 큰지 모르기 때문에 비교하여
# 큰 값이 b에 담길 수 있도록 한다. 이렇게 하면 range 함수를 사용할 때
# 항상 동일한 형태, 즉 a를 시작 값, b를 끝 값으로 사용할 수 있다.
    if a > b:  
        a, b = b, a  

 # range 함수는 끝 값을 반환하지 않기 때문에
 # b+1을 통해 끝 값도 포함하여 반환해주자.
 # 반환된 값의 합을 구하면 두 정수 사이의 모든 정수의 합을 구할 수 있다.
    return sum(range(a,b+1))
```
