# Java
* [JVM의 구조](#jvm의-구조)
* [Java의 실행 방식](#java의-실행-방식)
* [GC에 대한 설명](#gC에-대한-설명)
* [컬렉션 프레임워크](#컬렉션-프레임워크)
* [제네릭](#제네릭)

## JVM의 구조
자바 가상 머신의 약자를 따서 줄여 부르는 용어로 JVM의 역할은 자바 애플리케이션을 클래스 로더를 통해 읽어 자바 API와 함께 실행하는 것이다.      
메모리 관리(GC)을 수행하며 스택기반의 가상머신이다.   
![JVM구조](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/JVM%EA%B5%AC%EC%A1%B0.png)

JVM의 구조는 Class Loader, Execution Engine, Runtime Data Area, JNI, Native Method Library로 이루어져 있다.   
* Class Loader(클래스 로더)
  * JVM내로 클래스를 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈

* Execution Engine(실행 엔진)
  * 바이트 코드를 실행시키는 역할
  * 인터프리터
    * 바이트 코드를 한줄 씩 실행한다.
  * JIT 컴파일러
    * 인터프리터 효율을 높이기 위한 컴파일러로 인터프리터가 반복되는 코드를 발견하면 JIT 컴파일러가 반복되는 코드를 네이티브 코드로 바꿔준다.   
    * 그 다음부터 인터프리터는 네이티브 코드로 컴파일된 코드를 바로 사용합니다.   
  * GC(Garbage Collector)
    * 가비지 컬렉터로 힙 영역에서 사용되지 않는 객체들을 제거하는 작업을 의미한다.

* Runtime Data Area
  * 프로그램 실행 중에 사용되는 다양한 영역이다.
  * PC Register
    * Thread가 시작될 때 생성되며 현재 수행 중인 JVM 명령의 주소를 갖고 있습니다.
  * Stack Area
    * 지역 변수, 파라미터 등이 생성되는 영역. 
    * 실제 객체는 Heap에 할당되고 해당 레퍼런스만 Stack에 저장된다.
  * Heap Area
    * 동적으로 생성된 오브젝트와 배열이 저장되는 곳으로 GC의 대상 영역이다.
  * Method Area
    * 클래스 멤버 변수, 메소드 정보, Type 정보, Constant Pool, static, final 변수 등이 생성된다.

* JNI(Java Native Interface)
  * C, C++, 어셈블리어로 작성된 함수를 사용할 수 있는 방법을 제공해준다.
* Native Method Library
  * C, C++로 작성된 라이브러리이다.

### 참고
* [Backend-Interview-Question](https://github.com/ksundong/backend-interview-question#java)
* [JVM 구조](https://goodgid.github.io/Java-JVM/)

## Java의 실행 방식
* 자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어 자바 바이트코드(.class)로 변환시킨다.
* Class Loader를 통해 class 파일들을 JVM으로 로딩한다.
* 로딩된 class 파일들은 Execution Engine을 통해 해석된다.
* 해석된 바이트코드는 Runtime Data Areas 에 배치되어 실질적인 수행이 이루어진다.

### 참고
* [Backend-Interview-Question](https://github.com/ksundong/backend-interview-question#java)

## GC에 대한 설명
### GC란 무엇인가
GC는 힙 영역에서 사용하지 않는 객체들을 제거하는 작업을 총칭한다.

### GC가 필요한 이유는 무엇인가
자바는 개발자가 메모리를 직접 해제해줄 수 없는 언어이다.   
따라서 객체를 사용하고 제거하는 기능이 필요하게 된다.   

### GC의 동작 방식
> 가장 간단한 Serial GC 방식으로 설명한다.   

![GC](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/GC.PNG)

GC는 Minor GC, Major GC로 구분할 수 있다.   
Minor GC는 young 영역에서, Major GC는 old 영역에서 일어난다고 정의한다.   
GC를 수행할 때는 GC를 수행하는 스레드 이외의 스레드는 모두 정지한다.   
* 이를 Stop-the-world라고 한다.

Minor GC
* Eden 영역이 가득 참에서 부터 시작된다.   
* Eden 영역에서 참조가 남아있는 객체를 mark하고 survivor 영역으로 복사한다.
* 그리고 Eden 영역을 비운다.
* Survivor 영역도 가득차면 같은 방식으로 다른 Survivor 영역에 복사하고 비운다.
* 이를 반복하다 보면 계속 해서 살아남는 객체는 old 영역으로 이동하게 된다.

Major GC
* old 영역에서 일어난다.
* 위와 반대로 삭제되어야 하는 객체를 mark한다.
* 그리고 지운다.(sweep)
* 메모리는 단편화 된 상태이므로 이를 한 군데에 모아주는 것을 Compaction이라 하며 compact라고 한다.
* 그래서 Mark-Sweep-Compact 알고리즘이라고 한다.

### 주의점
GC 수행시 시스템이 멈추기 때문에 의도치 않은 장애의 원인이 될 수 있다.   
따라서 이를 위해 힙 영역을 조정하는 것을 GC 튜닝이라고 하고 JVM 메모리는 절대 마음대로 조정해선 안된다.

### 참고
* [Backend-Interview-Question](https://github.com/ksundong/backend-interview-question#java)
* [JAVA GC (Garbage Collector)](https://code-factory.tistory.com/48)

## 컬렉션 프레임워크
널리 알려져 있는 자료구조를 바탕으로 객체, 데이터들을 효율적으로 관리 할 수 있는 자료구조들이 있는 라이브러리를 컬렉션 프레임워크라고 한다.   
List, Set은 Collection 인터페이스을 상속받지만, Map 인터페이스는 구조상의 차이라 별도로 정의한다.   

### 참고
* [Backend-Interview-Question](https://github.com/ksundong/backend-interview-question#java)

## 제네릭
제네릭은 자바의 타입 안정성을 맡고 있다.   
컴파일 과정에서 타입체크를 해주는 기능으로 객체의 타입을 컴파일 시에 체크하기 때문에 객체의 타입 안정성을 높이고 형변환의 번거로움을 줄여준다.   

### 참고
* [Backend-Interview-Question](https://github.com/ksundong/backend-interview-question#java)