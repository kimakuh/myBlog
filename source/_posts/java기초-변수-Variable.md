---
title: '[java] 기초 - 변수(Variable)'
date: 2018-04-21 14:43:07
tags: java
category:
- java
---

변수의 설정 및 사용방법

## 변수(Variable)와 상수(Constant)

변수: 변할수 있는 수 (열린 상자)
상수: 항상 변하지 않는 수 (닫힌 상자)

변수는 그 내부에 있는 값을 프로그램이 실행되는 도중에 언제든지 교체할 수 있다.
상수는 한 번 설정되면 프로그램이 종료될 때까지 변경되지 않는 데이터이다.


## 변수의 쓰임

```java
    public static void main(String[] args) throws Exception {
    
        // 변수를 선언하고 그 안에 값을 넣는 초기화를 한다.
        
        int intType = 100; // 변수를 선언하는 부분
                           // 정수형을 나타내는 int 변수의 이름을 intType으로 만들고
                           // intType이라는 변수안에 100 이란 값을 넣었다(저장한다).
        
        
        double doubleType = 150.5; // 변수를 선언하는 부분
                                   // 실수형을 나타내는 double 변수의 이름을 doubleType으로 만들고
                                   // doubleType이라는 변수안에 150.5 라는 값을 넣었다(저장한다). 
        
        String stringType = "문자열"; // 변수를 선언하는 부분
                                      // 문자열을 나타내는 String 변수의 이름을 stringType으로 만들고
                                      // stringType이라는 변수안에 "문자열" 이라는 값을 넣었다(저장한다).
        
        
        // 각각의 변수를 출력한다.
        
        System.out.println(intType); // 괄호안에 들어있는 변수를 출력하고 한칸 줄바꿈을 한다.
        System.out.println(doubleType); // 괄호안에 들어있는 변수를 출력하고 한칸 줄바꿈을 한다.
        System.out.println(stringType); // 괄호안에 들어있는 변수를 출력하고 한칸 줄바꿈을 한다.

    }
```

## 상수의 쓰임

```java
    final static double PI = 3.141592; // 상수의 선언
                                       // 메인함수 밖에 선언된다.
                                       // final = 한번 선언되면 절대로 변하지 않는다. 바뀔 수 없다는 의미
                                       // ==>즉 상수의 의미
                                       // PI라는 이름으로 상수를 정의하고
                                       // 3.141592라는 값을 넣었다(저장한다).
                                       // 상수는 절대 바뀔 수 없는 값이기 때문에 final이라는 문법을 사용한다.

    public static void main(String[] args) {

        int r = 30; // 변수의 선언
                    // 정수형을 나타내는 int 변수의 이름을 r으로 만들고
                    // r이라는 변수안에 30 이란 값을 넣었다(저장한다).
        
        // 변수를 출력한다
        
        System.out.println(r * r * PI); // 원의 넓이를 구하는 공식
                                        // 반지름(r)이 30인 원의 넓이
    }
```

## 표현가능범위

표현

```java

    final static int INT_MAX = 2147483647; // 상수의 선언
                                           // INT_MAX라는 이름으로 정수형 상수를 정의하고


    public static void main(String[] args) {

        int a = INT_MAX; // 위에서 만들었던 INT_MAX라는 상수를 
                         // a라는 변수안에 값으로 넣어준다.
        
        // 출력
        System.out.println(a); // 정상출력
        System.out.println(a + 1); //비정상출력(값의 오류)
        
    }
```

### 자료형의 종류와 구분 (Prinitive Data Type)

| 자료형 | 데이터 | 크기 (btye)| 크기 (bit)| 표현가능범위 |
|:--------:|:--------:|:--------:|:--------:|:---------|
| boolean | 참과 거짓 | 1 byte | 1 bit| true, false |
| char | 문자 | 2 byte| 16 bits| Unicode  Character|
| byte | 정수 | 1 byte  | 8 bits | -128 ~ 127 |
| short | 정수 | 2 byte| 16 bits | -32,768 ~ 32,767 |
| int | 정수 | 4 byte | 32 bits | -2,147,483,648 ~ 2,147,483,647 |
| long | 정수 | 8 byte | 64 bits |  -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |
| float | 실수 | 4 byte | 32 bits |  ±(1.40129846432481707e-45 ~ 3.40282346638528860e+38) |
| double | 실수 | 8 byte | 64 bits |  ±(4.94065645841246544e-324d ~ 1.79769313486231570e+308d) |


## 사칙연산 프로그램

```java
    public static void main(String[] args) {

        // a 와 b 변수를 선언하고 값을 넣어준다.(초기화)

        int a = 1;
        int b = 2;

        // 사칙연산 출력
        // 문자열과 정수형 형태를 합쳐서 식을 표현할 수 있다.
        System.out.println("a + b = " + (a + b)); 
        System.out.println("a - b = " + (a - b)); 
        System.out.println("a * b = " + (a * b)); 
        System.out.println("a / b = " + (a / b)); 

    }
```



## 형변환(실수형 -> 정수형)

```java
        int a1 = 0.5; // a1 라는 값은 int로 선언되었기 때문에 정수만 들어갈 수 있다.
                     // ==> 오류가 발생한다. 0.5라는 실수는 넣을 수 없다.
        
        // 해결방법
        int a2 = (int) 0.5; // 형변환을 한다.
                            // ==> 즉 실수형을 정수형으로 형변환한다.
        
        // 출력
        System.out.println(a2); // 출력결과  0
                                // ==> 실수형을 정수형으로 바꿀 때에는
                                // ==> 소수점 자리 뒷 부분은 전부 제거된다.
```




## 형변환(정수형 -> 실수형)


```java
    public static void main(String[] args) {

        double b = 0.5;
        int a = (int) (b + 0.5); // b 가 어떠한 실수 값이던 간에
                                 // 항상 0.5를 더하고 int 형으로 변경한다.
                                 // ==> 항상 반올림이 된 값만 출력한다.

        // 출력
        System.out.println(a); // 결과 1
    }
```

## 변수활용의 주의사항

- 자바에서는 변수 초기화를 하지 않으면 사용할 수 없다.
- 정수를 나타내는 타입 [btye, short, int, long]
- 정부 변수안에 실수를 넣으면 정수 부분만 변수에 저장된다.
- 실수 값을 반올림할 때는 변수에 0.5를 더한 뒤에 정수형으로 형변환을 하면 된다.
- 반올림한 값 =(int)(실수 + 0.5);
