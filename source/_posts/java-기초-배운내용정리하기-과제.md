---
title: '[java]기초 - 배운내용정리하기(과제)'
date: 2018-04-22 11:53:57
tags: java
category:
- java
---


## 이름을 출력하는 프로그램작성
```java
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.print("이름을 입력해 주세요 > ");
        String name = scan.nextLine();
        System.out.println(name);
    }
```


## 사각형 모양을 출력하는 프로그램
```java
    public static void main(String[] args) {
        // 이중 for문
        for (int i = 0; i < 5; i++) {
            System.out.println();
            for (int j = 0; j < 10; j++) {
                System.out.print("*");
            }
        }
        System.out.println();

        // while 문
        System.out.println("---------------------------------");
        int line = 0;
        while (true) {
            for (int i = 0; i < 10; i++) {
                System.out.print("6");
            }
            System.out.println();
            line++;
            if (line == 5) {
                break;
            }
        }
       // 꼼수...
        System.out.println("---------------------------------");

        for (int count = 0; count < 5; count++) {
            System.out.print("9999999999");
            System.out.println();
        }
    }
```