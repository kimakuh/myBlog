---
title: '[java]기초 - 배열(Array)'
date: 2018-04-22 19:48:48
tags: java
category:
- java
---

배열은 쉽게 말해 데이터가 많을 때 사용하는 것
간단한 프로그램 예제에서는 단순히 한 두개의 변수만으로 프로그램을 작동시킬 수 있었지만
현실에서의 다양한 프로그램에는 아주 많은 양의 데이터가 사용되는 것이 일반적이다.
따라서 데이터가 많을 때 주로 배열을 이용할 수 있다.
이 때 배열은 한없이 많을 수 있으면서도 그 데이터 개수가 변경될 수 있는 데이터들의 집합을 
지정해 줄 수 있기 때문에 효과적으로 대부분의 프로그램에서 사용된다.

데이터가 들어갈 공간을 만들어준다.



## 원하는 개수만큼 배열 생성 및 최댓값을 구하는 프로그램
```java
    public static int max(int a, int b) {
        return (a > b) ? a : b; // a가 b보다 클때는 a를 반환하고
                                // 그렇지 않을 때는 b를 반환
    }

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.print("생성한 배열의 크기 입력 : ");
        int number = scan.nextInt();
        int[] arr = new int[number];
        for (int i = 0; i < number; i++) {
            System.out.print("배열에 입력할 정수를 하나씩 입력하세요(양수) : ");
            arr[i] = scan.nextInt();
        }
        int result = -1;
        for (int i = 0; i < number; i++) {
            result = max(result, arr[i]);
        }
        System.out.println("입력한 정수 중 가장 큰 값은 " + result);
    }
```
## 100개의 랜덤 정수의 평균을 구하는 프로그램
```java
    public static void main(String[] args) {
        int[] arr = new int[100];
        for (int i = 0; i < 100; i++) {
            arr[i] = (int) (Math.random() * 100 + 1);
        }
        int sum = 0;
        for (int i = 0; i < 100; i++) {
            sum += arr[i];
        }
        System.out.println("100 개의 랜덤 정수의 평균 값은 " + sum / 100);
    }
```
