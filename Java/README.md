# Java
* [JDK, JRE, JVM](#jdk-jre-jvm)
* [public static void main(String args[])](#public-static-void-mainstring-args)
* [Java가 플랫폼에 독립적인 이유](#java가-플랫폼에-독립적인-이유)
* [Java가 100% 객체 지향적이지 않은 이유](#java가-100-객체-지향적이지-않은-이유)
* [Wrapper 클래스](#wrapper-클래스)
* [Constructor(생성자)](#constructor생성자)
* [Singleton(싱글톤) 클래스](#singleton싱글톤-클래스)
* [ArrayList와 Vector의 차이점](#arraylist와-vector의-차이점)
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
* [String, StringBuilder, StringBuffer 차이점](#string-stringbuilder-stringbuffer-차이점)
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

[맨위로](#java)

## 객체 지향 프로그래밍(OOP, Object Oriented Programming)
프로그램을 로직과 기능이 아닌 객체를 중심으로 구성하는 프로그래밍 모델 또는 접근 방식입니다.   
즉, OOP는 로직보다는 조작해야 하는 객체에 초점을 맞춥니다.   

### OOP의 주요 개념
* 상속(Inheritance)
  * 한 클래스가 다른 클래스의 속성을 얻는 프로세스입니다.
* 캡슐화(Encapsulation)
  * 데이터와 코드를 단일 단위로 함께 감싸는 메커니즘입니다.
* 추상화(Abstraction)
  * 사용자에게 구현 세부 정보를 숨기고 기능만을 제공하는 방법론입니다.   
* 다형성(Polymorphism)
  * 변수, 함수, 객체가 여러 형태를 취할 수 있는 특성입니다.   

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
final 키워드는 다음과 같이 사용됩니다.
* final variable
  * 할당된 값을 변경할 수 없습니다.
  * 값이 할당되지 않은 경우 클래스 생성자를 통해서만 값을 할당할 수 있습니다.
* final method
  * 상속 클래스에서 메서드를 재정의할 수 없습니다.
* final class
  * 자식 클래스에 의해 상속될 수 없지만 다른 클래스를 상속 받을 수는 있습니다.

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

## String, StringBuilder, StringBuffer 차이점
String
* Constant String Pool에 저장됩니다.
* Immutable 입니다.
* Thread-safe 합니다.
* 속도가 빠릅니다.

StringBuilder
* Heap 영역에 저장됩니다.
* Mutable 입니다.
* Thread-safe 하지 않습니다.
* 더 효율적입니다.

StringBuffer
* Heap 영역에 저장됩니다.
* Mutable 입니다.
* Thread-safe 합니다.
* 덜 효율적입니다.

[맨위로](#java)

## 참고
* [100+ Java Interview Questions And Answers For 2021 | Edureka](https://www.edureka.co/blog/interview-questions/java-interview-questions/)

[맨위로](#java)
