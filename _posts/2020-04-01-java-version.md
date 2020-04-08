---
layout : single
title: java version
date: 2020-04-01 00:23:00 +0900
author: ByeongHeon
---

| JDK 1.0    | *이전버전에 불렸던 이름은 OAK였으나 JAVA로 바뀜*             |
| ---------- | ------------------------------------------------------------ |
| J2SE 1.2   | 새로운 GUI, JIT, CORBA 등의 굵직한 기능이 추가 , strictfp, Swing GUI, JIT, Java Applet을 구동하는 웹 브라우저 플러그인, CORBA, Collections 등이 추가되었다. |
| J2SE 1.3   | HotSpot JVM, JNDI, JPDA, JavaSound 등이 추가되었다.          |
| J2SE 1.4   | assert, 정규표현식, IPv6, Non-Blocking IO, XML API, JCE, JSSE, JAAS, Java Web Start 등이 추가되었다. |
| J2SE 5     | 이 때부터 버젼 중 앞의 1을 빼버리고 표기하기 시작했다,Generics, Annotation, Auto Boxing/Unboxing, Enumeration, 가변 길이 파라미터, Static Import, 새로운 Concurrency API 등이 추가되었다. |
| JAVA SE 6  | 이 때부터 표기가 J2SE에서 Java SE로 바뀌었다. Scripting Language Support, JDBC 4.0, Java Compiler API, Pluggable Annotation 등이 추가되었다. 스크립팅 언어 지원과 함께 Rhino JavaScrip 엔진이 기본으로 탑재되었다. |
| JAVA SE 7  | Dynamic Language 지원, switch문에서 String 사용, try문에서 자동 자원 관리, Diamond Operator <>, 이진수 리터럴, 숫자 리터럴에 _ 지원, 새로운 Concurrency API, 새로운 File NIO 라이브러리, Elliptic Curve Cryptography, Java2D를 위한 XRender, Upstream, Java Deployment Ruleset 등이 추가되었다. |
| JAVA SE 8  | Nashorn JavaScript 엔진 탑재,                                |
| JAVA SE 9  | Project Jigsaw 기반으로 런타임이 모듈화된 것이 가장 큰 특징,이 버전부터 64비트 버전만 출시되었으며, 32비트 버전은 더 이상 공식적으로 나오지 않는다. |
| JAVA SE 10 | JDK의 레포지토리가 하나로 통합되었으며, JVM 힙 영역을 시스템 메모리가 아닌 다른 종류의 메모리에도 할당할 수 있게 되었다/이전 버전에서 Deprecated 처리된 API는 Java SE 10에서 모두 삭제되었다. |
| JAVA SE 11 | 이클립스 재단으로 넘어간 Java EE가 JDK에서 삭제되고, JavaFX도 JDK에서 분리되어 별도의 모듈로 제공된다./Java SE 11부터 Oracle JDK의 독점 기능이 오픈 소스 버전인 OpenJDK에 이식된다. / **Oracle JDK가 구독형 유료 모델로 전환된다. |
| JAVA SE 12 | 특징 중 하나로 문법적으로 Switch문을 확장한 것이 있다.       |
| JAVA SE 13 | java 12에서의 스위치 개선을 이어 yield 라는 예약어가 추가되었다. |



## Java 7

| 1.1  | Type Inference (타입추론)                              |
| ---- | ------------------------------------------------------ |
| 1.2  | Switch 문 문자열 case                                  |
| 1.3  | Automatic Resource Management                          |
| 1.4  | Catching Multiple Exception Type in Single Catch Block |

+) 이진수 표현 숫자앞에 0B나 0b를 붙이면 2진수로 판단



##  Java 8

| 2.1  | Lambda                              |
| ---- | ----------------------------------- |
| 2.2  | interface 클래스에 구현체 작성 가능 |
| 2.3  | Optional                            |
| 2.4  | 다양한 DateTime 추가                |
| 2.5  | GC 성능 대폭 개선                   |

## Java 9

인터페이스 내에 private 구현체 가능



모듈시스템 등장(jigsaw)



## Java 10

Local Variable Type Inference -> var 사용

JVM heap 영역을 NVDIMM 혹은 사용자 지정과 같은 대체 메모리 장치에 할당 가능