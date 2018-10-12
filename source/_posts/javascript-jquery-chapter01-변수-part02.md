---
title: '[javascript & jquery] - chapter01 변수_part02'
date: 2018-05-29 16:21:47
tags:
- javascript  
- jquery
category:
- javascript  
---

# Lesson04 변수의 값 저장 및 변경
## 변수 값 저장
변수에는 상수뿐 아니라 또 다른 변수 자체를 저장할 수 있다.

```javascript
[문법]
var 변수A = 데이터; // 데이터가 변수A에 저장된다.
var 변수B = 변수A;  // *변수B에 변수A에 들어있는 값이 복사돼 저장
```
### 변수 data1을 만든 후 숫자 데이터 1234를 저장, 변수 data2를 만든 후 data1의 값을 저장
```javascript
var data1 = 1234;
var data2 = data1;  
```

## 변수 값 변경
var을 붙이지 않은 상태에서 변수에 값을 대입해주면 변수의 값이 변경된다.

```javascript
[문법]
var 변수이름 = 데이터;
변수이름 = 신규 데이터1;
변수이름 = 신규 데이터2;
```
### 변수 data1을 만든 후 초깃값을 10으로 한 후, 데이터를 다시 20으로 또 다시 한번 30으로 변경
```javascript
var data1 = 10;
data1 = 20;  
data1 = 30;
```

# Lesson05 변수의 값이 자동으로 읽혀지는 경우
* 우측에 변수를 두는 경우
* 함수 호출 시 변수를 매개변수(파라미터) 값으로 사용하는 경우
* 연산자와 함께 사용하는 경우

### 우측에 변수를 두는 경우(변수에 들어있는 값이 읽혀 다른 변수에 대입하는 경우)

```javascript
[문법]
변수A = 변수B(우측에 있을 때)
```

우측에 변수를 두면 변수 자체가 넘어가는 것이 아니라 변수 안에 들어 있는 데이터가 복사되어 좌측 변수에 저장된다.

* 정확히는 변수 안에 들어 있는 데이터 중 숫자, 문자, 논리 데이터만이 복사되며 배열, 함수, 객체 데이터 등은 실제 데이터가 들어있는 주소가 복사된다.

### 아래의 구문을 해석하기
```javascript
var name ="java"
var temp = name;
```
name 변수에 들어있는 "java"라는 값이 복사 되어 temp 변수에 대입된다.

### 함수 호출 시 변수를 매개변수 값으로 사용하는 경우
```javascript
[문법]
함수(변수);
```

함수 호출과 함께 변수를 사용하는 경우에도 값이 복사되어 매개변수(파라미터)로 넘어 간다.

### 아래의 구문을 해석하기
```javascript
function test1(userName){
   alert("userName =" + userName);
}

var name = "java";
test1(name);
```
test1(name); 을 호출하면 test1("java")로 변경된다.
