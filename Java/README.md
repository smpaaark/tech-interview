# Java
* [JDK, JRE, JVM](#jdk-jre-jvm)
* [public static void main(String args[])](#public-static-void-mainstring-args)
* [Java가 플랫폼에 독립적인 이유](#java가-플랫폼에-독립적인-이유)
* [Java가 100% 객체 지향적이지 않은 이유](#java가-100-객체-지향적이지-않은-이유)
* [Wrapper 클래스](#wrapper-클래스)
* [Constructor(생성자)](#constructor생성자)
* [Singleton(싱글톤) 클래스](#singleton싱글톤-클래스)
* [ArrayList와 Vector의 차이점](#arraylist와-vector의-차이점)
* [Array와 ArrayList의 차이점](#array와-arraylist의-차이점)
* [equals()와 ==의 차이점](#equals와-의-차이점)
* [JVM의 Heap과 Stack의 차이점](#jvm의-stack과-heap의-차이점)
* [Package(패키지)](#package패키지)
* [Java에 포인터가 없는 이유](#java에-포인터가-없는-이유)
* [JIT 컴파일러](#jit-컴파일러)
* [접근 제어자(access modifier)](#접근-제어자access-modifier)
* [클래스 구조](#클래스-구조)
* [Object(객체)](#object객체)
* [객체 지향 프로그래밍(OOP, Object Oriented Programming)](#객체-지향-프로그래밍oop-object-oriented-programming)
* [로컬 변수(local variable)과 인스턴스 변수(instance variable)의 차이점](#로컬-변수local-variable과-인스턴스-변수instance-variable의-차이점)
* [final 키워드](#final-키워드)
* [break와 continue의 차이점](#break와-continue의-차이점)
* [무한 루프(infinite loop)](#무한-루프infinite-loop)
* [this()와 super()의 차이점](#this와-super의-차이점)
* [String Pool](#string-pool)
* [static 메서드와 non-static 메서드의 차이점](#static-메서드와-non-static-메서드의-차이점)
* [Constructor Chaining(생성자 체이닝)](#constructor-chaining생성자-체이닝)
* [String, StringBuilder, StringBuffer의 차이점](#string-stringbuilder-stringbuffer의-차이점)
* [Class Loader(클래스 로더)](#class-loader클래스-로더)
* [Map](#map)
* [Collection(컬렉션)](#collection컬렉션)
* [Interface(인터페이스)](#interface인터페이스)
* [Overloading(오버로딩)과 Overriding(오버라이딩)의 차이점](#overloading오버로딩과-overriding오버라이딩의-차이점)
* [Servlet(서블릿)](#servlet서블릿)
* [Get 메서드와 Post 메서드의 차이점](#get-메서드와-post-메서드의-차이점)
* [RequestDispatcher](#requestdispatcher)
* [ServletContext와 ServletConfig의 차이점](#servletconfig와-servletcontext의-차이점)
* [JDBC Driver](#jdbc-driver)
* [Java에서 데이터베이스와 연결하는 과정](#java에서-데이터베이스와-연결하는-과정)
* [JDBC API 구성요소](#jdbc-api-구성요소)
* [JDBC Batch 처리(일괄 처리)](#jdbc-batch-처리일괄-처리)
* [JDBC Statement](#jdbc-statement)
* [finalize](#finalize)
* [Exception과 Error](#exception과-error)
* [Thread(스레드)]()
* [Garbage Collector(GC, 가비지 컬렉터)]()
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## JDK, JRE, JVM
JDK
* Java Development Kit의 약자입니다.
* Java 프로그램을 컴파일, 문서화, 패키징하기 위해 필요한 도구입니다.
* JRE + 개발 도구가 포함되어 있습니다.

JRE
* Java Runtime Environment의 약자입니다.
* Java bytecode(바이트코드)를 실행할 수 있는 런타임 환경을 말합니다.
* JVM을 구현하는 것입니다.

JVM
* Java Virtual Machine의 약자입니다.
* Java bytecode(바이트코드)를 실행할 수 있는 런타임 환경을 제공하는 스펙입니다.

[맨위로](#java)

## public static void main(String args[])
main()은 Java 프로그램의 시작점입니다.   
항상 public static void main(String[] args)로 작성됩니다.   

* public
  * 접근 제어자입니다.
  * 모든 클래스에서 이 메서드에 접근할 수 있습니다.
* static
  * 클래스 인스턴스를 생성하지 않고도 접근할 수 있습니다.
  * main() 메서드가 static이 아니라면 JVM이 main()을 검색할 때 에러가 발생합니다.
* void
  * 리턴 타입입니다.
  * 값을 반환하지 않습니다.
* main
  * JVM이 애플리케이션을 시작할 때 검색하는 메서드 이름입니다.

[맨위로](#java)

## Java가 플랫폼에 독립적인 이유
Java는 운영 체제에 관계없이 모든 시스템에서 실행될 수 있는 바이트코드이기 때문에 플랫폼에 독립적이라고 합니다.   

[맨위로](#java)

## Java가 100% 객체 지향적이지 않은 이유
Java는 객체가 아닌 8가지 primitive 데이터 타입(boolean, byte, char, int, float, double, long, short)을 사용하기 때문에 100% 객체 지향적이지 않습니다.

[맨위로](#java)

## Wrapper 클래스
Wrapper 클래스는 primitive 타입을 reference 타입으로 변환합니다.   
primitive 타입을 reference 타입으로 "Wrap(랩핑)"하기 때문에 Wrapper 클래스라고 합니다.   

[맨위로](#java)

## Constructor(생성자)
객체를 초기화하는 데 사용되는 코드 블럭입니다.   
생성자는 클래스 이름과 동일해야 합니다.   
또한, 리턴 타입이 없으며 객체가 생성될 때 자동으로 호출됩니다.   

### 생성자 유형
Default Constructor(디폴트 생성자)
* 파라미터 입력값을 받지 않는 생성자입니다.
* 사용자가 정의한 다른 생성자가 없는 경우 기본적으로 생성되는 생성자입니다.   
* 주요 목적은 인스턴스 변수를 기본값으로 초기화하는 것입니다.

Parameterized Constructor(파라미터 입력값을 받는 생성자)
* 파라미터로 입력된 값으로 인스턴스 변수를 초기화할 수 있는 생성자입니다.

### 생성자와 메서드 구분하는 방법
생성자
* 객체의 상태를 초기화하는 데 사용됩니다.
* 리턴 타입이 없습니다.
* 암시적으로 호출됩니다.
* 클래스에 생성자가 없는 경우 컴파일러가 디폴트 생성자를 제공합니다.
* 생성자 이름은 항상 클래스 이름과 동일해야 합니다.

메서드
* 객체의 동작을 나타내는 데 사용됩니다.
* 리턴 타입이 있어야 합니다.
* 명시적으로 호출해야 합니다.
* 컴파일러가 디폴트 메서드를 제공하지 않습니다.
* 메서드 이름은 클래스 이름과 같을 수도 있고 같지 않을 수도 있습니다.

### Copy Costructor(복사 생성자)
복사 생성자는 같은 클래스인 다른 객체를 사용하여 객체를 초기화하는 생성자입니다.   
Java에서는 모든 객체가 참조로 전달되기 때문에 복사 생성자가 필요하지 않습니다.   

### 생성자 오버로딩
클래스에 각각 다른 파라미터 목록을 갖는 생성자를 갯수와 관계없이 추가하는 기술입니다.   
컴파일러는 파라미터 갯수와 타입을 통해 오버로드된 생성자를 구분합니다.   
```
class Demo {

  int i;
  
  public Demo(int a) {
    i=k;
  }
  
  public Demo(int a, int b) {
    //body
  }

}
```

[맨위로](#java)

## Singleton(싱글톤) 클래스
하나의 JVM에서 하나의 인스턴스만 생성할 수 있는 클래스입니다.   
생성자를 private로 설정하여 만들 수 있습니다.   

[맨위로](#java)

## ArrayList와 Vector의 차이점
ArrayList
* synchronized되지 않습니다.
* synchronized되지 않으므로 속도가 빠릅니다.
* 최대 인덱스를 초과했을때 array의 크기가 50% 증가합니다.
* 생성할 때 size를 정의하지 않습니다.

Vector
* synchronized 됩니다.
* Thread-safe 하지만 속도가 느립니다.
* 최대 인덱스를 초과했을때 array의 크기가 100%(2배) 증가합니다.
* 생성할 때 size를 정의합니다.

[맨위로](#java)

## Array와 ArrayList의 차이점
Array
* size는 선언 시점에 정의해야 합니다.
* 데이터를 추가하려면 index를 지정해야 합니다.
* primitive 타입뿐만 아니라 객체도 포함될 수 있습니다.

ArrayList
* size를 동적으로 변경할 수 있습니다.
* 데이터를 추가할 때 index를 지정할 필요가 없습니다.
* 객체만 포함될 수 있으며 primitive 타입은 허용되지 않습니다.

[맨위로](#java)

## equals()와 ==의 차이점
equals()
* Object 클래스에 정의되어 있으며 정의된 비즈니스 로직을 통해 두 객체의 동일성을 확인하는데 사용됩니다.   

==
* Java의 기본 연산자입니다.   
* primitive 변수와 객체를 비교할 때 사용됩니다.
* 객체를 비교할 경우 객체의 주소값을 비교합니다.

[맨위로](#java)

## JVM의 Stack과 Heap의 차이점
Stack
* 하나의 스레드 내에서 사용됩니다.
* 다른 스레드에서 접근할 수 없습니다.
* LIFO(Last In First Out) 구조입니다.
* 스레드가 종료될 때까지 메모리가 유지됩니다.
* Local 변수가 할당됩니다.
  * Reference 타입일 경우 인스턴스 메모리는 Heap에 할당되고, 참조 변수만 Stack에 할당됩니다.

Heap
* 애플리케이션의 모든 부분에서 사용됩니다.
* 모든 스레드에서 접근할 수 있습니다.
* 메모리는 객체와 연관됩니다.
* 애플리케이션 실행 시작부터 끝까지 메모리가 유지됩니다.
* 객체를 생성할 때마다 항상 힙공간에 저장됩니다.

[맨위로](#java)

## Package(패키지)
관련있는 클래스 및 인터페이스의 모음입니다.   
개발자는 패키지를 사용하여 코드를 쉽게 모듈화하고 재사용성을 최적화할 수 있습니다.   
또한, 패키지 내의 코드를 다른 클래스에서 가져와서 재사용할 수 있습니다.   

### 장점
* 이름 충돌을 방지할 수 있습니다.
* 코드에 대한 접근 제어가 쉬워집니다.
* 외부 클래스에 노출되지 않고 패키지 내에서만 사용되게 할 수 있습니다.
* 관련된 클래스를 더 쉽게 찾을 수 있는 적절한 계층 구조를 만들 수 있습니다.

[맨위로](#java)

## Java에 포인터가 없는 이유
Java는 JVM이 메모리 할당을 담당하므로 사용자가 메모리에 직접 접근하는 것을 방지하기 위해 포인터를 사용하지 않습니다.   

[맨위로](#java)

## JIT 컴파일러
Just-In-Time 컴파일러를 의미합니다.   
Java 바이트코드를 프로세서(CPU)로 직접 전송되는 명령으로 변환해주는 프로그램입니다.  
Java 메서드가 호출될 때마다 활성화됩니다.   
그런 다음 호출된 메서드의 바이트코드를 네이티브 기계 코드로 컴파일하여 실행할 적시(just in time)에 실행되도록 합니다.      
메서드가 컴파일되면 JVM은 해당 메서드를 인터프리터를 통해 해석하지 않고 컴파일된 코드를 직접 호출합니다. 
따라서 런타임에 Java 애플리케이션의 성능 최적화를 담당합니다.

[맨위로](#java)

## 접근 제어자(access modifier)
다른 클래스와 다른 클래스의 생성자, 멤버 변수, 메서드에 대한 접근을 제어하는 키워드입니다.   

### 접근 제어자 유형
* Default
  * 같은 클래스에서 접근 가능
  * 같은 패키지의 자식 클래스에서 접근 가능
  * 같은 패키지의 다른 클래스에서 접근 가능
  * 다른 패키지의 자식 클래스에서 접근 불가능
  * 다른 패키지의 다른 클래스에서 접근 불가능
* Private
  * 같은 클래스에서 접근 가능
  * 같은 패키지의 자식 클래스에서 접근 불가능
  * 같은 패키지의 다른 클래스에서 접근 불가능
  * 다른 패키지의 자식 클래스에서 접근 불가능
  * 다른 패키지의 다른 클래스에서 접근 불가능
* Protected
  * 같은 클래스에서 접근 가능
  * 같은 패키지의 자식 클래스에서 접근 가능
  * 같은 패키지의 다른 클래스에서 접근 가능
  * 다른 패키지의 자식 클래스에서 접근 가능
  * 다른 패키지의 다른 클래스에서 접근 불가능
* Public
  * 같은 클래스에서 접근 가능
  * 같은 패키지의 자식 클래스에서 접근 가능
  * 같은 패키지의 다른 클래스에서 접근 가능
  * 다른 패키지의 자식 클래스에서 접근 가능
  * 다른 패키지의 다른 클래스에서 접근 가능

[맨위로](#java)

## 클래스 구조
필드(변수)와 객체의 동작을 설명하는 메서드로 구성됩니다.   
```
class Abc {

  member variables

  methods 

}
```

[맨위로](#java)

## Object(객체)
객체는 상태와 동작을 가진 실제 존재하는 엔티티입니다.   

### 객체의 특성
* State(상태)
* Behavior(동작)
* Identity(식별자)

### 객체 생성 방법
```
ClassName obj = new ClassName();
```

### Object Cloning(객체 복제)
객체의 복사본을 생성하는 프로세스입니다.   
객체 복제를 위해 Java는 clone() 메서드를 제공합니다.   
이 메서드는 현재 객체 클래스에 대한 새 인스턴스를 생성한 다음 해당 필드의 내용과 정확히 동일한 모든 필드를 초기화합니다.   
런타임 Exception을 방지하기 위해서는 Cloneable 마커 인터페이스를 구현해야합니다.   
clone() 메서드는 protected 메서드이므로 재정의해서 사용해야 합니다.

[맨위로](#java)

## 객체 지향 프로그래밍(OOP, Object Oriented Programming)
프로그램을 로직과 기능이 아닌 객체를 중심으로 구성하는 프로그래밍 모델 또는 접근 방식입니다.   
즉, OOP는 로직보다는 조작해야 하는 객체에 초점을 맞춥니다.   

### OOP의 주요 개념
* 상속(Inheritance)
  * 한 클래스가 다른 클래스의 속성을 얻는 프로세스입니다.
  * 코드를 재사용하고 클래스 간의 관계를 설정하는 데 도움이 됩니다.
  * 두 가지 클래스 유형 간에 수행됩니다.
    * 상위 클래스(Parent or Super or Base 클래스)
    * 하위 클래스(Child or Subclass or Derived 클래스)
  * 상속 유형 4가지
    * Single Inheritance(단일 상속)
      * 한 클래스는 다른 클래스의 속성을 상속받습니다.   
        * 한 부모 - 한 자녀 관계입니다.
    * Multilevel Inheritance(다계층 상속)
      * 한 클래스를 상속받은 클래스를 또 다른 클래스가 상속받는 것입니다.   
      * 즉 상위 클래스가 2개 이상 있는 경우입니다.   
    * Hierarchical Inheritance(계층 상속)
      * 한 클래스를 여러개의 클래스가 상속받은 경우입니다.
      * 즉, 둘 이상의 클래스가 동일한 상위 클래스를 갖는 경우입니다.   
    * Hybrid Inheritance(하이브리드 상속)
      * 위 상속 유형 중 2가지 이상의 상속 유형을 조합한 것입니다.
    * Multiple Inheritance(다중 상속)   
      * 하위 클래스가 여러 클래스를 상속받는 것을 다중 상속이라고 합니다.
      * Java에서는 다중 상속이 불가능합니다.
      * 다중 상속의 문제점은 여러 상위 클래스가 동일한 메서드 이름을 가진 경우 런타임에 컴파일러가 하위 클래스에서 실행할 메서드를 결정하기 어렵다는 것입니다.      

![6](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/6.PNG)

* 캡슐화(Encapsulation)
  * 데이터와 코드를 단일 단위로 함께 감싸는 메커니즘입니다.
  * 데이터는 외부에 숨겨지며 현재 클래스의 메서드를 통해서만 접근할 수 있습니다.
  * 불필요한 수정으로부터 데이터를 보호할 수 있습니다.
  * 캡슐화 하는 방법
    * 클래스의 변수를 private으로 선언합니다.
    * 변수의 값을 수정하고 확인할 수 있는 public getter/setter를 제공합니다.
* 추상화(Abstraction)
  * 사용자에게 구현 세부 정보를 숨기고 기능만을 제공하는 방법론입니다.   
  * 세부 정보를 숨기고 사용자에게는 필요한 정보만 보여주는 것입니다.   
  * 즉, 사용자에게 구현 세부 정보는 숨기고 기능만 공개하는 프로세스입니다.   
  * 추상화를 구현하는 2가지 방법
    * Abstract Class(추상 클래스)
      * 0 ~ 100% 추상화
    * Interface(인터페이스)
      * 100% 추상화
* 다형성(Polymorphism)
  * 변수, 함수, 객체가 여러 형태를 취할 수 있는 특성입니다.  
  * 간단하게 "하나의 인터페이스, 많은 구현"으로 묘사됩니다.
  * 다른 무언가에 다른 의미나 용법을 부여할 수 있는 특성입니다.
    * 특히 변수, 함수, 객체와 같은 엔티티가 둘 이상의 형식을 가질 수 있도록 허용합니다.  

  ![5](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/5.PNG)   
  * 두 가지 유형이 있습니다.
    * 컴파일타임 다형성
      * 메서드 오버로딩
    * 런타임 다형성
      * 상속과 인터페이스를 사용하여 수행됩니다. (메서드 오버라이딩)
      * 재정의(오버라이딩)된 메서드에 대한 호출이 컴파일 시간이 아닌 런타임에 해결되는 프로세스입니다.   
      * 이 과정에서 재정의된 메서드는 상위클래스의 참조 변수를 통해 호출됩니다.
      * 예시
      ```
      class Car {

        void run() {
          System.out.println(&ldquo;car is running&rdquo;);
        }

      } 

      class Audi extends Car {

        void run() {
          System.out.prinltn(&ldquo;Audi is running safely with 100km&rdquo;);
        }
        
        public static void main(String args[]) {
          Car b= new Audi(); //upcasting b.run();
        }

      }
      ```

[맨위로](#java)

## 로컬 변수(local variable)과 인스턴스 변수(instance variable)의 차이점
로컬 변수(local variable)
* 메서드, 생성자, 블럭 내에서 사용됩니다.
* 따라서 로컬 변수는 블럭 범위 내에서만 사용할 수 있습니다.
* 장점은 클래스의 다른 메서드가 해당 변수를 인식하지 못한다는 점입니다.
```
if(x > 100) {
  String test = "Edureka";
}
```

인스턴스 변수(instance variable)
* 객체 자체에 바인딩된 변수입니다.   
* 클래스 내에서 메서드 외부에 선언됩니다.
* 해당 클래스의 모든 객체는 객체를 사용하는 동안 변수의 복사본을 생성합니다.
* 따라서 변수의 변경 사항은 해당 클래스의 다른 인스턴스에 반영되지 않으며 해당 인스턴스에만 반영됩니다.   
```
class Test{

  public String EmpName;
  public int empAge; 
  
}
```

[맨위로](#java)

## final 키워드
클래스, 메서드, 변수에 대한 제한을 적용하는 데 사용됩니다.   
final 키워드는 다음과 같이 사용됩니다.
* final variable
  * 할당된 값을 변경할 수 없습니다.
  * 값이 할당되지 않은 경우 클래스 생성자를 통해서만 값을 할당할 수 있습니다.
* final method
  * 상속 클래스에서 메서드를 재정의할 수 없습니다.
* final class
  * 자식 클래스에 의해 상속될 수 없지만 다른 클래스를 상속 받을 수는 있습니다.
```
class FinalVarExample {
  
  public static void main( String args[]) {
    final int a=10; // Final 변수
    a=50; // 변경할 수 없으므로 에러
  }

}
```

[맨위로](#java)

## break와 continue의 차이점
break
* switch문 또는 loop 문(for, while, do while)에서 사용될 수 있습니다.
* 실행되는 순간 switch문 또는 loop문이 종료됩니다.
* 실행된 가장 안쪽의 switch문 또는 loop문이 종료되는 것입니다.   
```
for (int i = 0; i < 5; i++) {
  if (i == 3) {
    break;
  }
  
  System.out.println(i); 
}
```

continue
* loop 문(for, while, do while)에서만 사용될 수 있습니다.
* loop를 종료하지는 않고 다음 반복으로 건너뛰게 합니다.
* loop문 내의 switch문에서 실행되어도 loop문의 다음 반복이 실행됩니다.
```
for (int i = 0; i < 5; i++) {
  
  if(i == 2) {
    continue;
  }

  System.out.println(i);
}
```

[맨위로](#java)

## 무한 루프(infinite loop)
루프의 종료 조건이 충족되지 않을 때 끝없이 반복하는 것입니다.   
애플리케이션이 종료되면 종료됩니다.   
```
public class InfiniteForLoopDemo {

  public static void main(String[] arg) {
    for(;;) {
      System.out.println("Welcome to Edureka!");
    }
  }

}
```

[맨위로](#java)

## this()와 super()의 차이점
둘 다 생성자를 호출하는 데 사용되는 키워드입니다.   
* this()
  * 클래스의 현재 인스턴스를 나타냅니다.
  * 동일한 클래스의 디폴트 생성자를 호출하는 데 사용됩니다.
  * 현재 클래스의 메서드에 접근하는 데 사용됩니다.
  * 현재 클래스 인스턴스를 가리키는 데 사용됩니다.
  * 블럭의 첫 번째 라인이어야 합니다.
* super()
  * 상위 클래스의 현재 인스턴스를 나타냅니다.
  * 상위 클래스의 디폴트 생성자를 호출하는 데 사용됩니다.
  * 상위 클래스의 메서드에 접근하는 데 사용됩니다.
  * 상위 클래스 인스턴스를 가리키는 데 사용됩니다.
  * 블럭의 첫 번째 라인이어야 합니다.

[맨위로](#java)

## String Pool
리터럴을 이용한 String 생성 방식과 관련이 있습니다.   
Heap 메모리에 저장된 문자열들을 참조합니다.   
새 객체를 생성할 때마다 먼저 객체가 pool에 이미 있는지 여부를 확인합니다.   
객체가 이미 있으면 동일한 참조가 반환되고   
객체가 없으면 String pool에 새 객체가 생성되고 각각의 참조가 반환됩니다.   
![3](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/3.PNG)

### String이 immutable 클래스인 이유
String 객체는 일반적으로 String pool에서 캐시되므로 immutable입니다.   
따라서 String은 객체의 값을 수정하는 대신 새 문자열 객체를 생성하게 됩니다.   
String은 immutable이기 때문에 애플리케이션의 동기화 관련 성능을 향상시킵니다.   

[맨위로](#java)

## static 메서드와 non-static 메서드의 차이점
static 메서드
* 메서드 이름 앞에 사용해야 합니다.
* 클래스를 사용하여 호출합니다.
  * ex) ClassName.methodName
* non-static 인스턴스 변수나 메서드에 접근할 수 없습니다.

non-static 메서드
* 메서드 이름 앞에 static 키워드를 사용하지 않습니다.
* 일반적인 메서드 호출 방식입니다.
* 클래스의 인스턴스를 생성하지 않고 static 메서드와 static 변수에 접근할 수 있습니다.

[맨위로](#java)

## Constructor Chaining(생성자 체이닝)
현재 객체에 대해서 한 생성자를 다른 생성자에서 호출하는 프로세스입니다.   
우선 하위 클래스 생성자가 super클래스의 생성자를 먼저 호출해야만 가능합니다.   
생성자 체이닝에는 얼마든지 많은 수의 클래스가 있을 수 있습니다.   

### 생성자 체이닝 방법
* 같은 클래스에서 this()를 사용합니다.
* super()를 사용하여 상위 클래스 생성자를 가져옵니다.

[맨위로](#java)

## String, StringBuilder, StringBuffer의 차이점
String
* Constant String Pool에 저장됩니다.
* Immutable 입니다.
* Thread-safe 합니다.
* 속도가 빠릅니다.

StringBuilder
* Heap 영역에 저장됩니다.
* Mutable 입니다.
* Thread-safe 하지 않습니다.
* StringBuffer보다 더 효율적입니다.

StringBuffer
* Heap 영역에 저장됩니다.
* Mutable 입니다.
* Thread-safe 합니다.
* StringBuilder에 비해 덜 효율적입니다.

[맨위로](#java)

## Class Loader(클래스 로더)
클래스 파일 로드를 담당하는 JVM의 구성 요소입니다.   
Java 프로그램이 실행될 때마다 먼저 클래스 로더에 의해 로드됩니다.   
Java는 세 가지 클래스 로더를 제공합니다.
* Bootstrap ClassLoader
* Extension ClassLoader
* System/Application ClassLoader

[맨위로](#java)

## Map
Util 패키지의 인터페이스로 고유한 key와 value를 매핑합니다.   
Map 인터페이스는 컬렉션 인터페이스가 아니므로 다른 컬렉션 타입과 다르게 동작합니다.  

Map 인터페이스의 특징
* key값은 중복을 허용하지 않습니다.
* 각 key는 1개의 value만 매핑할 수 있습니다.

[맨위로](#java)

## Collection(컬렉션)
컬렉션은 객체 그룹을 저장하고 조작하는 아키텍처 역할을 하는 프레임워크입니다.   
컬렉션을 사용하여 검색, 정렬, 삽입, 조작, 삭제 등과 같은 다양한 작업을 수행할 수 있습니다.   

컬렉션의 계층 구조   
![2](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/2.PNG)

[맨위로](#java)

## Interface(인터페이스)
추상 메서드와 static 상수의 모음입니다.   
인터페이스의 각 메서드는 public이고 abstract이며, 생성자를 포함하지 않습니다.   
따라서 인터페이스의 메서드는 body가 없습니다.

예시
```
public interface Animal {

  public void eat();
  public void sleep();
  public void run();

}
```

### Abstract class(추상 클래스)와 Interface(인터페이스)의 차이점
Abstract class(추상 클래스)
* 1개의 추상 클래스만 확장할 수 있습니다.
* abstract가 아닌 메서드를 가질 수 있습니다.
* 인스턴스 변수를 가질 수 있습니다.
* 모든 접근 제어자를 가질 수 있습니다.
  * public, private, protected
* 새 메서드를 추가되어도 이를 상속받은 클래스의 모든 코드가 정상 작동합니다.   
* 생성자를 포함할 수 있습니다.
* 속도가 빠릅니다.

Interface(인터페이스)
* 하나의 클래스는 여러 인터페이스를 구현할 수 있습니다.
* 모든 메서드가 추상 메서드입니다.   
* 인스턴스 변수를 사용할 수 없습니다.
* 접근 제어자는 public 이거나 없어야 합니다.   
* 새 메서드를 추가하는 경우 이 인터페이스를 구현한 클래스는 새 메서드를 재정의해야 합니다.
* 생성자를 포함할 수 없습니다.
* 해당 메서드를 실제 구현한 메서드를 찾아야 하므로 속도가 느립니다.

### Marker Interface(마커 인터페이스)
멤버 변수 및 메서드가 없는 인터페이스입니다.   
간단히 말해서 빈 인터페이스를 마커 인터페이스라고 합니다.   
가장 일반적인 예로는 Serializable, Cloneable 등이 있습니다.   

마커 인터페이스는 다음과 같이 선언할 수 있습니다.
```
public interface Serializable{ }
```

[맨위로](#java)

## Overloading(오버로딩)과 Overriding(오버라이딩)의 차이점
Overloading(오버로딩)
* 동일한 클래스에서 메서드 이름은 같지만 파라미터 갯수 또는 파라미터의 유형과 순서가 달라야 합니다.
* 메서드의 동작을 "추가" 또는 "확장"하는 것입니다.
* 컴파일타임 다형성과 관련 있습니다.
* 메서드 시그니처가 달라야 합니다.
  * 메서드 이름 + 파라미터 리스트
* 상속이 필요할 수도 있고 필요하지 않을 수도 있습니다.
* 예시
```
class Adder {

  Static int add(int a, int b) {
    return a+b;
  }
  
  Static double add( double a, double b) {
    return a+b;
  }
  
  public static void main(String args[]) {
    System.out.println(Adder.add(11,11));
    System.out.println(Adder.add(12.3,12.6));
  }
  
}
```

Overriding(오버라이딩)
* 하위 클래스가 상위 클래스의 동일한 메서드 이름, 동일한 파라미터 갯수, 동일한 파라미터 유형, 동일한 리턴 타입을 갖는 메서드를 정의하는 것입니다.   
* 메서드의 기존 동작을 "변경"하는 것입니다.
* 런타임 다형성과 관련 있습니다.
* 메서드 시그니처가 동일해야 합니다.
* 항상 상속이 필요합니다.
* 예시
```
class Car {

  void run() {
    System.out.println(&ldquo;car is running&rdquo;);
  }

}
  
Class Audi extends Car {

  void run() {
    System.out.prinltn("Audi is running safely with 100km");
  }
  
  public static void main( String args[]) {
    Car b=new Audi();
    b.run();
  }
  
}
```
* private 또는 static 메서드는 재정의할 수 없습니다.
* 하위 클래스에 동일한 리턴 타입과 파라미터를 사용하여 유사한 메서드를 생성하면 상위 클래스 메서드가 숨겨집니다.
  * 이를 메서드 숨기기라고 합니다.
* 하위 클래스에서 상위 클래스의 private 메서드에 접근이 불가능하기 때문에 재정의 할 수 없습니다.
* 하위 클래스에 동일한 이름을 가진 private 메서드를 생성할수는 있습니다.
* 예시
```
class Base {

  private static void display() {
    System.out.println("Static or class method from Base");
  }
  
  public void print() {
    System.out.println("Non-static or instance method from Base");
  }
  
}

class Derived extends Base {

  private static void display() {
    System.out.println("Static or class method from Derived");
  }
  
  public void print() {
    System.out.println("Non-static or instance method from Derived");
  }

}
  
public class test {

  public static void main(String args[]) {
    Base obj= new Derived();
    obj1.display();
    obj1.print();
  }
  
}
```

[맨위로](#java)

## Servlet(서블릿)
* 동적인 Response와 데이터 영속성을 지원하여 웹 서버의 기능을 확장시켜주는 server-side 기술입니다.   
* javax.servlet과 javax.servlet.http 패키지는 서블릿 작성을 위한 인터페이스와 클래스를 제공합니다.
* 모든 서블릿은 서블릿의 라이프사이클 메서드를 정의하는 javax.servlet.Servlet을 구현해야합니다.
* 서비스를 구현할 때 Java Servlet API과 함께 제공되는 GenericServlet 클래스를 확장할 수 있습니다.
* HttpServlet 클래스는 HTTP 서비스를 처리하기 위한 doGet(), doPost()와 같은 메서드를 제공합니다.
  * 대부분의 웹 애플리케이션은 HTTP 프로토콜을 사용하므로 HttpServlet 클래스를 확장합니다.
* Servlet API 계층   
![4](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/4.PNG)

### Life-cycle(생명 주기)
서블릿의 생명 주기는 5가지 단계가 있습니다.   
![9](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/9.PNG)
* loaded(로드)
* instantiated(인스턴스화)
* initialized(초기화)
* request(요청)
* destroyed(파괴)

### 서블릿에서의 Cookie(쿠키)
* 쿠키는 서버에서 클라이언트로 보내는 텍스트 데이터이며 클라이언트의 로컬에 저장됩니다.
* 서블릿 API는 Serializable과 Cloneable 인터페이스를 구현한 javax.servlet.http.Cookie 클래스를 통해 쿠키를 지원합니다.
* 요청으로부터 쿠키 리스트를 가져오는 HttpServletRequest의 getCookies() 메서드가 제공되며, request에 쿠키를 추가하는 것은 의미가 없기 때문에 set, add와 같은 메서드는 없습니다.
* 마찬가지로 HttpServletResponse에는 응답 헤더에 쿠키를 추가하기 위한 addCookie(Cookie c) 메서드가 제공되지만 getter 메서드는 제공되지 않습니다.

### 서블릿에서의 Session(세션)
세션은 클라이언트와 서버 간의 대화 상태이며 클라이언트와 서버 간의 여러 요청 및 응답으로 구성됩니다.   
HTTP와 웹 서버는 모두 stateless(무상태)이기 때문에 세션을 유지하기 위한 유일한 방법은 모든 요청과 응답에서 세션(세션 ID)에 대한 고유한 정보가 서버와 클라이언트 간에 전달되는 것입니다.   

서블릿의 세션 관리 방법
* User Authentication(사용자 인증)
* HTML Hidden Field(HTML Hidden 필드)
* Cookies
* URL Rewriting
  * URL 의 뒷 부분에 정보를 가지고 다니는 것을 말합니다.
* Session Management API    

![10](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/10.PNG)

[맨위로](#java)

## Get 메서드와 Post 메서드의 차이점
Get
* 데이터가 body로 전송되지 않기 때문에 데이터 전송량이 제한됩니다.   
* 데이터가 URL에 노출되어 보안되지 않습니다.
* Idempotent(멱등) 입니다.
  * 멱등의 사전적 정의는 연산을 여러 번 적용하더라도 결과가 달라지지 않는 성질을 의미합니다.
  * GET은 리소스를 조회한다는 점에서 여러 번 요청하더라도 응답이 똑같을 것입니다. 
  * 반대로 POST는 리소스를 새로 생성하거나 업데이트할 때 사용되기 때문에 멱등이 아니라고 볼 수 있습니다.

Post
* 데이터가 body로 전송되기 때문에 대량의 데이터가 전송될 수 있습니다.
* 데이터가 URL에 노출되지 않기 때문에 보안이 됩니다.
* Non-Idempotent 입니다.

[맨위로](#java)

## RequestDispatcher
RequestDispatcher 인터페이스는 Request를 동일한 애플리케이션 내의 다른 HTML, JSP, Servlet 리소스에 전달하는 데 사용됩니다.   
또한 Response에 다른 리소스의 내용을 포함시키기 위해 이 기능을 사용할 수 있습니다.   

2가지 메서드가 정의되어 있습니다.
* void forward()   
![7](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/7.PNG)
* void include()   
![8](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/8.PNG)

### forward() 메서드와 sendRedirect() 메서드의 차이점
forward() 메서드
* 동일한 request를 다른 리소스로 전송합니다.
* server-side에서 작동합니다.
* 서버 내에서만 작동합니다.

sendRedirect() 메서드
* 브라우저의 URL을 사용하기 때문에 항상 새로운 요청을 보냅니다.
* client-side에서 작동합니다.
* 서버 내외부에서 모두 작동합니다.

[맨위로](#java)

## ServletConfig와 ServletContext의 차이점
ServletConfig
* 단일 서블릿을 나타냅니다.
* 특정 서블릿과 관련된 로컬 파라미터와 유사합니다.
* web.xml 파일의 servlet 섹션에 정의된 name-value 쌍이므로 servlet scope입니다.
* getServletConfig() 메서드를 사용하여 Config 객체를 가져옵니다.


ServletContext
* 특정 JVM에서 실행되는 전체 웹 애플리케이션을 나타내며 모든 서블릿에 공통적입니다.
* 전체 애플리케이션과 관련된 전역 파라미터와 유사합니다.
* web.xml 파일의 servlet 섹션 외부에 정의되기 때문에 애플리케이션 전체 scope입니다.
* getServletContext() 메서드를 사용하여 Context 객체를 가져옵니다.

[맨위로](#java)

## JDBC Driver
Java 애플리케이션이 데이터베이스와 상호 작용할 수 있도록 해주는 소프트웨어입니다.   

JDBC Driver 4가지 유형
* JDBC-ODBC bridge driver
* Native-API driver (일부 java driver)
* Network Protocol driver (완전 java driver)
* Thin driver (완전 java driver)

![11](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/11.PNG)

[맨위로](#java)

## Java에서 데이터베이스와 연결하는 과정
* Driver 클래스를 등록합니다.
* Connection을 생성합니다.
* Statement를 생성합니다.
* 쿼리를 실행합니다.
* Connection을 종료합니다.

[맨위로](#java)

## JDBC API 구성요소
java.sql 패키지에는 JDBC API에 대한 인터페이스와 클래스들이 있습니다.

인터페이스
* Connection
  * 데이터베이스와의 세션을 유지 관리합니다.
  * 트랜잭션 관리에 사용됩니다.
  * Statement, PreparedStatement, CallableStatement, DatabaseMetaData 인스턴스를 반환하는 팩토리 메서드를 제공합니다.   

![12](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/12.PNG)
* Statement
* PreparedStatement
* ResultSet
  * 테이블의 행을 나타냅니다.
  * 커서 포인터를 변경하고 데이터베이스에서 정보를 가져오는데 사용됩니다.
* ResultSetMetaData
  * 총 열의 수, 열 이름, 열 타입 등의 테이블 정보를 반환합니다.
* DatabaseMetaData
  * 사용자 이름, 드라이버 이름, 드라이버 버전, 테이블 수, View의 수와 같은 정보를 반환합니다.
* CallableStatement 등

클래스
* DriverManager
  * 등록된 Driver들을 관리합니다.
  * Driver를 등록 및 등록 취소하는데 사용됩니다.
  * Connection 인스턴스를 반환해주는 팩토리 메서드를 제공합니다.
* Blob
* Clob
* Types
* SQLException 등

[맨위로](#java)

## JDBC Batch 처리(일괄 처리)
관련된 SQL 문을 배치로 그룹화하고 단일 쿼리 대신에 실행할 수 있습니다.
여러 쿼리를 실행하는데 더 높은 성능을 낼 수 있습니다.

[맨위로](#java)

## JDBC Statement
SQL 명령을 데이터베이스에 전송하고 데이터베이스에서 데이터를 검색하는 데 사용되는 것입니다.
execute(), executeUpdate(), executeQuery() 등과 같은 다양한 메서드들이 데이터베이스와 상호작용 할 수 있도록 JDBC에 의해 제공됩니다.

JDBC가 제공하는 3가지 Statement 유형
* Statement
  * 데이터베이스에 대한 일반적인 접근에 사용되며 런타임에 정적인 SQL 쿼리를 실행합니다.   
* PreparedStatement
  * 실행 중에 쿼리에 대한 파라미터를 제공하는데 사용됩니다.
* CallableStatement
  * 데이터베이스의 Stored Procedure(저장 프로시저)에 접근하는데 사용되며 런타임 파라미터를 제공하는데 사용됩니다.

### execute, executeQuery, executeUpdate의 차이점
execute
* SQL 쿼리를 실행하는데 사용되며 결과가 ResultSet이면 TRUE를 리턴합니다.   
* insert 또는 update 쿼리의 결과는 FALSE를 리턴합니다.
* getResultSet() 메서드를 통해 ResultSet을 가져오고 getUpdateCount() 메서드를 통해 update 수를 가져올 수 있습니다.
* Statement의 유형이 불확실할때만 사용해야 합니다.

executeQuery
* select 쿼리를 실행하는데 사용되며 ResultSet을 리턴합니다.
* 쿼리와 일치하는 레코드가 없는 경우에도 ResultSet은 null이 아닙니다.
* select 쿼리를 실행할 때 executeQuery 메서드를 사용해야 하며 insert/update 문을 실행할 때 사용하면  SQLException이 발생합니다.

executeUpdate
* insert/update/delete(DML) 또는 DDL문을 실행하는 데 사용됩니다.
* 리턴 타입은 int형이며 DML문 row의 수가 리턴됩니다.   
* DDL문의 경우 0이 리턴됩니다.

[맨위로](#java)

## finalize
객체가 GC 처리 되기 전에 작업을 수행하는데 사용됩니다.   
```
class FinalizeExample {

  public void finalize() {
    System.out.println("Finalize is called");
  } 
  
  public static void main(String args[]) {
    FinalizeExample f1=new FinalizeExample();
    FinalizeExample f2=new FinalizeExample();
    f1= NULL;
    f2= NULL;
    System.gc();
  }

}
```

[맨위로](#java)

## Exception과 Error
Throwable은 모든 Exception 클래스들의 상위 클래스입니다.   

Exception에는 2가지 유형이 있습니다.
* CheckedExceptions
* UncheckedException(또는 RunTimeException)

2가지 Exception 유형 모두 Exception 클래스를 상속받으며   
Error는 VirtualMachineError와 AssertionError로 분류됩니다.

![13](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/13.PNG)

### Error와 Exception의 차이점
Error는 런타임에 발생하는 복구할 수 없는 상태입니다.   
OutOfMemory와 같은 에러입니다.   
* OutOfMemoryError는 java.lang.Error의 하위 클래스이며 JVM의 메모리가 부족할 때 발생하는 에러입니다.   

이러한 JVM 에러는 런타임에 복구할 수 없습니다.   
catch 블럭에서 에러가 발생할 수 있지만 애플리케이션 실행이 중지되어 복구할 수 없습니다.   

Exception은 입력 오류 또는 휴먼 에러 등으로 인해 발생합니다.   
예를 들어 지정된 파일이 존재하지 않으면 FileNotFoundException이 발생합니다.   
다른 예로 null 참조를 사용하려고 하면 NullPointerException이 발생합니다.   
대부분의 경우 Exception으로부터 복구할 수 있습니다.   
(적절한 값 입력 등에 대한 사용자 피드백을 제공하는 방법 등)

### Exception 처리 방법
Java에서 Exception 처리를 하기 위한 5가지 키워드입니다.
* try
* catch
  * 하나의 try 블럭에 여러개의 catch 블럭을 사용할 수 있습니다.
  * 단 Exception의 범위가 낮은 것부터 작성되어야 합니다.
```
public class Example {

  public static void main(String args[]) {
    try {
      int a[]= new int[10];
      a[10]= 10/0;
    } catch(ArithmeticException e) {
      System.out.println("Arithmetic exception in first catch block");
    } catch(ArrayIndexOutOfBoundsException e) {
      System.out.println("Array index out of bounds in second catch block");
    } catch(Exception e) {
      System.out.println("Any exception in third catch block");
    }
  }
  
}
```
* finally
  * 중요한 코드를 배치하는 데 사용되며 Exception이 처리되었는지 여부와 관계없이 실행됩니다.
  * System.exit()를 호출하거나 프로세스를 중단시키는 치명적인 오류가 발생하여 프로그램이 종료되는 경우에는 실행되지 않습니다.
```
class FinallyExample {
  
  public static void main(String args[]){
    try {
      int x=100;
    } catch(Exception e) {
      System.out.println(e);
    } finally {
      System.out.println("finally block is executing");
    }
  }
  
}
```
* throw
  * 명시적으로 Excpetion을 발생시키는 데 사용됩니다.
  * CheckedException은 throw만으로 전파될 수 없습니다.
  * 인스턴스에 의해 사용됩니다.
  * 메서드 내에서 사용됩니다.
  * 다중 Exception을 발생시킬 수 없습니다.
* throws
  * Exception을 선언하는 데 사용됩니다.
  * CheckedException은 throws를 통해 전파될 수 있습니다.
  * 클래스에 의해 사용됩니다.
  * 메서드 시그니처와 함께 사용됩니다.
  * 다중 Exception을 선언할 수 있습니다.
    * 예) public void method() throws IOException,SQLException

### Checked Exception과 Unchecked Exception의 차이점
Checked Exception
* RuntimeException과 Error을 제외한 Throwable 클래스를 상속받은 클래스입니다.
* 컴파일 시 확인됩니다.   
* 예) IOException, SQLException 등

Unchecked Exception
* RuntimeException을 상속받은 클래스입니다.
* 컴파일 시 확인되지 않습니다.
* 예) ArithmeticException, NullPointerException 등

### 사용자 정의 Exception
사용자 정의 Exception을 생성하려면 Exception 클래스 또는 Exception 클래스의 하위 클래스를 상속 받아야 합니다.   
```
class New1Exception extends Exception { }               // Checked Exception
class NewException extends IOException { }             // Checked exception
class NewException extends NullPonterExcpetion { }  // UnChecked exception
```

### Exception 클래스의 메서드
Exception 또는 Exception 하위 클래스들은 특정 메서드를 제공하지 않으며 모든 메서드는 Throwable 클래스에 정의되어 있습니다.   
* String getMessage()
  * Throwable의 String 메시지를 반환하며 그 메시지는 생성자를 통해 메시지를 제공될 수 있습니다.
* String getLocalizedMessage()
  * 하위 클래스가 재정의하여 메시지를 제공할 수 있도록 합니다.   
  * getMessage() 메서드를 사용하여 예외 메시지를 반환합니다.
* Synchronized Throwable getCause()
  * Exception의 원인을 반환하거나 원인을 알 수 없는 경우 null을 반환합니다.
* String toString()
  * Throwable에 대한 정보를 String 형식으로 반환하며 반환된 String에는 Throwable 클래스 이름과 메시지가 포함됩니다.
* void printStackTrace()
  * 스택 추적 정보를 표준 에러 스트림에 출력합니다.
  * 오버로드 된 메서드들이 있는데 이 메서드들은 스택 추적 정보를 파일이나 스트림에 write하기 위해 PrintStream 또는 PrintWriter를 파라미터로 전달할 수 있습니다.
* public StackTraceElement[] getStackTrace()
  * 스택 추적의 각 요소를 포함하는 배열을 반환합니다.
  * 0번 index는 호출 스택의 맨 위를 나타내고, 마지막 요소는 호출 스택의 맨 아래의 메서드를 나타냅니다.

[맨위로](#java)

## Thread(스레드)
스케쥴러에 의해 독립적으로 실행될 수 있는 프로그램의 작은 부분입니다.   
Java에는 모든 프로그램에 메인 스레드라고 알려진 스레드가 하나 이상 있습니다.   
이 메인 스레드는 프로그램이 실행될 때 JVM에 의해 생성됩니다.   
메인 스레드는 프로그램의 main()을 호출하는 데 사용됩니다.

### Proccess(프로세스)와 Thread(스레드)의 차이점
Proccess(프로세스)
* 프로그램의 실행 인스턴스입니다.
* 다른 프로세스와 통신하기 위해서는 Inter-Process Communication(IPC, 프로세스 간 통신)을 사용해야 합니다.
* 하위 프로세스에 대한 제어만 수행할 수 있습니다.
* 상위 프로세스의 변경 사항은 하위 프로세스에 영향을 주지 않습니다.
* 별도의 메모리 공간에서 실행됩니다.
* 운영 체제에 의해 제어됩니다.
* 독립적입니다.

Thread(스레드)
* 프로세스의 subset(하위 집합) 입니다.
* 프로세스의 다른 스레드와 직접 통신할 수 있습니다.
* 동일한 프로세스의 다른 스레드들을 제어할 수 있습니다.
* 메인 스레드의 변경 사항이 프로세스의 다른 스레드들의 동작에 영향을 줄 수 있습니다.
* 공유 메모리 공간에서 실행됩니다.
* 프로그램 개발자에 의해 제어됩니다.
* 종속적입니다.

### Synchronization(동기화)
멀티 스레드 환경에서 동기화된 코드 블럭은 한 번에 하나의 스레드만 실행될 수 있습니다.   
멀티 스레드 환경에서는 둘 이상의 스레드가 동일한 필드 또는 객체에 접근할 수 있습니다.   
동기화는 실행 중인 모든 스레드가 동기화되도록 유지하는 프로세스입니다.   
동기화는 공유 메모리의 불일치로 인한 메모리 일관성 에러를 방지합니다.
메서드가 synchronized로 선언되면 스레드가 해당 메서드의 객체에 대한 동기화를 유지합니다.   
스레드가 synchronized된 메서드를 실행하는 경우 해당 스레드의 작업이 완료될 때까지 다른 스레드의 접근이 차단됩니다.   
![14](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/14.PNG)

### 스레드 생성 방법
* Runnable 인터페이스를 구현합니다.
* Thread를 상속받습니다.

[맨위로](#java)

## Garbage Collector(GC, 가비지 컬렉터)
암시적 메모리 관리에 도움이 되는 프로그램입니다.   
Java에서는 new 키워드를 사용하여 동적으로 객체를 생성할 수 있으며, 생성되면 메모리가 사용됩니다.   
작업이 완료되고 객체에 대한 참조가 더이상 남지 않게 되면 Java는 가비지 컬렉터를 사용하여 객체를 제거하고 해당 객체에 사용된 메모리를 제거합니다.   

Java는 4가지 유형의 가비지 컬렉터를 제공합니다.
* Serial Garbage Collector
* Parallel Garbage Collector
* CMS Garbage Collector
* G1 Garbage Collector

[맨위로](#java)

## 참고
* [100+ Java Interview Questions And Answers For 2021 | Edureka](https://www.edureka.co/blog/interview-questions/java-interview-questions/)

[맨위로](#java)
