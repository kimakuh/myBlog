---
title: '[java]기초 - 사용자 정의 함수'
date: 2018-04-22 12:27:04
tags:  java
category:
- java
---

자바는 객체지향의 꽃

객체지향 : 객체는 일반적으로 말하는 물건을 의미하며, 여기서 물건은 단순한 데이터가 아니고 그 데이터의 조작 방법에 대한 정보 또한 포함하고 있어 그것을 대상으로 다루는 방법을 객체지향이라고 한다.


## 사용자 정의 함수
사용자 정의 함수는 정해진 특정한 기능을 수행하는 모듈을 의미 ==> 함수를 적절히 활용하면 하나의 문제를 작게 분해할 수 있다.
예를 들어, 이진 탐색 트리는 삽입, 삭제, 순회 등 다양한 함수의 집합으로 구성된다.
만약 사용자 정의 함수가 없다면 오직 메인 함수에서 모든 알고리즘을 처리해야 하는데 이는 작업의 효율성을 저하시킬 수 있다. 또한 함수는 각각의 모듈로서 쉽게 수정되고 보완될 수 있다는 장점이 있다.



## 3개의 수 최대 공약수를 찾는 프로그램


```java
    // 함수
    // 함수의 반환형 ==> int
    // 함수의 이름 ==> function
    // 매개변수 ==> int a, int b, int c ==> 일반적으로 함수가 어떠한 값을 처리할때 사전에 주어진 값
    // 사용자 정의 함수
    // 자바에서는 메서드랑 함수랑 같은의미.
    // 반환형, 함수명, 매개뱐스
    public static int function(int a, int b, int c) {
        int min; // 가장 작은 수
        if (a > b) {
            if (b > c) {
                min = c;
            } else {
                min = b;
            }
        } else {
            if (a > c) {
                min = c;
            } else {
                min = a;
            }
        }
        for (int i = min; i > 0; i--) {
            if (a % i == 0 && b % i == 0 && c % i == 0) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println("(400,300,750)의 최대 공약수 = " + function(400, 300, 750)); // 출력결과 (400,300,750)의 최대 공약수 = 50
    }

```


## 약수 중 K번째로 작은 수를 찾는 프로그램

```java
    public static int function(int number, int k) {
        for (int i = 1; i <= number; i++) {
            if (number % i == 0) {
                k--;
                if (k == 0) {
                    return i;
                }
            }
        }
        return -1;

    }

    public static void main(String[] args) {
        int result = function(3050, 10); // 3050의 10번째 약수를 찾겠다.
        if (result == -1) {
            System.out.println("3050의 10번째 약수는 없습니다.");
        } else {
            System.out.println("3050의 10번째 약수는 " + result);
        }
    }
```
## 문자열에서 마지막 단어를 반환하는 함수

```java
    public static char function(String input) {
        return input.charAt(input.length() - 1); // String은 문자열을 의미하는 자료형으로
                                                 // 내부적으로 클래스로 작성이 되어있다.
                                                 // 때문에 charAt과 같은 다양한 함수를 가진다.
                                                 // charAt은 몇번째 문자열을 뽑아오는 함수
                                                 // input이라는 입력값이 들어왔을 때
                                                 // input의 길이 즉 문자열의 길이[length()]에서
                                                 // -1을 뺀 문자열을 가져온다.
                                                 // ==> 즉 가장마지막에 위치한 문자열을 가져온다.
                                                 // input.length() 은 해당 문자열의 길이를 말한다.
                                                 // 즉 Hello World를 보면 띄어쓰기를 포함해서
                                                 // 총 11개의 문자열로 구성되어 있다.
                                                 // charAt은 0부터 시작하기 때문에 Hello World에서
                                                 // 10번째 문자열은 d가 된다.
                                                 // charAt(10) ==> 'd'

    }

    public static void main(String[] args) {
        System.out.println("Hello World의 마지막 단어는 " + function("Hello World")); // 출력결과 d
    }
```


## max()를 이용하여 최대값을 저장하는 프로그램
```java
    public static int max(int a, int b) {
        return (a > b) ? a : b; // 삼항연산자
                                // a가 b보다 크다면 a를 반환하고
                                // 그렇지 않다면 b를 반환한다.
    }

    public static int function(int a, int b, int c) {
        int result = max(a, b); // a와 b중에서 더 큰값을 result에 넣는다.
        result = max(result, c); // result의 값을 다시 c와 비교
        return result;
        // 결과적으로 가장 큰 값이 result에 담기게된다.
    }

    // 함수를 여러개 만들어서 모듈화를 한다.

    public static void main(String[] args) {
        System.out.println("(345,567,783) 중에 가장 큰 값은 " + function(345, 567, 7830));
    }
```