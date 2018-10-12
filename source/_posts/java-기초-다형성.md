---
title: '[java]기초 - 다형성'
date: 2018-05-03 22:44:28
tags: java
category:
- java
---


자바에서 다형성(Polymorphism)의 쓰임을 알아본다.


다형성(Polymorphism) - 다양한 동작

다형성은 기본적으로 다양한 형태의 성질을 가진다는 의미를 가지고 있다.
기본적으로 자바는 다형성을 그 특징으로 가지는 객체 지향 프로그래밍 언어이며,
자바에서는 이 다형성을 이용하여 객체를 사용할 때 사용하는 변수 형태를 바꾸어 여러 타입의 객체를 참조할 수 있다.

결과적으로 이러한 다형성의 개념을 적절하게 이용할 때 프로그램의 소스 코드를 유연하게 구성할 수 있습니다.

다형성은 부모 클래스 타입의 참조 변수로 하위 클래스의 객체를 참조할 수 있게 해준다.




## 과일 정보 프로젝트 구현



Fruit.java
```java 

public class Fruit {
    String name;
    int price;
    int fresh;
    
    public void show() {
        System.out.println("이름 : " + name);
        System.out.println("가격 : " + price);
        System.out.println("신선도 : " + price);
    }
    
}


```
Peach.java
```java 
public class Peach extends Fruit {
    public Peach() {
        price = 1500;
        name = "복숭아";
        fresh = 75;
    }
}
```


Banana.java
```java 
public class Banana extends Fruit {
    public Banana() {
        price = 1000;
        name = "바나나";
        fresh = 50;
    }
}
```

Main.java
```java 
public class Main {

    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);
        System.out.print("바나나 : 1, 복숭아 : 2 ?");
        int input = scan.nextInt();

        Fruit fruit;

        if (input == 1) {
            // 부모클래스의 변수로서
            // 자신의 자식클래스의 인스턴스를 넣어줄 수 있다.
            fruit = new Banana();
            fruit.show();
        } else if (input == 2) {
            fruit = new Peach();
            fruit.show();
        }

    }

}
```
