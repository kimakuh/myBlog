---
title: '[java] 기초 - 자료형(Data Type)'
date: 2018-04-21 16:29:57
tags: java
category:
- java
---

자료형 : 나에게 필요한 데이터 타입

어떠한 데이터를 표현하고 싶을 때, 
데이터를 표현해줄 수 있는 타입을 만들어준다. => 표현할 데이터의 형태를 정의

자료형(Data Type)
- Primitive (원시자료형)
- Non-Primitive (비원시자료형) => 내부적 함수가 존재한다.

일반적인 프로그래밍 언어에는 정수 자료형 int , 실수 자료형 float과 double, 문자 자료형 char, 문자 자료형 char, 문자열 자료형 String이 사용된다. 자바에서는 특히 String을 많이 활용한다.



## double을 이용한 평균값 구하는 프로그램

```java
    public static void main(String[] args) {
        double a = 10.3;
        double b = 9.6;
        double c = 10.1;

        System.out.println((a + b + c) / 3);
        
        // 3개의 실수형을 선언해서 3개의 값을 더하고
        // 3으로 나눈 즉, 평균값을 구하는 프로그램
    }
```


## char을 이용한 문자출력 프로그램

```java
    public static void main(String[] args) {
        for (char i = 'a'; i <= 'z'; i++) {
            System.out.print(i + " ");
        
            // 컴퓨터 내부적으로 아스키코드를 활용하여
            // a 부터 z 까지 1씩 증가시키면서 출력한다.
        }
    }

```

## 10진수를 8진수와 16진수로 변경하는 프로그램

```java
    public static void main(String[] args) {

        int a = 200;
        System.out.println("10진수: " + a);
        System.out.format("8진수: %o\n", a); // 형식지정자
        System.out.format("16진수: %x\n", a); // 형식지정자
        
        // 10진수를 8진수와 16진수로 변경
    }

```

## String의 substring 함수 활용

```java
    public static void main(String[] args) {
        String name = "String Type";
        System.out.println(name);
        System.out.println(name.substring(0, 1)); // 실행결과 S
                                                  // 0 => 출력할 첫번째문자열 (시작점)
                                                  // 1 => 출력할 마지막 문자열 (종료점)
        System.out.println(name.substring(5, 8)); // 실행결과 g T 
                                                  // 공백도 하나의 문자로 인식
                                                  
        
    }

```

## 자료형 정리

- 기본적으로 정수를 나타내는 자료형이 많은 이유는 각 자료형이 차지하는 메모리 공간의 크기가 다르기 때문
- double 형이라고 하더라도 과도하게 큰 수를 저장하고자 하면 잘못된 계산결과가 나올 수 있다.
- 소수점 표기 형식을 지수형식으로 출력하고 싶으면 %e를 이용하면 된다.
- 자바에서 String은 내부적으로 Char의 배열로 되어있다. 자바에서 String의 최대 크기는? 컴퓨터의 메모리 크기만큼
- 자바의 String은 클래스 기반의 비원시적인 자료형
