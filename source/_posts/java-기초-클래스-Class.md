---
title: '[java]기초 - 클래스(Class)'
date: 2018-04-22 22:05:38
tags: java
category:
- java
---

클래스는 객체 지향 프로그래밍에 있어서 가장 기본이 되는 것.
클래스를 이용하여 현실 게계의 특정한 물건을 지칭할 수 있다.
가장 많이 사용되는것이 Node클래스.
개발 프로젝트에서는 하나의 처리할 데이터 단위를 명시하는데 사용되기도 한다.

하나의 틀
어떤 특징 혹은 속성을 가진 변수를 만들어서 사용할 수 있도록하는것 => 인스턴스화 =>인스턴스로 만든다.

객체 : 실제 세계의 사물




## Node 클래스를 이용하여 두 점 사이의 중점을 구하는 프로그램

```java 
Node.java

public class Node {

    private int x;
    private int y;

    // Node 라는것은 좌표를 의미
    // x와 y의 값을 외부에서 바꿀 수 없도록 private 사용

    public int getX() { // public을 사용해서 외부에서 getX()에 접근하도록 한다.
        return x;
    }

    public void setX(int x) { // x의 값을 설정하는 함수
        this.x = x; // 기존에 가지고있는 x의 값을 현재 매개변수 x 로 값을 변경
    }

    public int getY() { // public을 사용해서 외부에서 getY()에 접근하도록 한다.
        return y;
    }

    public void setY(int y) { // y의 값을 설정하는 함수
        this.y = y; // 기존에 가지고있는 y의 값을 현재 매개변수 y 로 값을 변경
    }

    // 생성자
    public Node(int x, int y) { // 인스턴스 즉 객채를 하나 만들어줄때
                                // 자동으로 값들을 초기화 해주는 함수

        this.x = x;
        this.y = y;
        // Node 라는 인스턴스 변수를 만들어줌과 동시에
        // x 와 y 의 값을 초기화 해준다.
    }

    public Node getCenter(Node other) { // getCenter는 다른 Node를 매개변수로 받는다.
                                        // 즉 다른 Node와 비교해서
                                        // 자신이 가지고있는 x,y 좌표와 다른 Node가 가지고있는
                                        // x,y 좌표를 비교해서 정확히 정중앙을 가지는
                                        // 좌표를 반환한다.

        return new Node((this.x + other.getX()) / 2, (this.y + other.getY()) / 2);

    }
}

```


```java 
Main.java

    public static void main(String[] args) {
        Node one = new Node(10, 20);
        Node two = new Node(30, 40);

        Node result = one.getCenter(two);
        
        System.out.println("x는 " + result.getX());
        System.out.println("y는 " + result.getY());

    }

```