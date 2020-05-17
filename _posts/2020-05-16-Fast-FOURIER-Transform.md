---
layout: single
title: Fast FOURIER Transform
date: 2020-05-16
author: Kim Byeong Heon
---

## FFT (Fast Fourier Transform)

DFT(이산 푸리에 변환)과 IDFT를 빠르게 수행하는 효율적인 알고리즘이다. 대표적인 FFT 알고리즘은 쿨리-튜키 알고리즘이 있으며 , 이 알고리즘은 Butterfly Algorithm이라 불린다.



우리는 FFT를 알기에 앞서 DFT(이산 푸리에 변환) 과 DTFT(이산시간 푸리에 급수) 에대해 먼저 알아보도록 한다.

### DFT(Discrete Fourier Transform)



![](https://user-images.githubusercontent.com/62762126/82138914-0451b480-985f-11ea-8b31-3191f87cfb06.jpg)

위 그림 처럼 연속적인 값들에서 이산적으로 바꾸기 위해

연속적인 값을 일정크기(N)으로 나누어 sampling 한다.



![dft define](https://user-images.githubusercontent.com/62762126/82139284-ae324080-9861-11ea-849f-9e15b6dff505.jpg)

{F^0 , F^1 , F^2, ... , F^n} ===(DFT)===> {F0, F1, F2, ..., Fn}

그러면 위 그림처럼 된다.

이는 f를 N개로 sampling 했다 할수 있다.

### FFT(Fast Fourier Transform)

FFT 는 분할정복을 사용하는 알고리즘으로

예를들어

N=4일때

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/a17122e5097166a4b197212b17c6bdcf0f5209f5) 

와 같이 행렬로 표현할수 있으며

지수의 짝홀을 기준으로 식을 변형하면

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/9af88a21f9f2a2626c6005f54a85ad8db7efee77)

이는

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/15b40e73048081451aed8ab6fb9442b5ad7a6d65)

N=4인 DFT는 N=2인 DFT 두개를 사용해서 계산할수 있다.







## Big O 표기법

DFT에서는 

![](https://user-images.githubusercontent.com/62762126/82139003-e6388400-985f-11ea-81c1-b73dd4b21612.jpg)

F^k 하나를 구하는데 O(N)이 걸린다 그러므로 전체를 구하는데에는 O(n^2)이 걸리게 된다.



FFT에서는

![FFT2 1](https://user-images.githubusercontent.com/62762126/82142203-9a90d500-9875-11ea-84bf-ae2106b6e4fa.png)

분할정복을 위해 A(n)을 홀수부분과 짝수부분 두부분으로 나눈다.

![FFT2 2](https://user-images.githubusercontent.com/62762126/82142205-9b296b80-9875-11ea-9ec3-1f576be6b145.png)

이와같이 나누어 지며(이과정에서 O(N) )

![FFT2 3](https://user-images.githubusercontent.com/62762126/82142207-9e245c00-9875-11ea-80f1-bc1aca67c151.png)

라 정의 하면 위 A(n) 식은(이과정에서 2T(N/2))

![FFT2 4](https://user-images.githubusercontent.com/62762126/82142209-a086b600-9875-11ea-9675-d3da482b1e65.png)

![fft2 5](https://user-images.githubusercontent.com/62762126/82142345-a3ce7180-9876-11ea-9b67-f09750eb5ffc.png)

으로 간단하게 쓸수 있다.(이과정에서 O(n)만큼의 시간이 걸림)



총 시간복잡도를 T(N)이라 하면 

T(N) = O(N log N) 이다.



DFT(O(N^2)) >>>>>>>>>>>> FFT(O(N log N))



## CODE

GG;









##  MATLAB을 이용한 그래프 그리기

```
fs = 100
t =0:1/fs:1

x = 3*cos(20*pi*t)+6*sin(30*pi*t-3/(4*pi))
X = fft(x)

N = length(x)
n =0:N-1

f = fs*n/N

plot(f,2*abs(X)/N)
```

![그래프 1](https://user-images.githubusercontent.com/62762126/82143724-f9a81700-9880-11ea-938c-b0158ac52441.PNG)



```
fs = 100
t =0:1/fs:1

x = 3*cos(20*pi*t)+6*sin(30*pi*t-3/(4*pi))
X = fft(x)

N = length(x)
n =0:N-1

f = fs*n/N

cutoff = ceil(N/2)
cutoff =50
X = X(1:cutoff)
f = f(1:cutoff)

plot(f,2*abs(X)/N)
```

![그래프 3](https://user-images.githubusercontent.com/62762126/82143730-ff9df800-9880-11ea-86fe-a73ce26b2dad.PNG)



```
fs = 1000
t =0:1/fs:1

x = 3*cos(20*pi*t)+6*sin(30*pi*t-3/(4*pi))

X = fft(x)

N = length(x)
n =0:N-1

f = fs*n/N

cutoff =ceil(N/2)
cutoff =100
x = x(1:cutoff)
X = X(1:cutoff)
f = f(1:cutoff)

plot(f,abs(x),'--c')
hold on
plot(f,2*abs(X)/N,'--p')
```

![그래프 2](https://user-images.githubusercontent.com/62762126/82143728-fe6ccb00-9880-11ea-9568-35f7bba31efe.PNG)