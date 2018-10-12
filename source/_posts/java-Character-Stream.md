---
title: '[java] Character Stream'
date: 2018-04-11 19:19:48
tags: java
category:
- java
---

자바의 입출력

## Character Stream - 문자 단위로 출력하기

```java
    public static void main(String[] args) throws Exception {
        // 1) 문자 단위로 출력할 도구 준비
        FileWriter out = new FileWriter("temp/test2.txt");
        
        // 2) 문자 출력하기
        // => 자바는 문자 데이터를 다룰 때 UTF-16(2바이트) 유니코드를 사용한다.
        // => 그래서 출력할 때 UTF-16 2바이트 유니코드값을 
        //    JVM에 설정된 기본 문자코드표의 값으로 변환하여 출력한다.
        // => JVM을 실행할 때 출력 데이터의 문자 코드표를 지정하지 않으면 
        //    OS의 기본 문자코드표에 따라 변환한다.
        //    예) Windows OS(MS949), Unix(UTF-8)
        // => JVM을 실행할 때 출력 데이터의 문자 코드표를 지정하는 방법
        //    > java -Dfile.encoding=문자코드표 -cp 클래스경로 클래스명
        // 
        // => 따라서 다음 4바이트 값을 출력하면 
        //    앞의 2바이트는 버리고, 뒤의 2바이트(UTF-16)를 UTF-8 코드표에 따라 
        //    1 ~ 4 바이트 값으로 변환하여 출력한다.
        out.write(0x7a6bac00); 
        
        out.close();
        
        System.out.println("출력 완료!");
        
    }
```

## Character Stream - 문자 단위로 읽기

```java
    public static void main(String[] args) throws Exception {
        // 1) 파일의 데이터를 읽을 객체를 준비한다. 
        FileReader in = new FileReader("temp/test2.txt");
        
        // 2) JVM에 설정된 문자코드표에 따라 바이트를 읽어서 UTF-16으로 바꾼 후에 리턴한다.
        // => 리턴 값은 2바이트 UTF-16의 코드 값이다.
        // => JVM에 설정된 문자코드표가 UTF-8이면 1 ~ 4 바이트까지 
        //    문자에 따라 가변적으로 읽어들이다.
        //    즉 영어 문자는 1바이트를 읽어 2바이트 UTF-16 코드 값으로 바꿀 것이다.
        //    한글 문자는 3바이트를 읽어 2바이트 UTF-16 코드 값으로 바꿀 것이다.
        //    문자에 따라 읽는 바이트의 개수가 다르다는 것이다.
        // => 이것이 FileInputStream의 read() 메서드와 다른 점이다.
        //    FileInputStream의 read()는 무조건 1바이트를 읽는다.
        //    그리고 값을 변환하지 않는다.
        // => FileReader의 read()는 문자에 따라 1 바이트에서 4 바이트까지 
        //    읽는 바이트 수가 다른다. 
        //    리턴 값도 읽을 값을 그대로 리턴하는 것이 아니라 UTF-16 코드 값으로 변경하여 
        //    리턴한다. 
        //    왜? JVM에서 문자를 UTF-16 코드 값으로 다루기 때문이다.
        // => 그래서 이미지 파일이나 동영상 파일과 같이 바이너리 데이터는 
        ///   FileReader를 사용하여 읽어서는 안된다.
        //    왜? 문자라고 간주하고 값을 변경하기 때문이다.
        int ch = in.read(); 
        
        // 3) 읽기 도구를 닫는다.
        in.close();
        
        System.out.printf("%x\n", ch);
    }
```

## Character Stream - 문자 배열 출력하기

```java
    public static void main(String[] args) throws Exception {
        FileWriter out = new FileWriter("temp/test2.txt");
        
        char[] chars = new char[] {'A','B','C','가','각','간','똘','똥'}; 
        
        out.write(chars); // 문자 배열 전체를 출력한다.
        // 당연히 UTF-16을 JVM 기본 문자 코드표에 따라 변환하여 출력한다.
        // JVM이 입출력 문자 코드표로 UTF-8을 사용한다면
        // 영어는 1바이트로 변환되어 출력될 것이고,
        // 한글은 3바이트로 변환되어 출력될 것이다.
        
        out.close();
        
        System.out.println("데이터 출력 완료!");

    }
```

## Character Stream - 문자 배열 읽기

```java
    public static void main(String[] args) throws Exception {
        FileReader in = new FileReader("temp/test2.txt");
        
        // UTF-16 문자 코드 값을 저장할 배열을 준비한다.
        // => 이렇게 임시 데이터를 저장하기 위해 만든 바이트 배열을 보통 "버퍼(buffer)"라 한다.
        char[] buf = new char[100];
        
        // read(버퍼의주소)
        // => 버퍼가 꽉 찰 때까지 읽는다.
        // => 물론 버퍼 크기보다 파일의 데이터가 적으면 파일을 모두 읽어 버퍼에 저장한다.
        // => 리턴 값은 읽은 바이트의 개수이다.
        // => 파일을 읽을 때 JVM의 문자코드표에 따라 바이트를 읽는다.
        //    그리고 2바이트 UTF-16 코드 값으로 변환하여 리턴한다.
        // => JVM의 문자코드표가 UTF-8이라면,
        //    파일을 읽을 때, 영어나 숫자, 특수기호는 1바이트를 읽어 UTF-16으로 변환할 것이고
        //    한글은 3바이트를 읽어 UTF-16으로 변환할 것이다.
        int count = in.read(buf); 
        
        in.close();
        
        System.out.printf("%d\n", count);
        for (int i = 0; i < count; i++)
            System.out.printf("%c(%x) ", buf[i], (int)buf[i]);
        
        System.out.println();

    }
```

## Character Stream - 문자 배열의 특정 부분을 출력하기

```java
    public static void main(String[] args) throws Exception {
        FileWriter out = new FileWriter("temp/test2.txt");
        
        char[] chars = new char[] {'A','B','C','가','각','간','똘','똥'}; 
        
        out.write(chars, 2, 3); // 2번 문자부터 3 개의 문자를 출력한다.
        
        out.close();
        
        System.out.println("데이터 출력 완료!");

    }
```

## Character Stream - 읽은 데이터를 문자 배열의 특정 위치에 저장하기

```java
    public static void main(String[] args) throws Exception {
        FileReader in = new FileReader("temp/test2.txt");
        
        char[] buf = new char[100];
        
        // read(버퍼의주소, 저장할위치, 읽을바이트개수)
        // => 리턴 값은 실제 읽은 문자의 개수이다.
        int count = in.read(buf, 10, 40); // 40개의 문자를 읽어 10번 방부터 저장한다. 
        
        in.close();
        
        System.out.printf("%d\n", count);
        for (int i = 10; i < (count + 10); i++)
            System.out.printf("%c(%x) ", buf[i], (int)buf[i]);
        
        System.out.println();

    }
```