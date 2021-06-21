# Java
* [primitive variable와 reference variable의 차이점]()
* [Java 변수의 종류]()
* [static variable이란?]()
* [instance variable이란?]()
* [local variable이란?]()
* [block variable이란?]()
* [final variable이란?]()
* [transient variable이란?]()
* [volatile variable이란?]()

## primitive variable와 reference variable의 차이점
primitive variable은 기본 리터럴 값을 갖는 변수이다.
* ex) int var1 = 123;   

reference variable은 Object에 대한 참조 값을 갖는 변수이다.
* ex) Box var2 = new Box();

## Java 변수의 종류
기본적으로는 primitive variable과 reference variable 두 종류가 있다.   
primitive variable은 기본 리터럴 값을 갖는 변수이며,   
reference variable은 Object에 대한 참조 값을 갖는 변수이다.   

변수의 scope에 따라서는 class variable, instance variable, local variable, Block variable 4가지로 나뉜다.      
scope은 클래스 내에 선언된 위치에 따라 결정된다.
* Class variable(static field)
  * 메서드나 블럭 외부에 선언된다.
  * 'static' 키워드로 선언된다.
  * 가장 긴 scope을 갖는다.
  * 클래스가 로드될때 생성되며 클래스가 JVM에 로드된 상태로 유지되는 한 계속 메모리에 남아 있다.
* Instance variable(Non-static fields)
  * 메서드나 블럭 외부에 선언된다.
  * 'static' 키워드 없이 선언된다.
  * 두번째로 긴 scope을 갖는다.
  * 새 클래스 인스턴스가 생성될 때 생성되며 인스턴스가 메모리에서 제거 될 때까지 유지된다.
* Local variable
  * 메서드 본문 내에 선언된 변수이다.
  * 선언된 메서드가 스택에 남아있는 동안만 유지된다.
* Block variable
  * init block이나 for문과 같은 block 내에서 선언된 변수이다.
  * block을 실행하는 동안에만 살고 가장 짧게 삶아있는 변수이다.

## static variable이란?
메서드 또는 블록 외부에 선언되며 'static' 키워드로 선언된 변수이다.   
scope이 가장 길다.    
클래스가 로드될때 생성되며 클래스가 JVM에 로드된 상태로 유지되는 한 계속 메모리에 남아 있다.      
전역 변수이다.   
모든 객체간에 공유된다.   
클래스의 모든 인스턴스는 동일한 static variable을 공유한다.   
객체 인스턴스를 만들지 않고 클래스를 사용하여 접근할 수 있다.   
Heap에 저장된다.   

## instance variable이란?
메서드나 블럭 외부에 선언된다.   
'static' 키워드 없이 선언된다.   
두번째로 긴 scope을 갖는다.   
새 클래스 인스턴스가 생성될 때 생성되며 인스턴스가 메모리에서 제거 될 때까지 유지된다.   
Heap에 저장된다.   

## local variable이란?
메서드 본문 내에 선언된 변수이다.   
선언된 메서드가 스택에 남아있는 동안만 유지된다.   
Stack에 저장된다.

## block variable이란?
init block이나 for문과 같은 block 내에서 선언된 변수이다.   
block을 실행하는 동안에만 살고 가장 짧게 삶아있는 변수이다.    
Stack에 저장된다.

## final variable이란?
'final' 키워드로 선언된 변수이다.   
값을 변경할 수 없다.   
primitive variable일 경우 리터럴을 변경할 수 없다.   
reference variable이고 객체가 할당된 경우 다른 객체를 참조하도록 변경할 수 없다.   
참조하는 객체의 속성은 변경될 수 있다.   

## transient variable이란?
객체가 직렬화 될때 값이 직렬화되지 않는 변수이다.   
객체가 역직렬화 될때 primitive variable은 기본 값으로 초기화된다.   
객체가 역직렬화 될때 reference variable은 null로 초기화된다.   

## volatile variable이란?
여러 스레드가 객체의 변수에 접근하는 멀티 스레드 프로그래밍과 관련이 있다.   
'volatile' 키워드로 선언된다.
일반적인 변수의 경우 스레드는 변수의 값을 메모리에 캐싱하고 필요할 때 이 캐시된 값을 참조한다.   
다른 스레드에 의해 이 변수가 업데이트 되더라도 이 스레드에 반영되지 않는다.   

volatile variable은 JVM에 이 변수가 여러 스레드에 의해 업데이트되고 항상 메인 메모리에서 값을 가져오도록 지시한다.   
따라서 모든 스레드가 접근할때 메인 메모리에서 volatile variable 값을 얻고 스레드의 메모리에 값을 캐싱하지 않는다.   

## 참고
* [Java - Variables Interview Questions and Answers](https://www.interviewgrid.com/interview_questions/java/java_variables)
