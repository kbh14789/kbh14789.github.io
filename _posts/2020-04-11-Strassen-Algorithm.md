---
layout: single
title: Strassen Algorithm
date: 2020-04-11 17:42:00 +0900
author: ByeongHeon
---

슈트라센 알고리즘을 알아보기에 앞서 

ex)  전체수행시간 약 
$$
O(n^{log_27})
$$
과 같은 표현과 분할정복에 대해 먼저 알아보자



## 1. 빅오 표기법(시간 복잡도)

시간복잡도 (Time Complexity)는 알고리즘을 수행하는데 연산들이 몇 번 이루어지는지를 숫자로 표기

연산의 개수 -> 데이터의 개수 n의 함수 = 시간복잡도 함수
$$
T(n)
$$
이라 표기한다.



곱 계산 방법

EX)
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

![8d91fa79d27697a5c6551698c1a83a3d5837c57b](C:\Users\user\Desktop\8d91fa79d27697a5c6551698c1a83a3d5837c57b.svg)

![a08bea24eec9422cda82e6e04af1d96fc6822038](C:\Users\user\Desktop\a08bea24eec9422cda82e6e04af1d96fc6822038.svg)

![7adffe97db091ce8ba231352b3721bbe261985ca (1)](C:\Users\user\Desktop\7adffe97db091ce8ba231352b3721bbe261985ca (1).svg)

![8b40ed74cf54465d8e54d09b8492e50689928313](C:\Users\user\Desktop\8b40ed74cf54465d8e54d09b8492e50689928313.svg)

이다

위와같이 우리가 일반적으로 배운 방식으로 계산을 한다면

 **곱셈** : 8회 / **덧셈** : 4회 가 필요하다

​    

행렬 A,B,C, 가 각각 n X n인 행렬을 계산하게 된다면 

**곱셈** :
$$
N^3 회
$$
**덧셈** : 
$$
N^2(N-1) 회
$$
가 필요하게 된다.



# ※. Strassen Algorithm

슈트라센 알고리즘에서는 다음과 같이 **행렬** 을 정의할것이다
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
전체적으로

**곱셈** : 7회 / **덧셈** : 18회 가 필요하다



위에서 우리가 알고있는 방식으로 계산하였을때인 곱셈 : 8회 덧셈 : 4회인 경우가 더 계산횟수가 적어 더 빠르것이라 생각하였다

하지만 찾아보니

작은 행렬에 대해서는 우리가 알고있는 1과같은 방식이 빠르지만 큰행렬에 대해서는 곱셈이 덧셈보다  더 많은 시간이 걸리므로 곱셈을 적게하는것이 더 **효율적**이라고 한다

슈트라센 알고리즘은 **수치 안정성** 이 떨어지는것으로 알려져있다  

수치 안정성에 대해서는 아래에서 알아보자



## ※ 수치 안정성



![제목 없음](C:\Users\user\Desktop\제목 없음.png)

수치 안정성은 위험하니깐 다음에 알아보도록 하자





# ※. 변형된 알고리즘

- 위노그라드 알고리즘

$$
\mathbf {S_1}=\mathbf ({A} _{2,1}+\mathbf {A} _{2,2})\\
\mathbf {S_2}=\mathbf ({S} _{1}+\mathbf {A} _{1,1})\\
\mathbf {S_3}=\mathbf ({B} _{1,2}+\mathbf {B} _{1,1})\\
\mathbf {S_4}=\mathbf ({B} _{2,2}-\mathbf {S} _{3})\\
\mathbf {M_1}=\mathbf ({S} _{2}\mathbf {S} _{4})\\
\mathbf {M_2}=\mathbf ({A} _{1,1}\mathbf {B} _{1,1})\\
\mathbf {M_3}=\mathbf ({A} _{1,2}\mathbf {B} _{2,1})\\
\mathbf {M_4}=\mathbf ({A} _{1,1}-\mathbf{A}_{2,1})(\mathbf {B} _{2,2}-\mathbf{B}_{1,2})\\
\mathbf {M_5}=\mathbf ({S} _{1}\mathbf {S} _{3})\\
\mathbf {M_6}=\mathbf ({A} _{1,2}-\mathbf{S}_{2})(\mathbf {B} _{2,2})\\
\mathbf {M_7}=\mathbf ({A} _{2,2})\mathbf ({S} _{4}-\mathbf{B}_{2,1} )\\
\mathbf {T_1}=\mathbf ({M} _{1}+\mathbf {M} _{2})\\
\mathbf {T_2}=\mathbf ({T} _{1}+\mathbf {M} _{4})
$$

위 행렬을 이용하여
$$
C_{11} / C_{12}/C_{21}/C_{22}
$$
을 표현하면
$$
C_{11} = M_2 +M_3\\
C_{12} = T_1+M_5+_M6\\
C_{21} = T_2 - M_7\\
C_{22} = T_2 + M_5\\
$$
이다.

위노그라드 알고리즘은 

곱셈 :7번 / 덧셈: 15번으로 표현 가능하다 (슈트라센 알고리즘보다 덧셈2번이 줄어듦)



이외에도

- 슈트라센 알고리즘을 변형한 빅터 판의 알고리즘
- 코퍼스미스-위노그라드 알고리즘
- 윌리엄스의 알고리즘

등이 있다