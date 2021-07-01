# Java
* [JVM](#jvm)
  * [JVM, JRE, JDK의 차이점](#jvm-jre-jdk의-차이점)
  * [Java가 플랫폼에 독립적인 이유](#java가-플랫폼에-독립적인-이유)
  * [바이트코드(bytecode)](#바이트코드bytecode)
  * [클래스 로더(Class Loader)](#클래스-로더class-loader)
  * [클래스 로더 종류](#클래스-로더-종류)
  * [클래스 로드 단계](#클래스-로드-단계)
  * [Runtime Data Area(런타임 데이터 영역)](#runtime-data-area런타임-데이터-영역)
  * [JVM의 Java 프로그램 실행 단계](#jvm의-java-프로그램-실행-단계)
* [Variable(변수)](#variable변수)
  * [Java 변수 종류](#java-변수-종류)
  * [Final variable](#final-variable)
  * [Transient variable](#transient-variable)
  * [Volatile variable](#volatile-variable)
* [Synchronization(동기화)]()
  * [스레드 동기화]()
  * [static 메서드 동기화]()
  * [Thread 클래스의 메서드 종류]()
  * [Deadlock(교착 상태)]()
  * [스레드 간 통신할 때 주요한 메서드]()
  
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## JVM
### JVM, JRE, JDK의 차이점
JVM
* Java Virtual Machine
* java 바이트코드를 해석하고 실행하는 가상 머신입니다.
* java 프로그램을 컴파일하면 바이트코드로 이루어진 .class 파일이 생성됩니다.
* JVM은 바이트코드를 해석하고 .class 파일을 실행할 수 있습니다.
* 윈도우, 리눅스 등 OS 별로 JVM이 구현되어 있습니다.
  * 각 JVM은 모두 동일한 .class 파일을 실행할 수 있습니다.
  * 이러한 이유로 Java는 플랫폼에 독립적입니다.   
    * [Java가 플랫폼에 독립적인 이유 상세 설명](#java가-플랫폼에-독립적인-이유)

JRE
* Java Runtime Environment
* JVM을 구현합니다.
  * Java 프로그램을 실행하기 위해 필요한 라이브러리 및 기타 구성 요소를 지원합니다.
* Java 프로그램의 두 가지 배포 방법을 가능하게 하는 구성요소를 제공합니다.

JDK
* Java Development Kit
* JRE + (개발자가 Java 프로그램을 개발하는데 필요한 컴파일러, 디버거 등의 툴)

[맨위로](#java)

### Java가 플랫폼에 독립적인 이유
Java 프로그램을 컴파일하면 바이트코드로 이루어진 .class 파일이 생성됩니다.   
JVM은 바이트코드를 해석하고 Java 프로그램을 실행시켜줍니다.   
JVM은 특정 플랫폼(윈도우, 리눅스 등) 별로 구현됩니다.   
각 플랫폼 별 JVM은 동일한 .class 파일을 실행시킬 수 있습니다.   
따라서 Java는 한번 작성 및 컴파일하면 모든 플랫폼에서 실행시킬 수 있기 때문에 플랫폼에 독립적인 것입니다.   

[맨위로](#java)

### 바이트코드(bytecode)
개발자가 프로그램을 개발할 때 사용하는 언어인 Java와 프로그램을 실행하는 기계어의 중간 언어입니다.   
Java 프로그램을 컴파일하면 바이트코드로 이루어진 .class 파일이 생성됩니다.   
JVM은 클래스 로더를 통해 Java 클래스를 로드하고 실행시킵니다.   

[맨위로](#java)

### 클래스 로더(Class Loader)
런타임 시 클래스 파일을 로드하는 JVM의 구성 요소입니다.   

클래스 로더의 특징
* Hierarchy(계층)
  * 부모-자식 관계가 있는 계층 구조입니다.
  * Bootstrap class loader(부트스트랩 클래스 로더)가 모든 클래스 로더의 최상위 부모입니다.
* Delegation model(위임 모델)
  * 클래스를 로드하기 전에 부모 클래스 로더가 해당 클래스를 이미 로드했는지 확인합니다.
  * 부모 클래스 로더가 해당 클래스를 이미 로드한 경우 해당 클래스가 사용됩니다.
  * 부모 클래스 로더가 클래스를 로드하지 않은 경우 자식 클래스 로더가 클래스를 로드하여 사용합니다.
* Visibility(가시성)
  * 자식 클래스 로더는 부모 클래스 로더의 클래스를 찾을 수 있지만 부모 클래스 로더는 하위 클래스 로더의 클래스를 찾을 수 없습니다.
* Deletion(삭제)
  * 클래스 로더가 클래스를 로드한 후에는 그 클래스를 다시 언로드 할 수 없습니다.
  * 그래서 클래스 로더를 삭제하고 새로운 클래스 로더를 생성하는 옵션이 있습니다.

[맨위로](#java)

### 클래스 로더 종류
4개의 주요 클래스 로더가 있습니다.   
* Bootstrap class loader(부트스트랩 클래스 로더)
  * 클래스 로더 계층 중 최상위 클래스 로더입니다.
  * Java API 클래스를 로드합니다.
* Extension class loader(확장 클래스 로더)
  * Java API 확장 클래스를 로드합니다.
* System class loader(시스템 클래스 로더)
  * 사용자 또는 애플리케이션이 정의한 클래스 경로(class-path)에서 모든 애플리케이션 관련 클래스 파일을 로드합니다.
* User defined class loader(사용자 정의 클래스 로더)
  * 프레임워크 또는 애플리케이션 서버에 의해 정의된 클래스 로더입니다.

[맨위로](#java)

### 클래스 로드 단계
클래스가 로드되고 초기화되는 단계는 다음과 같습니다.
* Load(로드)
  * 클래스 파일이 JVM 메모리에 로드됩니다.
* Verify(검증)
  * 클래스가 Java 언어 및 JVM 스펙에 준수하는지 확인합니다.
* Prepare(준비)
* Resolve(분석)
  * 심볼릭 레퍼런스를 실제 레퍼런스로 변경합니다.
* Initialize(초기화)
  * 클래스 변수 및 static 변수를 초기화합니다.

[맨위로](#java)

### Runtime Data Area(런타임 데이터 영역)
JVM을 실행할 때 OS로부터 할당된 메모리 영역입니다.   
런타임 데이터 영역은 두 종류가 있습니다.
* 각 스레드마다 생성되는 영역
* 모든 스레드가 공유하는 영역

각 스레드마다 생성되는 영역은 PC Register, JVM Stack, Navive Method Stack이 있습니다.
* PC Register
  * Program Counter Register
  * PC Register에는 현재 실행 중인 JVM 명령의 주소가 있습니다.
  * 각 JVM 스레드가 시작될 때 해당 스레드에 PC Register가 생성됩니다.
* JVM Stack
  * 각 JVM 스레드에 생성되며 Stack Frame을 저장합니다.
  * 메서드가 실행되면 Stack Frame이 생성되어 JVM Stack에 추가되고, 메서드가 종료되면 JVM Stack에서 제거됩니다.
* Native Method Stack
  * Java 이외의 언어로 작성된 Native Data의 Stack이며, JNI를 통해 호출됩니다.
    * JNI: Java Native Interface
  * 각 스레드에는 고유한 Native Method Stack이 있습니다.

모든 스레드가 공유하는 영역은 Heap, Method area, Runtime Constant Pool(런타임 상수 풀)이 있습니다.
* Heap
  * Java 객체 인스턴스가 저장되고 Java Garbage Collector에 의해 제거되는 메모리 영역입니다.
  * JVM 성능 향상을 위해 튜닝되는 메모리 영역 중 하나입니다.
* Method area
  * Runtime Constant Pool(런타임 상수 풀), 필드 및 메서드 정보, 모든 클래스의 static 변수 및 메서드 바이트코드, JVM에 로드된 인터페이스가 저장됩니다.
* Runtime constant pool(런타임 상수 풀)
  * 각 클래스 및 인터페이스의 상수와 메서드 및 필드에 대한 모든 참조가 포함됩니다.
  * 메서드 또는 필드가 참조되면 JVM은 Runtime constant pool(런타임 상수 풀)에서 메서드 또는 필드의 실제 주소를 가져옵니다.

[맨위로](#java)

### JVM의 Java 프로그램 실행 단계
Java 프로그램(.java 파일)은 컴파일러(javac)를 통해 바이트코드(.class 파일)로 컴파일됩니다.   
클래스 로더는 컴파일된 Java 바이트코드를 런타임 데이터 영역으로 로드합니다.   

런타임 데이터 영역에 로드된 class 파일(또는 바이트코드)는 JVM의 Execution engine(실행 엔진)에 의해 실행됩니다.   
Execution engine(실행 엔진)은 실행하기 전에 바이트코드를 읽고 해당 OS가 이해할 수 있는 네이티브 코드로 변환시킵니다.   

Execution engine(실행 엔진)은 바이트코드를 네이티브 코드로 변환하는 데 두 가지를 사용합니다.
* Interpreter
  * Execution engine(실행 엔진)은 바이트코드를 한줄씩 읽고 해석하여 실행합니다.   
  * 바이트코드를 해석한 다음 실행해야 하므로 실행 속도가 느립니다.
* JIT (Just In Time) Compiler
  * JIT (Just In Time) Compiler가 전체 바이트코드를 네이티브 코드로 컴파일하는 동안 Execution engine(실행 엔진)은 먼저 Interpreter를 실행합니다.
  * 네이티브 코드가 생성되면 Execution engine(실행 엔진)은 더이상 바이트코드를 해석하지 않고 네이티브 코드를 직접 실행합니다.

[맨위로](#java)

## Variable(변수)
### Java 변수 종류
Java에는 기본적으로 Privimitive Variable와 Reference variable라는 두 가지 변수가 있습니다.  
Privimitive Variable은 기본 리터럴 값이고, Reference variable는 객체에 대한 참조 값입니다.   
```
class MyClass {

	//Primitive variable - var1,
	//var1은 리터럴 값 123.
	int var1 = 123; 

	//Reference variable - var2,
	//var2는 객체에 대한 참조 값 'Box'.
	Box var2 = new Box(); 

}
```

scope에 따라 변수는 Class variable, Instance variable, Local variable, Block variable 4가지 유형으로 나뉩니다.   
변수의 scope은 Java 클래스 내에 선언된 위치에 따라 결정됩니다.   
* Class variable (Static fields)
  * 클래스 본문 내에서 메서드 또는 블록 외부에 선언되며 'static' 키워드가 붙습니다.   
  * scope이 가장 깁니다.
  * 클래스가 로드될 때 생성되며 클래스가 JVM에서 로드된 상태로 유지되는 한 메모리에 유지됩니다.
  * global variable(전역 변수) 입니다.
  * 클래스 레벨의 모든 객체 간에 공유됩니다.
  * 클래스의 모든 인스턴스는 동일한 static variable을 공유합니다.
  * 객체 인스턴스를 생성하지 않고 클래스를 사용하여 접근할 수 있습니다.
  * JVM의 Method Area에 저장되며 변수 Type이 Reference Type일 경우 인스턴스는 Heap에 저장됩니다.
* Instance variables (Non-static fields)
  * 클래스 본문 내에서 메서드 또는 블록 외부에 선언되며 'static' 키워드가 붙지 않습니다.
  * scope이 Class variable 다음으로 두 번째로 깁니다.
  * 새 클래스 인스턴스가 생성될 때 생성되며 인스턴스가 메모리에서 제거될 때까지 메모리에 유지됩니다.
  * JVM의 Heap에 저장됩니다.
* Local Variables
  * 메서드 본문 내에 선언된 변수입니다.
  * 선언된 메서드가 Stack에 남아 있는 동안만 메모리가 유지됩니다.
  * JVM의 Stack에 저장되며 변수 Type이 Reference Type일 경우 인스턴스는 Heap에 저장됩니다.
* Block variable
  * init(초기화) 블록이나 for 루프와 같은 블록 내에서 선언된 변수입니다.
  * scope이 가장 짧은 변수입니다.
  * 블록 실행 동안에만 메모리가 유지됩니다.
  * JVM의 Stack에 저장되며 변수 Type이 Reference Type일 경우 인스턴스는 Heap에 저장됩니다.

```
class MyClass {

	//Static variable
	static String string1 = 'test string 1';

	//Instance variable
	String string2 = 'test string 2';

	//Block variable in init block
	{
        String string3 = 'test string 3'
    }

	void perform() {
		//Local variable 
		String string4 = 'test string 4' 

		//Block variable in for loop
		for (int i=0; i < 4; i++) {
            ...
        }
	}

}
```

![1](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Java/1.PNG)

[맨위로](#java)

### Final variable
'final' 키워드로 선언된 변수입니다.   
final variable로 선언되면 값을 변경할 수 없습니다.   

Final variable가 primitive type인 경우 리터럴 값을 변경할 수 없습니다.

Final variable가 reference type이면서 객체가 할당된 경우 다른 객체를 참조하도록 변경할 수 없습니다.   
하지만 참조하고 있는 객체의 속성 값은 변경할 수 있습니다.   

```
class MyClass {

	//final primitive variable - var1,
	//123에서 다른 리터럴 값으로 변경할 수 없습니다.
	final int var1 = 123;

	//final reference variable - var2
	//var2를 다른 Box 객체로 변경할 수 없습니다,
	//현재 Box 객체의 속성 값은 변경할 수 있습니다.
	final Box var2 = new Box();

}
```

[맨위로](#java)

### Transient variable
객체의 serialization(직렬화) 중에 값이 serialization(직렬화)되지 않는 변수입니다.   
객체가 역직렬화될 때 transient primitive variable은 default 값으로 초기화됩니다.   
객체가 역직렬화될 때 Transient reference variable은 null로 초기화됩니다.

```
class MyClass {

	// Transient variable
	transient int var1 = 123;

}
```

[맨위로](#java)

### Volatile variable
여러 스레드가 객체의 변수에 접근하는 멀티 스레드 프로그래밍과 관련이 있습니다.   
'volatile' 키워드로 선언됩니다.   

일반(non-volatile) variable의 경우 스레드는 변수 값을 메모리에 캐싱하고 필요한 경우 이 캐싱된 값을 참조합니다.   
다른 스레드에 의해 이 변수가 업데이트되더라도 이 스레드에는 반영되지 않습니다.   

Volatile variable의 경우 JVM의 메인 메모리에서 이 변수가 여러 스레드에 의해 업데이트되며 각 스레드는 항상 메인 메모리에서 값을 가져옵니다.   
따라서 모든 스레드는 메모리에 변수 값을 캐싱하여 사용하지 않고 메인 메모리에서 volatile variable의 값에 접근하게 됩니다.   

```
class MyClass {

	// Volatile variable
	volatile int var1 = 123;

}
```

[맨위로](#java)

## Synchronization(동기화)
### 스레드 동기화
스레드는 병렬로 실행되기 때문에 하나의 스레드는 데이터를 읽고 다른 하나의 스레드는 해당 데이터를 수정하는 하는 것과 같은 동기화 문제가 발생합니다.   


메서드에 'synchronized' 키워드를 붙이면 여러 스레드가 동일한 메서드를 동시에 실행하지 못하도록 막을 수 있습니다.   
```
synchronized int setandGetSum(int a1, int a2, int a3) {
    cell1 = a1;
    sleepForSomeTime();
    cell2 = a2;
    sleepForSomeTime();
    cell3 = a3;
    sleepForSomeTime();
    return cell1 + cell2 + cell3;
}
```

블럭에 'synchronized' 키워드를 붙이면 여러 스레드가 동일한 블럭을 동시에 실행하지 못하도록 막을 수 있습니다. 
```
void synchronizedExample2() {
    synchronized (this){
        //All code goes here..
    }
}
```

[맨위로](#java)

### static 메서드 동기화
static 메서드와 static 블록은 클래스 기준으로 동기화됩니다.   
instance 메서드와 블록은 생성된 객체 인스턴스 기준으로 동기화됩니다.   
따라서 static 동기화 메서드와 instance 동기화 메서드는 서로 전혀 영향을 주지 않습니다.   
```
synchronized static int getCount(){
    return count;
}

static int getCount2(){
    synchronized (SynchronizedSyntaxExample.class) {
        return count;
    }
}
```
여기서 서로 다른 스레드에서 getCount()와 getCount2()를 각각 호출해도 count에 접근하는 것은 서로 영향을 주지 않습니다.   

[맨위로](#java)

### Thread 클래스의 메서드 종류
join 메서드
* Thread 클래스의 instance 메서드입니다.   
* join() 메서드를 호출한 스레드가 완료될 때까지 메인 메서드의 실행을 강제로 중지합니다.   
```
thread3.start();
thread2.start();
thread3.join();// 스레드3이 완료될 때까지 메인 메서드는 중지됩니다.
System.out.println("Thread3 is completed.");
thread4.start();
```
* 오버로드된 join 메서드
  * 시간(milliseconds)을 매개 변수로 받는 오버로드 된 join 메서드도 있습니다.
  * 아래 예시에서 메인 메서드는 2000ms 또는 스레드4 실행 종료 중 최소값까지 중지됩니다.
  ```
  thread4.join(2000);
  ```

yield 메서드
* Thread 클래스의 static 메서드입니다.
* 스레드의 상태를 RUNNING에서 RUNNABLE로 변경합니다.
* 하지만 해당 스레드의 우선 순위가 가장 높을 경우 스케줄러는 다시 해당 스레드를 선택하여 실행할 수 있습니다.

sleep 메서드
* Thread 클래스의 static 메서드입니다.
* InterruptedException이 발생할 수 있습니다.
* 스레드가 지정된 시간(milliseconds) 동안 일시정지가 됩니다.

[맨위로](#java)

### Deadlock(교착 상태)
스레드1이 스레드2를 기다리고 스레드2가 스레드1을 기다리는 상태를 교착 상태라고 합니다.   
교착 상태에서는 이러한 두 스레드가 서로를 영원히 기다립니다.   

[맨위로](#java)

### 스레드 간 통신할 때 주요한 메서드
wait 메서드
* Object 클래스에 정의되어 있습니다.
* notify 될 때까지 스레드가 대기하게 됩니다.
```
synchronized(thread){
    thread.start();
    thread.wait();
}
```

notify 메서드
* Object 클래스에 정의되어 있습니다.
* wait 중인 스레드에게 notify 요청 보냅니다.
```
synchronized (this) {
    calculateSumUptoMillion();
    notify();
}
```

notifyAll 메서드
* wait 상태인 스레드가 둘 이상인 경우 해당 스레드들에게 notify 요청을 보냅니다.
```
thread.notifyAll();
```

[맨위로](#java)

## 참고
* [Java - JVM Internals Interview Questions and Answers](https://www.interviewgrid.com/interview_questions/java/java_jvm_internals)
* [Java - Variables Interview Questions and Answers](https://www.interviewgrid.com/interview_questions/java/java_variables)
* [Java Synchronization Interview Questions](http://www.javainterview.in/p/java-synchronization-interview-questions.html)

[맨위로](#java)
