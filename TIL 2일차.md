# TIL 2일차

강의 번호: JAVA
복습: No
유형: 강의기록
작성일시: 2022년 4월 26일 오전 9:06

# 객체 지향 프로그래밍(OOP:Object Oreiented Prigramming)

절차 지향 프로그래밍과는 다른 방식의 프로그래밍 방법론을 의미한다. 사용자의 요구 사항이 변경될 경우 발생하는 문제들을 효과적으로 다룰 수 있다는 장점이 있음.

## 1.객체?

### 주체(Subject) 와 객체(Object)

나는 주체, 객체는 나를 제외한 모든 것을 의마한다.

다른 사람 입장에서는 내가 객체가 된다.

---

## 2. 기존의 프로그래밍 패러다임은?

### 2-1. 절차 지향 프로그래밍

기본 사상과 지향점 : 함수를 통해 코드를 논리적인 단위로 구분/ 분할/ 정복한다.

### 2-2. 객체 지향 프로그래밍

세상에 존재하는 모든 것은 사물이다.

기본 사상과 지향점 : 현실 세계에서 사람이 사물을 인지하는 방식처럼 프로그래밍한다.

각각의 사물은 고유한(instance) 값을 가진다.

```java
class Person { // 모든 객체(class)는 속성과 행위(기능)을 가지고 있다.
	String name; // 속성, Member field

	public void work() { // 행위(기능), Member Method
		System.out.println(name + "이(가) 걷고 있습니다.");
	}
}

Person y = new Person("Yoo");  //사람 객체 생성, y에는 "Yoo"라는 고유한(instance) '사람'이 들어있다.
Peron h = new Person("Hong");

System.out.println(y == h); //false, 서로 다른 '사람'이기 때문에 같지 않다.
```

---

다른 예시로 연습해보자.

강아지(개) 클래스

속성: age, color, weight

행위(Method): 움직인다, 사료를 먹는다, 잔다.

```java

class Dog{
	String name;
	int age;
	String color;
	double weight;

	public Dog(String name, int age, String color, double weight){
	this.name = name;
	this.age = age;
	this.color = color;
	this.weight = weight;
	}

	public void run(){
	System.out.println(name + " 달려!");
	}	

	public void eat(){
	System.out.println(name + "사료를 먹는다.");
	}

	public void sleep(){
	System.out.println(name + " 잔다..");
	}

}
```

 객체 생성

인스턴스를 생성하기 위해서는 new 키워드와 함께 클래스 명()을 기술한다.

new 클래스명 (꽁치,2,검정,5); ⇒ 하나의 인스턴스가 된다.

Dog 타입의 변수인 꽁치ㅔ 생성한 인스턴스 값을 할당한다.

---

> 클래스: 어떤 객체를 생성하기 위한 설계도, 설계도가 없으면 객체나 인스턴스를 생성할 수 없다. 객체에 비해 상대적으로 더 추상적인 레벨의 개념
> 

> 객체(object): 클래스에 비해 상대적으로 구체적인 레벨에서 이야기할 때
> 

> 인스턴스(instance): 해당 클래스를 통해 실제로 생성된 고유한(세상에 유일무이하게 존재하는) 값 그 자체를 의미한다.
> 

---

# 주제: 클래스와 객체?

사람은 사물을 하나하나 개별적으로 이해하지 않고 공통된 부분끼리 묶어서 분류(Classification)할 수 있다.

→ 인간이 가진 주의력의 한계를 가지고 있기 때문.

내가 어떤 객체를 만들기 위해서는 객체들의 공통적인 분류체계를 지정해야한다.

```java
class Human //사람이라는 클래스
	String name;
	int age; //클래스가 공통적으로 가질 속성(필드)들

Human a = new Human {"윤종섭", 34}; //클래스 내에서 {}속성을 가진 새로운 instance를 만들 수 있게 됨.
Human b = new Dog {"꽁치", 3}; //사람이라는 클래스에는 같은 속성을 가졌으나 Dog라는 클래스는 없기 때문에 새로운 instance를 만들 수 없다.

//클래스는 분류에 대한 개념일 뿐 실체하지 않는다. 객체(인스턴스)는 실체한다.
```

# 강사님 정리

---

예시 - 사람과 강아지의 상호작용.

new Person();

new Dog();

사람이 개에게 앉아!라고 명령할 수 있음.

강아지 객체가 가지고 있는 메서드(sit();)을 사람이 호출할 수 있도록 구성한다면

메서드를 통해서 사람과 개가 서로 통신, 협력(메시지를 주고 받고 있음)

→ 객체의 ‘협력’을 이뤄낼 수 있다.

---

# 나만의 정리

객체지향프로그래밍의 기본 목적은, 내가 일을 편하게 하기 위함이다. 

코드를 간결하게(객체 생성, 속성 부여, 메소드 관리) 할 수도 있다. 문제점들을 해결하기 위해서 컴퓨터라는 가상의 공간 안에서 구현 한 뒤 동작하는 데 있어서 객체 간에 **상호작용** 할 수 있도록 환경을 구성하는 것.
