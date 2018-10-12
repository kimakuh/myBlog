---
title: '[java]기초 - final'
date: 2018-05-03 21:09:17
tags: java
category:
- java
---

Final 의 쓰임

자바에서 절대 변하지 않는 특정한 것을 정하고 싶을 때는 Final을 사용
이 키워드는 변수, 메소드, 클래스에 모두 사용할 수 있다.
변수에 사용할 경우 변하지 않는 상수
메소드가 사용할 때는 재정의가 불가능한 메소드
클래스에서 사용할 때는 상속이 불가능한 하나의 완전한 클래스

값이 바뀌는 것을 막는다.
한번 정의되면 다시 바뀌지 않는 메소드

최종적으로 규정한다 혹은 정한다.

## Final 키워드를 사용한 변수를 다룬다.



```java 

    public static void main(String[] args) {
        final int number = 10; // 상수를 정의한다.
        //number = 5; // 오류가 발생한다.
        System.out.println(number);
    } 

```

## Final 키워드를 사용한 메소드를 다룬다.


Parent.java
```java 

public class Parent {
    public void show() {
        System.out.println("Hi");
    }
}

```

Main.java

```java 

public class Main extends Parent {

    // 함수 재정의 ==> 다시 정의한다.
    // 자신의 부모클래스에서 존재하는 show()라는 함수는 지워버리고
    // 자신의 클래스에서 재정의 된(오버라이딩) 함수를 실행한다.
    public void show() {
        System.out.println("Hello");
    }

    public static void main(String[] args) {

        Main main = new Main();
        main.show();
    }

}
```

하지만 Parent에 아래와 같이 final을 붙이면


Parent.java 


```java 

public class Parent {
    public final void show() {
        System.out.println("Hi");
    }
}

```
Main 클래스에서 오류가 발생한다. ==> 오버라이딩 불가 ==> 함수의 재정의를 막는다.

```java 

public class Main extends Parent {

    // 함수 재정의 ==> 다시 정의한다.
    // 자신의 부모클래스에서 존재하는 show()라는 함수는 지워버리고
    // 자신의 클래스에서 재정의 된(오버라이딩) 함수를 실행한다.
    public void show() {
        System.out.println("Hello");
    }

    public static void main(String[] args) {

        Main main = new Main();
        main.show();
    }

}
```





## Final 키워드를 사용한 클래스를 다룬다.

기존에 만들어진 Parent 클래스에 public 대신 final을 붙인다.

```java 
final class Parent {
    public final void show() {
        System.out.println("Hi");
    }
}

```
위와 같이 바꿔주면 메인클래스에서 오류가 발생한다.

final로 정의된 클래스를 상속 받고자 했기 때문이다. ==> 상속 불가

클래스명에 final이 붙게 된다면 그 클래스는 더 이상 어떠한 클래스에서도 상속이 불가능 하다.
