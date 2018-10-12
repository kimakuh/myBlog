---
title: '[java]기초 - 조건문 & 반복문'
date: 2018-04-21 20:34:20
tags: java
category:
- java
---

논리적 흐름의 기본

조건문 : 조건에 따라 실행하거나 실행하지 않거나. ==> 조건에 따라서 실행여부 결정
반복문 : 조건이 맞다면 그 조건 안에서 계속해서 반복한다.



## 조건문 & 반복문 정리

- 하나의 비교연산자는 true 혹은 false를 반환하게 됩니다.
- 모든 조건문 / 반복문에서는 왠만하면 무조건 괄호를 적용해라.
- for문 혹은 while문은 얼마든지 중첩될 수 있다.
- for(;;)은 while(ture)와 똑같이 무한 루프라는 의미로 동작한다.
- break;를 이용하여 반복문을 즉시 빠져나올 수 있다.

```java

    public static void main(String[] args) {
        int count = 0;
        for (;;) {
            System.out.println("출력");
            count++;
            if (count == 10) {
                break;
            }
        }

```



## if문을 이용하여 문자열이 특정문자열을 포함하는지 확인하는 프로그램

```java
    public static void main(String[] args) {
        String a = "I LOVE YOU.";
        
        // 조건문
        
        if(a.contains("LOVE")) {
            // 문자열을 검사한다.
            // a에 들어있는 I LOVE YOU. 라는 문자열에
            // LOVE가 들어있는지(포함하는지)
            // 들어있는 경우 실행되는 문장이 들어간다.
            System.out.println("Me Too.");
        } else {
            // 들어있지 않은 경우 실행되는 부분
            System.out.println("I Hate You.");
        }
        
    }
```

## 점수에 따라서 다른 메세지를 출력하는 프로그램

```java
    public static void main(String[] args) {
        int score = 95;

        if (score >= 90) {
            System.out.println("A+ 입니다.");
        } else if (score >= 80) {
            System.out.println("B+ 입니다.");
        } else if (score >= 70) {
            System.out.println("C+ 입니다.");
        } else if (score >= 60) {
            System.out.println("D+ 입니다.");
        } else {
            System.out.println("F 입니다.");
        }
    }
```

## 문자열과 정수형을 각각 조건문을 이용해 활용


```java
    public static void main(String[] args) {
        String a = "Man";
        int b = 0;

        // 자바는 String을 비교할때 equal()을 이용한다.
        // 이유? String은 다른 자료형들과는 다른 문자열 자료형이기 때문이다.

        if (a.equals("Man")) {
            System.out.println("남자입니다.");
        } else {
            System.out.println("남자가 아닙니다.");
        }

        if (b == 3) {
            System.out.println("b는 3입니다.");
        } else {
            System.out.println("b는 3이 아닙니다.");
        }

        if (a.equalsIgnoreCase("man") && b == 0) { // 대소문자 구분을 하지 않고 비교
                                                   // a가 대소문자와 상관없이 man 인지 비교하고
                                                   // b가 0 이라면, 즉 둘다 참이라면 아래의 내용이 출력된다.
            System.out.println("참입니다.");
        } else {
            System.out.println("거짓입니다.");
        }
        
        //  ==> 위와 같이 연산자는 조건문 / 반복문과 함께 사용된다.

    }

```

## while을 이용하여 1부터 1000까지의 합을 출력하는 프로그램

```java
    public static void main(String[] args) {
        int i = 1, sum = 0; // 한번에 두개의 변수 선언

        while (i <= 1000) { // 1부터 1000이 될때까지
            sum += i++;
        }
        System.out.println("1부터 1000까지의 합 : " + sum);
    }
```

## for문을 이용하여 삼각형을 출력하는 프로그램
### for문 사용1
```java
    final static int N = 30; // N이라는 30이라는 값을 가진 상수를 정의

    public static void main(String[] args) {
        // for문 : 초기화 부분, 조건 부분, 연산 부분
        for (int i = N; i > 0; i--) { // int 는 N부터 시작해서
                                      // i가 0보다 클때
                                      // i를 1씩 감소하며
                                      // 반복힌다.

            System.out.println("*");
        }
```
### for문 사용2(이중for문)
```java
    final static int N = 30; // N이라는 30이라는 값을 가진 상수를 정의

    public static void main(String[] args) {
        // for문 : 초기화 부분, 조건 부분, 연산 부분
        for (int i = N; i > 0; i--) { // int 는 N부터 시작해서
                                      // i가 0보다 클때
                                      // i를 1씩 감소하며
                                      // 반복힌다.
            
            // 이중 for문
            for (int j = i; j>0;j--) {
                System.out.print("*");
            }
            System.out.println( );
        }

    }
```
## for문을 이용하여 원을 출력하는 프로그램
```java
    final static int N = 15; // N이라는 15이라는 값을 가진 상수를 정의

    public static void main(String[] args) {
        for (int i = -N; i <= N; i++) {
            for (int j =- N; j <= N; j++) {
                if (i * i + j * j <= N * N) {
                    System.out.print("*");
                } else {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }

```