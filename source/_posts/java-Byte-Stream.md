---
title: '[java] Byte Stream'
date: 2018-04-11 19:02:19
tags: java
category:
- java
---

자바의 입출력


## Byte Stream - 바이트 단위로 출력하기 

```java
public static void main(String[] args) throws Exception {
        // 1) 파일로 데이터를 출력하는 객체를 준비한다. 
        FileOutputStream out = new FileOutputStream("temp/test1.data");
        
        // 2) 1바이트를 출력한다.
        // => int 값을 아규먼트로 넘기더라도 맨 마지막 1바이트만 출력한다.
        out.write(0x7a6b5c4d); // 출력하는 값은 0x4d 이다.
        
        // 3) 출력 도구를 닫는다.
        // => 항상 입출력 도구를 사용한 후 닫아야 한다.
        // => 어떤 입출력 도구는 닫지 않으면 버퍼(임시메모리)에 남아있는 데이터가 
        //    출력되지 않고 버려진다.
        out.close();
        
        System.out.println("데이터 출력 완료!");

    }
```

## Byte Stream - 바이트 단위로 읽기 

``` java
    public static void main(String[] args) throws Exception {
        // 1) 파일의 데이터를 읽을 객체를 준비한다. 
        FileInputStream in = new FileInputStream("temp/test1.data");
        
        // 2) 1바이트를 읽는다.
        // => read() 메서드의 리턴 타입이 int 라 하더라도 1바이트를 읽어 리턴한다.
        int b = in.read(); // 읽은 값은 0x4d 이다.
        
        // 3) 읽기 도구를 닫는다.
        in.close();
        
        System.out.printf("%x\n", b);

    }
```

## Byte Stream - 바이트 배열 출력하기 

``` java
    public static void main(String[] args) throws Exception {
        FileOutputStream out = new FileOutputStream("temp/test1.data");
        
        byte[] bytes = new byte[] {0x7a, 0x6b, 0x5c, 0x4d, 0x3e, 0x2f, 0x30};
        
        out.write(bytes); // 바이트 배열 전체를 출력한다.
        
        out.close();
        
        System.out.println("데이터 출력 완료!");

    }
```

## Byte Stream - 바이트 배열 읽기

``` java
    public static void main(String[] args) throws Exception {
        FileInputStream in = new FileInputStream("temp/test1.data");
        
        // 바이트들을 저장할 배열을 준비한다.
        // => 이렇게 임시 데이터를 저장하기 위해 만든 바이트 배열을 보통 "버퍼(buffer)"라 한다.
        byte[] buf = new byte[100];
        
        // read(버퍼의주소)
        // => 버퍼가 꽉 찰 때까지 읽는다.
        // => 물론 버퍼 크기보다 파일의 데이터가 적으면 파일을 모두 읽어 버퍼에 저장한다.
        // => 리턴 값은 읽은 바이트의 개수이다.
        int count = in.read(buf); 
        
        in.close();
        
        System.out.printf("%d\n", count);
        for (int i = 0; i < count; i++)
            System.out.printf("%x ", buf[i]);
        
        System.out.println();

    }
```

## Byte Stream - 바이트 배열의 특정 부분을 출력하기

``` java
    public static void main(String[] args) throws Exception {
        FileOutputStream out = new FileOutputStream("temp/test1.data");
        
        byte[] bytes = new byte[] {0x7a, 0x6b, 0x5c, 0x4d, 0x3e, 0x2f, 0x30};
        
        out.write(bytes, 2, 3); // 2번 데이터부터 3 바이트를 출력한다.
        
        out.close();
        
        System.out.println("데이터 출력 완료!");

    }
```

## Byte Stream - 읽은 데이터를 바이트 배열의 특정 위치에 저장하기

``` java
    public static void main(String[] args) throws Exception {
        FileInputStream in = new FileInputStream("temp/test1.data");
        
        byte[] buf = new byte[100];
        
        // read(버퍼의주소, 저장할위치, 읽을바이트개수)
        // => 리턴 값은 실제 읽은 바이트의 개수이다.
        int count = in.read(buf, 10, 40); // 40바이트를 읽어 10번 방부터 저장한다. 
        
        in.close();
        
        System.out.printf("%d\n", count);
        for (int i = 10; i < (count + 10); i++)
            System.out.printf("%x ", buf[i]);
        
        System.out.println();

    }
```