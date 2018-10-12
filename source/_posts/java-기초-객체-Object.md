---
title: '[java]기초 - 객체(Object)'
date: 2018-05-04 23:03:59
tags: java
category:
- java
---

객체(Object) - 모든 객체의 조상

객체(Object) 클래스는 모든 객체의 조상으로서 쓰인다. 자바에서 사실 모든 클래스는 암시적으로 Object 클래스를 상속 받고 있다. 그런 이유로 Object 클래스는 모든 클래스의 조상이라고 할 수 있다. 이러한 클래스가 존재하는 이유는 모든 클래스가 공통으로 포함하고 있어야 하는 기능을 제공하기 위함이다.


객체(Object) 클래스에 대해서 이해하자

## 객체를 비교하는 방법을 알아본다.

Archer.java

```java 

public class Archer { // Archer 가 Object를 상속받는다고
                      // 명시해 주지 않아도
                      // 상속받도록 설정되어 있다.
                      //  ==> Archer는 항상 Object의 자식클래스이다.
    String name;
    String power;

    public Archer(String name, String power) {
        this.name = name;
        this.power = power;
    }

    public boolean equals(Object obj) { // 다형성
        Archer temp = (Archer) obj;
        if(name == temp.name && power == temp.power) {
            return true;
        } else {
            return false;
        }
    }
}

```

Main.java

```java 

public class Main {

    public static void main(String[] args) {
        Archer archer1 = new Archer("궁수1", "상");
        Archer archer2 = new Archer("궁수2", "중");
        System.out.println(archer1 == archer2);
        
        Archer archer3 = new Archer("궁수1", "상");
        Archer archer4 = new Archer("궁수1", "상");
        System.out.println(archer3 == archer4);
        // 두 개의 인스턴스가 내부적으로 가지고 있는 값이 같더라도
        // 인스턴스의 값이 아닌 인스턴스 자체를 비교하기 때문에
        // false가 나온다
        
        Archer archer5 = new Archer("궁수1", "상");
        Archer archer6 = new Archer("궁수1", "상");
        System.out.println(archer5.equals(archer6));
        
        // 두 인스턴스가 내부적으로 가지는 변수의 값을 비교하기 때문에
        // true
        
    }

}

```