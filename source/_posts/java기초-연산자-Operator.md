---
title: '[java] 기초 - 연산자(Operator)'
date: 2018-04-21 17:20:21
tags: java
category:
- java
---

연산자 : 연산을 도와주는 문법

계산의 기본

## 연산자 참고사항

- i++ 와 ++i 는 단순히 값을 증가시키려는 목적이라면 그 기능이 동일하다.
- 100 < x < 200은 잘못된 표현이다. ==> (100 < x) && (x < 200)로 표현하는것이 올바른 연산식 표현이다.
- i++ 은 i+ 와 동일한 표현이다. 또한, i= i + 1 과도 동일한 표현이다.==>모두 1만큼 증가시킨다는 의미를 나타낸다.



##


## 초를 입력 받아 몇 분 몇 초인지 계산하는 프로그램

```java
    final static int SECOND = 1000; // 상수 선언
                                    // SECOND 상수에 1000을 넣는다(저장한다).
    
    public static void main(String[] args) {
        
        int minute = SECOND / 60; // 상수 1000초는 몇분
        int second = SECOND % 60; // 상수 1000초는 몇초
        
        
        System.out.println(minute + "분" + second + "초");
        
        // 출력 16분 40초
    }
```

## ++와 --연산(증감연산자)
```java
    public static void main(String[] args) {
        int a = 10;
        System.out.println("현재 a의 값 = " + a );
        a++;
        System.out.println("현재 a의 값 = " + a );
        System.out.println("현재 a의 값 = " + ++a ); // 먼저 a에 1을 더하여 출력
        System.out.println("현재 a의 값 = " + a++ ); // 값의 변화가 없다.
                                                     // 출력이 된 이후에 값이 변한다.
        System.out.println("현재 a의 값 = " + a );   // 출력 결과 13
    }
```


## ++와 --연산2(증감연산자)
```java
    public static void main(String[] args) {
        int i = 20;

        System.out.println(i);
        i++;
        System.out.println(i);
        i = i + 1; // 아래의 식과 동일한 의미  ==> 1이 증가한다.
        System.out.println(i);
        i += 1; // 위의 식과 동일한 의미 ==> 1이 증가한다.
        System.out.println(i);
    }
```

## %연산자(모듈러 연산자)

```java
    public static void main(String[] args) {
        // 모듈러 연산자를 이용하여 나머지를 구한다.
        System.out.println(1 % 3);
        System.out.println(2 % 3);
        System.out.println(3 % 3);
        System.out.println(4 % 3);
        System.out.println(5 % 3);
        System.out.println(6 % 3);
        
        //출력결과
        // 1
        // 2
        // 0
        // 1
        // 2
        // 0
    }
```

## ==, >, <, &&, ||, ! 연산
```java
    public static void main(String[] args) {
        int a = 50;
        int b = 50;
        System.out.println("a와 b가 같은가? " + (a == b));
        System.out.println("a와 b가 큰가? " + (a > b));
        System.out.println("a와 b가 작은가? " + (a < b));
        System.out.println("a와 b가 같으면서 a가 b보다 큰가? " + ((a == b) && (a > b)));
        System.out.println("a가 50이 아닌가? " + !(a == 50));
    }
```



## 조건 ? 참 : 거짓(삼항연산자)

```java
    public static void main(String[] args) {
        
        int x = 50;
        int y = 60;
        
        System.out.println("최대값 " + max(x, y) );

    }

    // 반환형, 함수이름, 매개변수
    static int max(int a, int b) { 
        int result = (a > b) ? a : b;
        return result;
        
        // int a와 int b를 입력받아서
        // 둘 중 더 큰값을 반환하는 max라는 함수
        // 둘 중 더 큰값을 int 형태로 반환한다.
        
        
        // int result 는 a가 보다 클 때
        // 식이 참값이라면 a를 반환하고
        // 거짓이라면 b를 반환한다.
        // 그리고 그 결과인 result를 반환한다.
        
        
        // 출력결과 최대값 60
        
    }
    
```

## pow()를 이용한 거듭제곱 연산
```java
    public static void main(String[] args) {
        double a = Math.pow(3.0, 20.0); // 3의 20제곱이 실수 a에 넣는다.
        System.out.println("3의 20제곱은 " + (int) a);

    }
    
```
