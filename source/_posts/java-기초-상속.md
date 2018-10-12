---
title: '[java]기초 - 상속'
date: 2018-05-02 21:31:39
tags: java
category:
- java
---

상속 = 클래스 간의 상호작용

상속이란 쉽게 말해서 다른 클래스가 가지고 있는 정보를 자신이 포함하겠다는 의미
즉, 다른 클래스에 대한 정보를 상속받아 자신이 그대로 사용할 수 있도록 한다.




## 하나의 사람을 의미하는 Person 클래스를 생성한다.

```java 

public class Person {
    private String name;
    private int age;
    private int height;
    private int weight;
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public int getHeight() {
        return height;
    }
    public void setHeight(int height) {
        this.height = height;
    }
    public int getWeight() {
        return weight;
    }
    public void setWeight(int weight) {
        this.weight = weight;
    }
    public Person(String name, int age, int height, int weight) {
        super();
        this.name = name;
        this.age = age;
        this.height = height;
        this.weight = weight;
    }
    
    
}

```

## Person을 상속받아 하나의 학생을 의미하는 Student 클래스

```java 
public class Student extends Person{
    private String studentID;
    private int garde;
    private double GPA;
    public String getStudentID() {
        return studentID;
    }
    public void setStudentID(String studentID) {
        this.studentID = studentID;
    }
    public int getGarde() {
        return garde;
    }
    public void setGarde(int garde) {
        this.garde = garde;
    }
    public double getGPA() {
        return GPA;
    }
    public void setGPA(double gPA) {
        GPA = gPA;
    }
    public Student(String name, int age, int height, int weight, String studentID, int garde, double gPA) {
        super(name, age, height, weight);
        this.studentID = studentID;
        this.garde = garde;
        GPA = gPA;
    }
    
    public void show() {
        System.out.println("----------------------------");
        System.out.println("학생이름 : " + getName());
        System.out.println("학생나이 : " + getAge());
        System.out.println("학생키 : " + getHeight());
        System.out.println("학생몸무게: " + getWeight());
        System.out.println("학생 학번 : " + getStudentID());
        System.out.println("학생 학년 : " + getGarde());
        System.out.println("학생 학점 : " + getGPA());
    }
}

```

## Student 클래스를 이용하여 객체를 생성

```java 

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Student student1 = new Student("초보자", 20,174,40,"20180502", 1, 4.5);
        Student student2 = new Student("신규자", 20,180,90,"20180503", 2, 3.0);
        
        student1.show();
        student2.show();
    }
```

## Person을 상속받아 하나의 선생님을 의미하는 Teacher 클래스 

```java 
public class Teacher extends Person{
    private String teacherID;
    private int monthSalary;
    private int workedYear;
    public String getTeacherID() {
        return teacherID;
    }
    public void setTeacherID(String teacherID) {
        this.teacherID = teacherID;
    }
    public int getMonthSalary() {
        return monthSalary;
    }
    public void setMonthSalary(int monthSalary) {
        this.monthSalary = monthSalary;
    }
    public int getWorkedYear() {
        return workedYear;
    }
    public void setWorkedYear(int workedYear) {
        this.workedYear = workedYear;
    }
    
    
    public Teacher(String name, int age, int height, int weight, String teacherID, int monthSalary, int workedYear) {
        super(name, age, height, weight);
        this.teacherID = teacherID;
        this.monthSalary = monthSalary;
        this.workedYear = workedYear;
    }
    
    
    public void show() {
        System.out.println("----------------------------");
        System.out.println("교사이름 : " + getName());
        System.out.println("교사나이 : " + getAge());
        System.out.println("교사키 : " + getHeight());
        System.out.println("교사몸무게: " + getWeight());
        System.out.println("교사 직원번호 : " + getTeacherID());
        System.out.println("교사 월급 : " + getMonthSalary());
        System.out.println("교사 연차 : " + getWorkedYear());
    }
    
    
}

```

## 데이터를 입력받은 데이터를 배열을 이용하여 저장하고 출력하는 연습

```java 
   public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);
        System.out.print("총 몇 명의 학생이 존재합니까? ");
        int number = scan.nextInt();
        Student[] students = new Student[number];
        for (int i = 0; i < number; i++) {
            String name;
            int age;
            int height;
            int weight;
            String studentID;
            int garde;
            double gPA;

            System.out.println("학생의 이름을 입력하세요 : ");
            name = scan.next();
            System.out.println("학생의 나이를 입력하세요 : ");
            age = scan.nextInt();
            System.out.println("학생의 키를 입력하세요 : ");
            height = scan.nextInt();
            System.out.println("학생의 몸무게를 입력하세요 : ");
            weight = scan.nextInt();
            System.out.println("학생의 학번을 입력하세요 : ");
            studentID = scan.next();
            System.out.println("학생의 학년을 입력하세요 : ");
            garde = scan.nextInt();
            System.out.println("학생의 학점을 입력하세요 : ");
            gPA = scan.nextDouble();

            students[i] = new Student(name, age, height, weight, studentID, garde, gPA);
            System.out.println();
            System.out.println("----------------------------------------");
            System.out.println();
        }

        for (int i = 0; i < number; i++) {
            students[i].show();
        }

        // TODO Auto-generated method stub
        Student student1 = new Student("초보자", 20, 174, 40, "20180502", 1, 4.5);
        Student student2 = new Student("신규자", 20, 180, 90, "20180503", 2, 3.0);

        student1.show();
        student2.show();

        Student[] student = new Student[100];
        for (int i = 0; i < 100; i++) {
            student[i] = new Student("초보자", 20, 174, 40, i + " ", 1, 4.5);
            student[i].show();
        }

        Teacher teacher1 = new Teacher("선생님1", 20, 174, 40, "teacher1", 10000000, 5);
        Teacher teacher2 = new Teacher("선생님2", 20, 174, 40, "teacher2", 20000000, 6);

        teacher1.show();
        teacher2.show();
    }

}
```