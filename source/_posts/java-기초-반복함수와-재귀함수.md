---
title: '[java]기초 - 반복함수와 재귀함수'
date: 2018-04-22 18:28:24
tags: java
category:
- java
---


반복함수 : 단순히 while 혹은 for 문법을 이용하여 특정한 처리를 반복하는 방식
재귀함수 : 자신의 함수 내부에서 자기 자신을 스스로 호출함으로써 재귀적으로 문제를 해결하는 함수
* 재귀함수는 경우에 따라서는 아주 간결하고 직관적인 코드로 문제를 해결할 수 있게 해주지만 때에 따라서는 심각한 비효율성을 낳을 수 있기 때문에
알고리즘을 작성할 때 유의할 필요가 있다.



## 팩토리얼을 재귀함수로 구현
```java
    // 팩토리얼이란?
    // 5! (5 팩토리얼)
    // 5! = 5 * 4 * 3 * 2 * 1 = 120
    public static int factorial(int number) {
        int sum = 1;
        for (int i = 2; i <= number; i++) {
            sum *= i;
        }
        return sum;
    }

    public static void main(String[] args) {
        System.out.println("10팩토리얼 : " + factorial(10));
    }
```
## 팩토리얼을 반복함수로 구현
```java
    // 팩토리얼이란?
    // 5! (5 팩토리얼)
    // 5! = 5 * 4 * 3 * 2 * 1 = 120
    public static int factorial(int number) {
        if (number == 1)
            return 1;
        else
            return number * factorial(number - 1);
        // 5! = 5 * 4!
        // 4! = 4 * 3!
    }

    public static void main(String[] args) {
        System.out.println("10팩토리얼 : " + factorial(10));
    }
```
## 피보나치 수열을 반복함수로 구현
```java
    // 피보나치수열
    // 이전 두개의 수를 합쳐서 다음 한개의 수를 만든다.
    // 1 + 1 = 2
    // 1 + 2 = 3
    // 2 + 3 = 5
    // 3 + 5 = 8

    // 피보나치수열에서 몇번째 해당하는 것이 어떤 값인가 구하는 프로그램
    public static int fibonacci(int number) {
        int one = 1;
        int two = 1;
        int result = -1; // 문제가 발생한것

        if (number == 1) {
            return one;
        } else if (number == 2) {
            return two;
        } else {
            for (int i = 2; i < number; i++) {
                result = one + two;
                one = two;
                two = result;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println("피보나치 수열의 10번째 원소는 " + fibonacci(10));
    }
```

## 피보나치 수열을 재귀함수로 구현
```java


    // 피보나치수열
    // 이전 두개의 수를 합쳐서 다음 한개의 수를 만든다.
    // 1 + 1 = 2
    // 1 + 2 = 3
    // 2 + 3 = 5
    // 3 + 5 = 8

    // 피보나치수열에서 몇번째 해당하는 것이 어떤 값인가 구하는 프로그램
    public static int fibonacci(int number) {

        if (number == 1) {
            return 1;
        } else if (number == 2) {
            return 1;
        } else {
            return fibonacci(number - 1) + fibonacci(number - 2);
        }
    }

    public static void main(String[] args) {
        System.out.println("피보나치 수열의 10번째 원소는 " + fibonacci(10));
    }
    
    // 작은 값에서는 활용할 수 있으나, 값이 커질수록 컴퓨터 연산이 비효율적이다.
    // 예) 50을 넣으면 값이 나오지 않거나 이상한 값이 나온다.

```