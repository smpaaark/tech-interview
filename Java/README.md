# Java
* [JVM의 구조](#jvm의-구조)
* [Java의 실행 방식](#java의-실행-방식)

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