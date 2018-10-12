---
title: '[java]기초 - 추상'
date: 2018-05-02 22:29:09
tags: java
category:
- java
---

자바 객체지향의 활용

자바에서의 객체지향을 본격적으로 활용하기 위해서는 자바의 객체지향 개념을 더욱 더 깊게 이해하고 적용할 필요가 있다.
자바에서는 C언어나 다른 원시적 프로그래밍 언어에서는 제공하지 않았던 특수한 기능을 제공한다.
대표적으로 추상(Abstract)의 개념이 있으며 그와 비슷하지만 조금 다른 개념인 인터페이스(Interface)의 개념이 존재한다.

자바에서는 이러한 다양한 설계 기법들을 제공하기 때문에 개발 자체에서의 안정성 및 확장 가능성을 보장 받을 수 있다.

※ 객체지향 :  객체는 일반적으로 말하는 물건을 의미하며 여기서 물건은 단순한 데이터가 아니고 그 데이터의 조작 방법에 대한 정보 또한 포함하고 있어 그것을 대상으로 다루는 수법을 객체지향이라고 한다.

## 추상(Abstract)

자바에서는 일종의 미완성 클래스라고 할 수 있는 추상(Abstract) 클래스를 제공합니다. 추상클래스는 직접적으로 객체 인스턴스를 생성할 수 없다. 하지만 새로운 클래스를 작성하는 데 밑바탕이 되는 역할을 해준다는 것에서 의미가 있다.
어느 정보 미리 설계로서 틀을 갖추고 클래스를 작성할 수 있게 한다는 기능적인 측면에서 의미가 있다.



추상 클래스를 사용하려면 꼭 상속을 받아야 하며 상속받은 모든 추상 메소드는 반드시 구현을 해주어야 한다.


## 추상의 개념을 이용하여 음악 플레이어 클래스를 구현합니다.


Player.java

```java 

abstract class Player {
    abstract void play(String songName);
    abstract void pause();
    abstract void stop();
}


```
Main.java

```java 

public class Main extends Player {

    public static void main(String[] args) {

        Main main = new Main();
        main.play("싸이 - 강남스타일 ");
        main.pause();
        main.stop();
    }

    @Override
    void play(String songName) {
        System.out.println(songName + "곡을 재생합니다.");
    }

    @Override
    void pause() {
        System.out.println("곡을 일시정지합니다.");
    }

    @Override
    void stop() {
        System.out.println("곡을 정지합니다.");
    }

}


```

## 추상의 개념을 이용하여 동물 클래스를 구현합니다.


Animal.java
```java 
abstract class Animal {
    abstract void crying();
}
```


Cat.java
```java 
public class Cat extends Animal{

    @Override
    void crying() {
        System.out.println("야옹야옹");
    }

}
```
Dog.java
```java 
public class Dog extends Animal{

    @Override
    void crying() {
        System.out.println("멍멍");
    }

}
```

Main.java
```java 
public class Main {

    public static void main(String[] args) {

        Dog dog = new Dog();
        Cat cat = new Cat();
        dog.crying();
        cat.crying();
    }

}
```