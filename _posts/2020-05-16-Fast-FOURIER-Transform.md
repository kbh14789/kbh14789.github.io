---
layout: single
title: Fast FOURIER Transform
date: 2020-05-16
author: Kim Byeong Heon
---

## FFT (Fast Fourier Transform)

DFT(이산 푸리에 변환)과 IDFT를 빠르게 수행하는 효율적인 알고리즘이다.  FFT 알고리즘은 쿨리-튜키 알고리즘을 사용하며, 이 알고리즘은 분할정복을 적용하여  n 크기의 dft를 n1, n2크기로 나누어 DFT를 수행하기때문에 
$$
n = 2^K
$$
인 경우를 많이 적용한다.



우리는 FFT를 알기에 앞서 DFT(이산 푸리에 변환) 과 DTFT(이산시간 푸리에 급수) 에대해 먼저 알아보도록 한다.

### DFT

![](https://user-images.githubusercontent.com/62762126/82138914-0451b480-985f-11ea-8b31-3191f87cfb06.jpg)





![](https://user-images.githubusercontent.com/62762126/82139003-e6388400-985f-11ea-81c1-b73dd4b21612.jpg)