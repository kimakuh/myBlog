---
title: '[java]기초 - 객체지향의 활용'
date: 2018-05-04 23:24:20
tags: java
category:
- java
---

객체지향의 활용
문법을 이해한다고해서 프로그램을 작성할 수 있는것은 아니다.

객체지향 기법의 활용


## 게임 캐릭터 공격 프로젝트 구현

Hero.java

```java 

public class Hero {
    String name;

    public Hero(String name) {
        this.name = name;
    }

    public void attack() {
        System.out.println("기본 공격");
    }
}

```


Warrior.java

```java 

public class Warrior extends Hero {

    public Warrior(String name) {
        super(name); // 부모클래스의 생성자
    }
    
    public void WarriorAttack() {
        System.out.println("후려치기");
    }

}


```


Archer.java

```java 

public class Archer extends Hero {

    public Archer(String name) {
        super(name);
    }

    public void ArcherAttack() {
        System.out.println("활쏘기");
    }

}



```


Wizard.java

```java 

public class Wizard extends Hero{

    public Wizard(String name) {
        super(name);
    }
    
    public void WizardAttack() {
        System.out.println("얼리기");
    }

}


```



Main.java

```java 

public class Main {

    public static void main(String[] args) {
        Hero[] heros = new Hero[3];
        heros[0] = new Warrior("전사");
        heros[1] = new Archer("궁수");
        heros[2] = new Wizard("마법사");

        for (int i = 0; i < heros.length; i++) {
            heros[i].attack();

            if (heros[i] instanceof Warrior) {
                Warrior temp = (Warrior) heros[i];
                temp.WarriorAttack();
            } else if (heros[i] instanceof Archer) {
                Archer temp = (Archer) heros[i];
                temp.ArcherAttack();
            } else if (heros[i] instanceof Wizard) {
                Wizard temp = (Wizard) heros[i];
                temp.WizardAttack();
            }
        }
    }

}



```