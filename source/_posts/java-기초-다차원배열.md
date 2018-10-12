---
title: '[java]기초 - 다차원배열'
date: 2018-04-22 21:44:50
tags: java
category:
- java
---


배열의 확장
대부분 2차원배열
배열이 배열의 원소로 들어가는 구조
행과 열의 조합



## 10 x 10의 정수 랜덤 데이터를 생성하여 전체 데이터를 분석
```java
    public static void main(String[] args) {
        int N = 50; // 행과 열의 길이
                    // 2500개의 데이터가 들어간다.
                    // int => 4byte 라고하면
                    // 결국 10000byte 가 되고
                    // 10000byte = 10KB
        int[][] arr = new int[N][N];
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                arr[i][j] = (int) (Math.random() * 10);// (int) (Math.random() * 10); 0 부터 9까지의 랜덤한 정수가
                                                       // 만들어진다.
            }
        }
        for (int i = 0; i<N;i++) {
            for (int j =0; j<N;j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
```