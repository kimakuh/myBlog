---
title: '[java]기초 - 기본 입출력(Input & Output)'
date: 2018-04-22 10:56:29
tags: java
category:
- java
---

사용자와 상호작용
입력 받은 자료는 내부적으로 어떠한 처리를 한 뒤에 다시 사용자에게 그 값을 반환할 수 있다.

프로그램이 입출력을 지원한다는 것은 사용자 인터페이스가 뛰어나다는 의미

## 기본입출력 팁

- 자바에서는 Scanner클래스만 잘 활용해도 다양한 입출력 형태를 구현할 수 있다.
- 주석은 일단 최대한 많이 작성하는 습관을 들여야 한다. 주석은 컴파일 단계에서 제거되기 때문에 프로그램의 크기와는 상관없다.
- Scanner로 문자열을 입력받고 싶을 때에는 next() 함수와 nextLine()을 적절히 활용하자.



## 특정한 정수를 입력받아서 그대로 출력하는 프로그램

```java
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in); // 자바에서 제공하는 라이브러리
                                               // (System.in) 콘솔장에서 입력하는 어떠한 데이터.
        System.out.print("정수를 입력하세요 : ");
        int i = scan.nextInt(); // 입력받은 정수를 i에 넣어준다.
        System.out.println("입력된 정수는 " + i + "입니다.");
        scan.close();
    }

```

## 파일에 차례로 입력된 모든 정수에 100을 곱해 출력하는 프로그램
```java
    public static void main(String[] args) {
        // 파일을 컨트롤할 수 있는 file변수와
        // 그 파일로 부터 직접 파일에 쓰여있는 내용을 읽어올 수 있는 scan 변수를 만든다.
        File file = new File("input.txt"); // input.txt 파일을 읽어와서 file변수가 그것을 처리할 수 있게 한다.
        try { // 파일이 없을 경우, 또는 오류상황이 발생했을때를 대비해 예외처리를 한다.
            Scanner scan = new Scanner(file); // 사용자로부터 입력받는게 아니라 파일을 통해 입력을 받는다.
            while (scan.hasNextInt()) { // scan이 읽어오고 있는 파일에서 다음으로 읽어올 정수가 있나 확인
                System.out.println(scan.nextInt() * 100); // 정수에 100을 곱하여 출력
            }
            scan.close(); 
        } catch (FileNotFoundException e) {
            System.out.println("파일을 읽어오는 도중에 오류가 발생했습니다.");
        }
    }
```
input.txt

```txt

300 30 20 49 39 227

```


## 1단부터 9단까지 구구단을 출력하는 프로그램
