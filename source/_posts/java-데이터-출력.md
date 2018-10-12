---
title: '[java] 데이터 출력'
date: 2018-04-11 19:28:28
tags: java
category:
- java
---

자바의 입출력


## 데이터 출력 - int 값 출력

```java
    public static void main(String[] args) throws Exception {
        FileOutputStream out = new FileOutputStream("temp/test3.data");
        
        int money = 1_3456_7890; // = 0x080557d2
        
        out.write(money); //항상 출력할 때는 맨 끝 1바이트만 출력한다.
        
        out.close();
        
        System.out.println("데이터 출력 완료!");

    }
```

## 데이터 출력 - int 값 읽기

```java
    public static void main(String[] args) throws Exception {
        FileInputStream in = new FileInputStream("temp/test3.data");
        
        // Exam02_1을 실행하여 출력한 데이터를 read()로 읽는다. 
        // read()는 1바이트를 읽어 int 값으로 만든 후 리턴한다.
        int value = in.read(); // 실제 리턴한 값은 0x08이다.
        
        in.close();
        
        System.out.printf("%x\n", value);
    }
```