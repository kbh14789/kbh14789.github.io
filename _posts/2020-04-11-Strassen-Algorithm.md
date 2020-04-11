---
layout: single
title: Strassen Algorithm
date: 2020-04-11 17:42:00 +0900
author: ByeongHeon
---

# 1. 기존의 행렬곱 계산 방법

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



라는 A , B , C라는 2x2 행렬이 있을때

C = A ● B 라고 하면 

C1,1 / C1,2 / C2,1 / C2,2 는 각각

![8d91fa79d27697a5c6551698c1a83a3d5837c57b](C:\Users\user\Desktop\8d91fa79d27697a5c6551698c1a83a3d5837c57b.svg)

![a08bea24eec9422cda82e6e04af1d96fc6822038](C:\Users\user\Desktop\a08bea24eec9422cda82e6e04af1d96fc6822038.svg)

![7adffe97db091ce8ba231352b3721bbe261985ca (1)](C:\Users\user\Desktop\7adffe97db091ce8ba231352b3721bbe261985ca (1).svg)

![8b40ed74cf54465d8e54d09b8492e50689928313](C:\Users\user\Desktop\8b40ed74cf54465d8e54d09b8492e50689928313.svg)

으로 구한다.

위와같이 계산시 **곱셈** : 8회 / **덧셈** : 4회 가 필요하다

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
하게된다.



# 2. Strassen Algorithm

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



작은 행렬에 대해서는 우리가 알고있는 1과같은 방식이 빠르다 하지만 큰행렬에 대해서는 곱셈이 덧셈보다  더 많은 시간이 걸리므로 곱셈을 적게하는것이 더 **효율적**이다.

슈트라센 알고리즘은 **수치 안정성** 이 떨어지는것으로 알려져있다  

수치 안정성에 대해서는 아래에서 알아보자



## ※ 수치 안정성



![제목 없음](C:\Users\user\Desktop\제목 없음.png)

수치 안정성은 위험하니깐 다음에 알아보도록 하자





# 3. 변형된 알고리즘

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