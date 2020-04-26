---
layout: single
title: Egyptian fraction
date: 2020-04-26 16:39:00 +0900
author: byeongheon
---

## 이집트 분수

단위분수의 유한개의 합의 형태

예를 들어

1/2 + 1/3 + 1/4 처럼 단위분수로 표현하는것을 이집트 분수라 한다.

과거에 예를들어 빵 3개를 4명이 균등하게 배분하여 먹어야할때 와 같은 경우에 사용했다고 알려져 있다.

## 이집트 분수 코드

###  error

``` java
else if( a>b || b%a ==0){
                System.out.println("입력 오류");
                continue;
            }
```

분자가 분모보다 큰 경우나  약분되는 경우는 제외하였습니다.



### 단위분수 

```java
while(a>1) {
    n = b / a + 1;

    System.out.print("1/" + n +"+");
    cnt++;
    if (cnt > 3)
        break;
    a = n * a - b;
    b = n * b;
}
```

분모가 가장 작은거 부터(즉 단위 분수가 가장 큰거부터) 값을 차지하게한다.

그리고 계산이 딱 안떨어져서 항이 무한대로 나오는 경우를 방지하기 위해

```java
if (cnt > 3)
        break;
```

를 사용하여 항이 제한되게 만들었습니다.

ex) 8/19 = 1/3 + 1/12 + 1/229 + 1/52213 + 3/156636



단위분수가 가장 큰거부터 차지하는것을 보고 그리디 알고리즘과 비슷하다 생각하여 이집트 분수를 선택하게 되었습니다.



## 전체코드

```java
import java.util.Scanner;

public class Main {
    public static void main(String []args) {
        Scanner s = new Scanner(System.in);

        while(true){

            int n, cnt = 0;
            System.out.println("*************************");
            System.out.println("** 이집트 분수 (EXIT:0/0)**");
            System.out.println("*************************");
            System.out.print("입력:");
            int a = s.nextInt();
            int b = s.nextInt();
            if(a==0&&b==0){
               break;
            }
            else if( a>b || b%a ==0){
                System.out.println("입력 오류");
                continue;
            }

            while(a>1) {
                n = b / a + 1;

                System.out.print("1/" + n +"+");
                cnt++;
                if (cnt > 3)
                    break;
                a = n * a - b;
                b = n * b;
            }
            System.out.println(a+"/"+b);
            }
        }
    }
```





## 결과

*************************
** 이집트 분수 (EXIT:0/0)**
*************************
입력:2 3
1/2+1/6
*************************
** 이집트 분수 (EXIT:0/0)**
*************************
입력:3 7
1/3+1/11+1/231
*************************
** 이집트 분수 (EXIT:0/0)**
*************************
입력:7 13
1/2+1/26
*************************
** 이집트 분수 (EXIT:0/0)**
*************************
입력:3 4
1/2+1/5+1/21+1/421+2/840

*************************
** 이집트 분수 (EXIT:0/0)**
*************************
입력:0 0

Process finished with exit code 0