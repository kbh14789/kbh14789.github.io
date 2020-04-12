---
layout: single
title: Strassen Algorithm
date: 2020-04-11 17:42:00 +0900
author: ByeongHeon
---

슈트라센 알고리즘을 알아보기에 앞서 

ex)  전체수행시간 약 

O(n^{log_27})

big-O 표현과 분할정복에 대해 먼저 알아보자



## 1. big-O 표기법(시간 복잡도)

시간복잡도 (Time Complexity)는 알고리즘을 수행하는데 연산들이 몇 번 이루어지는지를 숫자로 표기

연산의 개수 -> 데이터의 개수 n의 함수 = 시간복잡도 함수
$$
T(n)
$$
이라 표기한다.



big-O 표기법은

faster  ![img](https://t1.daumcdn.net/cfile/tistory/995DFD335C7EB57801)   slower

다음과 같은 실행 시간 순서를 갖는다.



![](https://miro.medium.com/max/1400/1*jiVqYhDzvODfVq6RH0DB1g.png)

실행시간이 길수록 데이터(n)의 값이 커질때 실행횟수가 기하급수적으로 늘어나는 것을 볼수 잇다.(즉 오른쪽으로 갈수록 비효율적이다.)



## 2.분할정복

분할정복은 크게 3가지 순서로 계산된다

- DIVIDE :  하나 또는 둘 이상의 인스턴스로 나눈다
- CONQUER : 나누어진 문제가 모두 하나 둘 인스턴스로 나누어져 있으면 COMBINE 하고 그렇지 않다면 다시 DIVIDE 한다.
- COMBINE : 나눠진 인스턴스들을 다시 하나로 합친다.



# 3. 일반적인 행렬곱 계산방법

EX)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/41c6337190684aff7b69f124226d6e62d79ebca5)
$$
\mathbf{A} = \begin{vmatrix}
\mathbf{A_1,_1} & \mathbf{A_1,_2} \\
\mathbf{A_2,_1} & \mathbf{A_2,_2} \\
\end{vmatrix}
$$

$$
\mathbf{B} = \begin{vmatrix}
\mathbf{B_1,_1} & \mathbf{B_1,_2} \\
\mathbf{B_2,_1} & \mathbf{B_2,_2} \\
\end{vmatrix}
$$

$$
\mathbf{C} = \begin{vmatrix}
\mathbf{C_1,_1} & \mathbf{C_1,_2} \\
\mathbf{C_2,_1} & \mathbf{C_2,_2} \\
\end{vmatrix}
$$



라는 A , B , C라는 각각ㅢ 2x2 행렬이 있다고 하자

C = A ● B 를 계산하면

C1,1 / C1,2 / C2,1 / C2,2 는 각각

![](https://t1.daumcdn.net/cfile/tistory/216A1B365818B6470D)

이다

위와같이 우리가 일반적으로 배운 방식으로 계산을 한다면

 **곱셈** : 8회 / **덧셈** : 4회 가 필요하다

​    

행렬 A,B,C, 가 각각 n X n인 행렬을 계산할땐

**곱셈** :

N^3 회

**덧셈** : 

N^2(N-1) 회

가 필요하게 된다.



# ※. Strassen Algorithm

슈트라센 알고리즘에서는 다음과 같이 **행렬** 을 정의할것이다 (위 A B 행렬을 이용하였다.)
$$
\mathbf {M_1}=\mathbf ({A} _{1,1}+\mathbf {A} _{2,2})(\mathbf {B} _{1,1}+\mathbf {B} _{2,2})
$$

$$
\mathbf {M_2}=\mathbf ({A} _{2,1}+\mathbf {A} _{2,2})(\mathbf {B} _{1,1})
$$

$$
\mathbf {M_3}=\mathbf ({A} _{1,1})(\mathbf {B} _{1,2}-\mathbf {B} _{2,2})
$$

$$
\mathbf {M_4}=\mathbf ({A} _{2,2})(\mathbf {B} _{2,1}-\mathbf {B} _{2,2})
$$

$$
\mathbf {M_5}=\mathbf ({A} _{1,1}+\mathbf {A} _{1,2})(\mathbf {B} _{2,2})
$$

$$
\mathbf {M_6}= \mathbf ({A} _{2,1}- \mathbf {A} _{1,1})(\mathbf {B} _{1,1}+\mathbf {B} _{1,2})
$$

$$
\mathbf {M_7}=\mathbf ({A} _{1,2}-\mathbf {A} _{2,2})(\mathbf {B} _{2,1}+\mathbf {B} _{2,2})
$$

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e9e6268d824de7ad5010a32a1921452b264f7ee)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d40beeba8019e378fa0ed4b6e549c44a140a9ec)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/45e8e9679d33f2c66e24bd812e1e554f95bb1571)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/c12df2bb70f8f09f33f1ca4b8c2d577d5850a2ee)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/715adfa757b74b3ad6b4eea545c24762e4079161)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/30107b9c9c99494bf75f23e84b505e5921cee46e)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e93ef1c265be8be96209dde36230d56e139fc72)



이 행렬들은

**곱셈**: 7회 / **덧셈** : 10회 가 필요하다



위 행렬들을 이용하여

C1,1 C1,2 C2,1 C2,2 를 표현하면


$$
C_1,_1 = M_1 + M_4 - M_5 + M_7 \\
C_1,_2 = M_3 + M_5 \\
C_2,_1 = M_2 + M_4 \\
C_2,_2 = M_1 - M_2 + M_3 + M_6
$$
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)

전체적으로

**곱셈** : 7회 / **덧셈** : 18회 가 필요하다



위에서 우리가 알고있는 방식으로 계산하였을때인 곱셈 : 8회 덧셈 : 4회인 경우가 더 계산횟수가 적어 더 빠르것이라 생각하였다

하지만 찾아보니

작은 행렬에 대해서는 우리가 알고있는 일반적인 행렬곱 계산방식이 빠르지만 큰행렬에 대해서는 곱셈이 덧셈보다  더 많은 시간이 걸리므로 곱셈을 적게하는것이 더 **효율적**이라고 한다

하지만 이렇게 효율적인 슈트라센 알고리즘도 단점이 존재한다.

슈트라센 알고리즘은 **수치 안정성** 이 떨어진다는 것이다.  





# ※. 변형된 알고리즘

- 위노그라드 알고리즘

위노그라드 알고리즘은 

곱셈 :7번 / 덧셈: 15번으로 표현 가능하다 (슈트라센 알고리즘보다 덧셈2번이 줄어듦)



이외에도

- 슈트라센 알고리즘을 변형한 빅터 판의 알고리즘
- 코퍼스미스-위노그라드 알고리즘
- 윌리엄스의 알고리즘

등이 있다

위처럼 더 나은 알고리즘들이 나왔지만 슈트라센 알고리즘과의 시간차이가 크게 나지 않고

처음으로 n^3 이라는 틀에서 벗어났다는거에 슈트라센 알고리즘의 대단함을 느낌

![](C:\Users\user\Desktop\image\제목 없음.png)