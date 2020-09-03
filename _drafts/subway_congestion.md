---
title: [Side Project No.1] 지하철은 언제 이용해야 가장 안전할까?
excerpt: "지하철 혼잡도 예측 모델 만들기"

toc: true
toc_label: "Table of Contents"
toc_sticky: true
categories:
  - Side_Project
tags:
  - Python
  - Machine_Learning
last_modified_at: 2020-09-03
---

> 지하철 혼잡도 예측 모델 만들기

<br>

## 들어가기 전

코로나19는 우리의 삶을 완전히 변화시켰다.  
이제 마스크는 마치 옷처럼 매일 사용해야 하는 필수품이 되었다.  
2.5단계로 격상된 사회적 거리두기를 덤덤하게 받아들이는 우리들.  
언제쯤 이런 문자를 받아볼 수 있을까??

![Image_1]({{ site.url }}{{ site.baseurl }}/assets/images/2020-09-03-subway_congestion/end_of_covid19.jpg)

<br>

안전하게 이동하는 것은 이제 모두의 관심사이자 공감대이다.  
출퇴근 길에도 회사에서도 등하교 시간에도 학원에서도 거리에서도..  
물론 대중교통을 이용하면서도 우리는 마스크를 사용한다.  

하지만 그럼에도 출퇴근 시간에 옆 사람과 간격이 10cm에 불과할 때,  
**'이렇게 다니는 게 안전할까?'** 하는 의구심이 들지만, 어쩔 수 없다.

적어도 어린 자녀와 이동을 하거나, 연세가 지긋하신 어르신과 이동해야 할 경우,  
가장 덜 붐비는 시간대는 언제인지 알 수 있다면 좋겠다는 생각을 했다.


## Introduction

- 문제제기: 노약자가 코로나로부터 위협을 받고 있다.
-
