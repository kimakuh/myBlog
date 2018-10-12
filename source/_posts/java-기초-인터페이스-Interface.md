---
title: '[java]기초 - 인터페이스(Interface)'
date: 2018-05-03 21:36:42
tags: java
category:
- java
---

인터페이스 (Interface) - 설계의 본질

인터페이스(Interface)는 얼핏 보기에는 추상(Abstract) 클래스와 매우 흡사한 개념으로 느껴질 수 있다.
인터페이스는 숙련된 자바 개발자들에게 아주 선호되는 설계 기능이면서 자바에서 다중 상속을 구현하게 해주는 고급 기술이다.
추상클래스는 추상 메소드 외에 맴버 변수나 일반 메소드를 가질 수 있지만
인터페이스에서는 반드시 사전에 정의된 추상 메소드와 상수만을 가질 수 있다는 특징이 있다.

인터페이스는 팀 프로젝트의 동시 작업에 유리하고 일반적으로 추상보다 요구되는 설계의 기준이 높아서 더 체계적이라고 평한다.



기본적으로 자바에서는 다중상속 구현이 불가하다. 즉 하나의 클래스가 여러개의 클래스에서 상속을 받는것이 불가하다.
하지만 인터페이스를 사용하면 다중상속 구현이 가능하다.

인터페이스는 설계만 하는 것이다.


인터페이스는 추상클래스보다 더 엄격한 설계


## 인터페이스를 선언하고 메소드를 다루어본다.

Dog.java

```java 

public interface Dog {
    abstract void crying();

    public void show() { // 오류가 발생한다.
                         // 인터페이스는 미리 일반 메서드를 가지는 것을 막아놓았다.
                         // 즉 인터페이스 안에서는 설계만 가능하다.
                         // 아래와 같이 실질적인 코드를 작성하면 오류가 발생한다.
        System.out.println("Hello");
    }
}

```


하지만 위의 클래스를 추상클래스로 바꾸어주면 오류가 발생하지 않는다.

```java 

abstract class Dog {
    abstract void crying();

    public void show() { // 오류가 발생한다.
                         // 인터페이스는 미리 일반 메서드를 가지는 것을 막아놓았다.
                         // 즉 인터페이스 안에서는 설계만 가능하다.
                         // 아래와 같이 실질적인 코드를 작성하면 오류가 발생한다.
        System.out.println("Hello");
    }
}

```


따라서 인터페이스를 사용하려면 아래와 같이 어떤 함수가 존재하는지만 알려줘야한다.
즉, 설계만 가능하다.

Dog.java
```java 

public interface Dog {
    abstract void crying();
    public void show();
}

```
Main.java

```java 

public class Main implements Dog { // 인터페이스는 implements를 사용

    public static void main(String[] args) {
        Main main = new Main();
        main.crying();
        main.show();
    }

    @Override
    public void crying() {
        System.out.println("멍멍");
    }

    @Override
    public void show() {
        System.out.println("강아지가 짖는다.");
    }

}

```




## 인터페이스의 다중 상속에 대하여 학습한다.


Dog.java
```java 
abstract class Dog {
    abstract void crying();

}

```

Cat.java

```java 
abstract class Cat {
    abstract void crying();

}
```


아래와 같이 Dog와 Cat을 둘다 상속받으려고 하면 오류가 발생한다.
==>다중상속 불가

Main.java

```java 
public class Main extends Dog, Cat {

    public static void main(String[] args) {
        Main main = new Main();
        main.crying();
    }

    @Override
    public void crying() {
        System.out.println("멍멍");
    }
}
```


인터페이스를 사용하여 다중상속을 구현해 본다.


Dog.java
```java 
public interface Dog {
    abstract void crying();
}

```

Cat.java

```java 
public interface Cat {
    abstract void crying();
}
```


아래와 같이 인터페이스를 사용하면 Dog와 Cat을 둘다 상속 받더라도
오류가 발생하지 않는다.

Main.java
```java 
public class Main implements Dog, Cat {

    public static void main(String[] args) {
        Main main = new Main();
        main.crying();
   
    }

    @Override
    public void crying() {
        System.out.println("멍멍");
    }
}

```


※ 설계된 모든 메서드들을 다 구현해야 한다. 하나라도 구현하지 않으면 오류가 발생한다.



