# Java
* [primitive variable와 reference variable의 차이점](#primitive-variable와-reference-variable의-차이점)
* [Java 변수의 종류](#java-변수의-종류)
* [static variable이란?](#static-variable이란)
* [instance variable이란?](#instance-variable이란)
* [local variable이란?](#local-variable이란)
* [block variable이란?](#block-variable이란)
* [final variable이란?](#final-variable이란)
* [transient variable이란?](#transient-variable이란)
* [volatile variable이란?](#volatile-variable이란)
* [스레드의 동기화(synchronization)란?](#스레드의-동기화synchronization란)
* [동기화 블록 코드 예시](#동기화-블록-코드-예시)
* [static method를 동기화할 수 있나요?](#static-method를-동기화할-수-있나요)
* [Thread 클래스의 join 메서드에 대한 설명](#thread-클래스의-join-메서드에-대한-설명)
* [Thread 클래스의 주요 메서드](#thread-클래스의-주요-메서드)
* [교착상태(deadlock)이란?](#교착상태deadlock이란)
* [스레드 간 통신을 위해 중요한 Method는?](#스레드-간-통신을-위해-중요한-method는)
* [wait 메서드](#wait-메서드)
* [notify 메서드](#notify-메서드)
* [notifyAll 메서드](#notifyall-메서드)
* [wait 및 notify 메서드로 동기화된 프로그램 코드 예시](#wait-및-notify-메서드로-동기화된-프로그램-코드-예시)
* [Java에서 synchronization의 대안책은 무엇입니까?](#java에서-synchronization의-대안책은-무엇입니까)

## primitive variable와 reference variable의 차이점
primitive variable은 기본 리터럴 값을 갖는 변수이다.
* ex) int var1 = 123;   

reference variable은 Object에 대한 참조 값을 갖는 변수이다.
* ex) Box var2 = new Box();

[맨위로](#java)

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

[맨위로](#java)
## static variable이란?
메서드 또는 블록 외부에 선언되며 'static' 키워드로 선언된 변수이다.   
scope이 가장 길다.    
클래스가 로드될때 생성되며 클래스가 JVM에 로드된 상태로 유지되는 한 계속 메모리에 남아 있다.      
전역 변수이다.   
모든 객체간에 공유된다.   
클래스의 모든 인스턴스는 동일한 static variable을 공유한다.   
객체 인스턴스를 만들지 않고 클래스를 사용하여 접근할 수 있다.   
Heap에 저장된다.   

[맨위로](#java)
## instance variable이란?
메서드나 블럭 외부에 선언된다.   
'static' 키워드 없이 선언된다.   
두번째로 긴 scope을 갖는다.   
새 클래스 인스턴스가 생성될 때 생성되며 인스턴스가 메모리에서 제거 될 때까지 유지된다.   
Heap에 저장된다.   

[맨위로](#java)
## local variable이란?
메서드 본문 내에 선언된 변수이다.   
선언된 메서드가 스택에 남아있는 동안만 유지된다.   
Stack에 저장된다.

## block variable이란?
init block이나 for문과 같은 block 내에서 선언된 변수이다.   
block을 실행하는 동안에만 살고 가장 짧게 삶아있는 변수이다.    
Stack에 저장된다.

[맨위로](#java)
## final variable이란?
'final' 키워드로 선언된 변수이다.   
값을 변경할 수 없다.   
primitive variable일 경우 리터럴을 변경할 수 없다.   
reference variable이고 객체가 할당된 경우 다른 객체를 참조하도록 변경할 수 없다.   
참조하는 객체의 속성은 변경될 수 있다.   

[맨위로](#java)
## transient variable이란?
객체가 직렬화 될때 값이 직렬화되지 않는 변수이다.   
객체가 역직렬화 될때 primitive variable은 기본 값으로 초기화된다.   
객체가 역직렬화 될때 reference variable은 null로 초기화된다.   

[맨위로](#java)
## volatile variable이란?
여러 스레드가 객체의 변수에 접근하는 멀티 스레드 프로그래밍과 관련이 있다.   
'volatile' 키워드로 선언된다.
일반적인 변수의 경우 스레드는 변수의 값을 메모리에 캐싱하고 필요할 때 이 캐시된 값을 참조한다.   
다른 스레드에 의해 이 변수가 업데이트 되더라도 이 스레드에 반영되지 않는다.   

volatile variable은 JVM에 이 변수가 여러 스레드에 의해 업데이트되고 항상 메인 메모리에서 값을 가져오도록 지시한다.   
따라서 모든 스레드가 접근할때 메인 메모리에서 volatile variable 값을 얻고 스레드의 메모리에 값을 캐싱하지 않는다.   

[맨위로](#java)

## 스레드의 동기화(synchronization)란?
스레드는 병렬로 실행되기 때문에 스레드1과 스레드2가 동시에 데이터를 수정하면 동기화 문제가 발생한다.   
여러 스레드가 동일한 메서드를 실행하지 못하도록 방지하는 방법은 해당 메서드에 synchronized 키워드를 사용하는 것이다.   
메서드에 synchronized 키워드가 붙어 있다면 현재 이 메서드를 실행중인 스레드가 없을 경우에만 다른 스레드가 이 메서드에 접근할 수 있다.   
```
synchronized int setAndGetSum(int a1, int a2) {

  ...

}
```

[맨위로](#java)

## 동기화 블록 코드 예시
블록 안의 모든 코드는 현재 객체에서 동기화된다.
```
void synchronizedExample() {
    synchronized (this) {
        ...
    }
}
```

[맨위로](#java)

## static method를 동기화할 수 있나요?
동기화 할 수 있다.   
static method와 block은 클래스에서 동기화된다.   
instance method와 block은 클래스의 인스턴스에서 동기화된다.   
static synchorinized method와 instance synchronized method는 서로 영향을 주지 않는다.   

[맨위로](#java)

## Thread 클래스의 join 메서드에 대한 설명
thread의 join 메서드를 호출하면 해당 thread가 실행을 완료할 때까지 main 메소드의 실행을 강제로 중지한다.   
join메서드에 ms 단위의 시간을 매개 변수로 받는 메서드도 있다.   
```
thread.join(2000);
```
위 코드를 예로 들면 이 메서드는 최소 2000ms 또는 해당 스레드의 실행 종료를 기다린다.   

[맨위로](#java)

## Thread 클래스의 주요 메서드
yield 메서드
* static method이다.
* 스레드 상태가 RUNNING에서 RUNNABLE로 변경된다.
* 하지만 해당 스레드가 가장 우선순위가 높은 스레드일 경우 다시 RUNNING 상태로 변경할 수 있다.

sleep 메서드
* static method이다.
* InterruptedException을 던질 수 있다.
* 실행중인 스레드를 지정된 ms 동안 절전 상태로 전환한다.

[맨위로](#java)

## 교착상태(deadlock)이란?
thread1이 thread2를 기다리고 있고 thread2가 thread1을 기다리고 있는 상황.   
교착 상태에서 이 두 스레드는 서로를 영원히 기다린다.

[맨위로](#java)

## 스레드 간 통신을 위해 중요한 Method는?
wait, notify, notifyAll

[맨위로](#java)

## wait 메서드
Object 클래스에 정의되어 있다.   
notify를 받을때까지 대기한다.

[맨위로](#java)

## notify 메서드
Object 클래스에 정의되어 있다.   
다른 wait 중인 스레드에게 notify 한다.

[맨위로](#java)

## notifyAll 메서드
둘 이상의 스레드가 wait 상태인 경우 notifyAll 메서드를 사용하여 모든 스레드에게 notify 할 수 있다.

[맨위로](#java)

## wait 및 notify 메서드로 동기화된 프로그램 코드 예시
```
class Calculator extends Thread {

    long sumUptoMillion;
    long sumUptoTenMillion;

    public void run() {
        synchronized (this) {
            calculateSumUptoMillion();
            notify();
        }
        calculateSumUptoTenMillion();
    }

    private void calculateSumUptoMillion() {
        for (int i = 0; i < 1000000; i++) {
            sumUptoMillion += i;
        }
        System.out.println("Million done");
    }

    private void calculateSumUptoTenMillion() {
        for (int i = 0; i < 10000000; i++) {
            sumUptoTenMillion += i;
        }
        System.out.println("Ten Million done");
    }
}

class ThreadWaitAndNotify {

    public static void main(String[] args) throws InterruptedException {
        Calculator thread = new Calculator();
        synchronized(thread){
            thread.start();
            thread.wait();
        }
        System.out.println(thread.sumUptoMillion);
    }

}
```

[맨위로](#java)

## Java에서 synchronization의 대안책은 무엇입니까?
Java Concurrent Collections

[맨위로](#java)

## 참고
* [Java - Variables Interview Questions and Answers](https://www.interviewgrid.com/interview_questions/java/java_variables)
* [Java Synchronization Interview Questions](http://www.javainterview.in/p/java-synchronization-interview-questions.html)

[맨위로](#java)
