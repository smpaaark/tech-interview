# Java
* [JVM, JRE, JDK의 차이점]()
* [Java가 플랫폼에 독립적인 이유]()
* [바이트코드(bytecode)]()
* [JVM이 Java 프로그램을 실행하는 방법]()
* [클래스 로더(Class Loader)]()
* [클래스 로더 종류]()
* [클래스 로드 단계]()
* [Runtime Data Area(런타임 데이터 영역)]()
* [JVM의 Java 프로그램 실행 단계]()

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
* [동기화 코드 예시](#동기화-코드-예시)
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
* [immutable class가 무엇입니까?](#immutable-class가-무엇입니까)
* [immutable class를 만드는 방법은 무엇입니까?](#immutable-class를-만드는-방법은-무엇입니까)
* [아래의 Employee 클래스는 immutable인가요?](#아래의-employee-클래스는-immutable인가요)
* [위의 Employee 클래스를 immutable로 만드려면 어떻게 해야 합니까?](#위의-employee-클래스를-immutable로-만드려면-어떻게-해야-합니까)
* [immutable 클래스의 예시](#immutable-클래스의-예시)
* [immutable 클래스는 Thread safe 합니까?](#immutable-클래스는-thread-safe-합니까)
* [mutable 인스턴스 변수를 사용하는 경우 어떤 조치를 취해야 합니까?](#mutable-인스턴스-변수를-사용하는-경우-어떤-조치를-취해야-합니까)
* [immutable 객체가 HashMap에 적합한 key로 간주되는 이유는 무엇입니까?](#immutable-객체가-hashmap에-적합한-key로-간주되는-이유는-무엇입니까)
* [immutable 클래스의 좋은 예](#immutable-클래스의-좋은-예)
* [ConcurrentHashMap이란 무엇입니까?](#concurrenthashmap이란-무엇입니까)
* [ConcurrentHashMap은 Thread-safe 합니까?](#concurrenthashmap은-thread-safe-합니까)
* [ConcurrentHashMap은 어떤 원리로 thread-safe 합니까?](#concurrenthashmap은-어떤-원리로-thread-safe-합니까)
* [여러 스레드가 동시에 ConcurrentHashMap 값을 읽을 수 있습니까?](#여러-스레드가-동시에-concurrenthashmap-값을-읽을-수-있습니까)
* [ConcurrentHashMap 내부적으로 어떻게 작동합니까?](#concurrenthashmap-내부적으로-어떻게-작동합니까)
* [ConcurrentHashMap에서 값을 어떻게 자동으로 업데이트합니까?](#concurrenthashmap에서-값을-어떻게-자동으로-업데이트합니까)
* [ConcurrentHashMap을 순회하면서 map을 제거하려면 어떻게 해야 합니까?](#concurrenthashmap을-순회하면서-map을-제거하려면-어떻게-해야-합니까)
* [ConcurrentHashMap의 Iterator는 fail-safe 입니까 fail-fast 입니까?](#concurrenthashmap의-iterator는-fail-safe-입니까-fail-fast-입니까)
* [한 스레드가 반복되는 동안 ConcurrentHashMap에 새로운 매핑을 추가하면 어떻게 됩니까?](#한-스레드가-반복되는-동안-concurrenthashmap에-새로운-매핑을-추가하면-어떻게-됩니까)
* [Map 타입 변수에 ConcurrentHahsMap를 전달할 수 있습니까?](#map-타입-변수에-concurrenthahsmap를-전달할-수-있습니까)
* [Atomic 데이터 타입이 무엇입니까?](#atomic-데이터-타입이-무엇입니까)
* [Atomic 데이터 타입의 종류](#atomic-데이터-타입의-종류)
* [Atomic 데이터 타입은 언제 사용할 수 있습니까?](#atomic-데이터-타입은-언제-사용할-수-있습니까)
* [Atomic 데이터 타입, volatile 변수, synchronization의 차이점은 무엇입니까?](#atomic-데이터-타입-volatile-변수-synchronization의-차이점은-무엇입니까)
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## primitive variable와 reference variable의 차이점
Java에는 기본적으로 primitive variable과 reference variable이라는 2가지 변수가 있습니다.   
primitive variable은 리터럴 값이고, reference variable은 객체에 대한 참조 값입니다.   
```
class MyClass {
	//primitive variable 선언 - var1,
	//var1은 리터럴 값 123
	int var1 = 123; 

	//Reference variable 선언 - var2,
	//var2은 'Box' 타입의 객체에 대한 참조값
	Box var2 = new Box(); 
}
```

[맨위로](#java)

## Java 변수의 종류
Java에는 기본적으로 primitive variable과 reference variable이라는 2가지 변수가 있습니다.   
primitive variable은 리터럴 값이고, reference variable은 객체에 대한 참조 값입니다.   

scope에 따라 변수는 class variable, instance variable, local variable, block variable 4가지로 나뉠수 있습니다.         
변수의 scope은 Java 클래스 내에서 선언된 위치에 따라 결정됩니다.   
* Class variable(static field)
  * 클래스 본문 내에서 메서드 또는 블록 외부에 선언된 변수이며, 'static' 키워드로 선언됩니다.   
  * scope이 가장 깁니다.
    * 클래스가 로드될 때 생성되며 클래스가 JVM에서 로드된 상태로 유지되는 한 메모리에 유지됩니다.   

* Instance variable(Non-static field)
  * 클래스 본문 내에서 메서드 또는 블록 외부에 선언된 변수이며, 'static' 키워드 없이 선언된 변수입니다.   
  * scope이 두번째로 깁니다.   
    * 새 클래스 인스턴스가 생성될 때 생성되며, 인스턴스가 메모리에서 제거될 때까지 유지됩니다.   
* Local variable
  * 메서드 본문 내에 선언된 변수입니다.
  * 선언된 메서드가 스택에 남아 있는 동안만 유지됩니다.   
* Block variable
  * init block 또는 for 루프와 같은 block 내에서 선언된 변수입니다.   
  * block을 실행하는 동안에만 유지되며 scope이 가장 짧은 변수입니다.   

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

[맨위로](#java)

## static variable이란?
클래스 본문 내에서 메서드 또는 블록 외부에 선언된 변수이며, 'static' 키워드로 선언됩니다.  
scope이 가장 깁니다.   
* 클래스가 로드될 때 생성되며 클래스가 JVM에서 로드된 상태로 유지되는 한 메모리에 유지됩니다.      

전역 변수입니다.   
* 모든 객체간에 공유됩니다.      
* 클래스의 모든 인스턴스는 동일한 static variable을 공유합니다.      

객체 인스턴스를 만들지 않고 클래스를 사용하여 접근할 수 있습니다.   
Heap에 저장됩니다.   

```
class MyClass {
	//Static variable
	static String string1 = 'test string 1';
}
```

[맨위로](#java)

## instance variable이란?
클래스 본문 내에서 메서드 또는 블록 외부에 선언된 변수이며, 'static' 키워드 없이 선언된 변수입니다.   
scope이 두번째로 깁니다.   
* 새 클래스 인스턴스가 생성될 때 생성되며, 인스턴스가 메모리에서 제거될 때까지 유지됩니다.  

Heap에 저장됩니다.   

```
class MyClass {
	//instance variable
	String string1 = 'test string 1';
}
```

[맨위로](#java)

## local variable이란?
메서드 본문 내에 선언된 변수입니다.   
선언된 메서드가 스택에 남아 있는 동안만 유지됩니다.   
Stack에 저장됩니다.   

```
class MyClass {
	void perform() {
		//Local variable 
		Integer speed = 100;
	}
}
```

[맨위로](#java)

## block variable이란?
init block 또는 for 루프와 같은 block 내에서 선언된 변수입니다.   
block을 실행하는 동안에만 유지되며 scope이 가장 짧은 변수입니다.   
Stack에 저장됩니다.   

```
class MyClass {
	//Block variable in for loop
		for (int i=0; i < 4; i++) {...}
	}
}
```

[맨위로](#java)

## final variable이란?
'final' 키워드로 선언된 변수입니다.   
값을 변경할 수 없습니다.   

primitive variable일 경우 리터럴을 변경할 수 없습니다.   
reference variable이고 객체가 할당된 경우 다른 객체를 참조하도록 변경할 수 없습니다.   
* 참조하는 객체의 속성은 변경될 수 있습니다.   

```
class MyClass {
	//final primitive variable var1,
	//var1 값은 123에서 변경할 수 없습니다.
	final int var1 = 123;

	//final reference variable - var2
	//var2는 다른 Box 객체를 참조하도록 변경할 수 없습니다.
	//Box 객체의 속성은 변경될 수 있습니다.
	final Box var2 = new Box();
}
```

[맨위로](#java)

## transient variable이란?
객체가 직렬화 될 때 값이 직렬화되지 않는 변수입니다.      
객체가 역직렬화 될 때 primitive variable은 기본 값으로 초기화됩니다.   
객체가 역직렬화 될 때 reference variable은 null로 초기화됩니다.   

```
class MyClass {
	// Transient variable
	transient int var1 = 123;
}
```

[맨위로](#java)

## volatile variable이란?
여러 스레드가 객체의 변수에 접근하는 멀티 스레드 프로그래밍과 관련이 있습니다.   
'volatile' 키워드로 선언됩니다.   

일반적인 변수의 경우 스레드는 변수의 값을 메모리에 캐싱하고 필요한 경우 이 캐시된 값을 참조합니다.      
* 다른 스레드에 의해 이 변수가 업데이트된 내용은 이 스레드에 반영되지 않습니다.   

JVM에 이 변수가 여러 스레드에 의해 업데이트되며 항상 메인 메모리에서 값을 가져오도록 한다.      
* 따라서 모든 스레드는 메인 메모리에서 volatile variable의 값에 접근하고 스레드 메모리에 값을 캐싱하지 않습니다.   

```
class MyClass {
	// Volatile variable
	volatile int var1 = 123;
}
```

[맨위로](#java)

## 스레드의 동기화(synchronization)란?
스레드는 병렬로 실행되기 때문에 스레드1과 스레드2가 동시에 데이터를 수정하는 문제가 발생할 수 있습니다.    
이 문제를 동기화 문제라고 합니다.   

동기화 문제를 해결하기 위한 방법은 'synchronized' 키워드를 사용하는 것입니다.   
* 이 경우 스레드는 현재 실행중인 다른 스레드가 없는 경우에만 접근할 수 있습니다.   


[맨위로](#java)

## 동기화 코드 예시
메서드 동기화   
* 메서드 안의 모든 코드는 동기화된다.   

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

블록 동기화   
* 블록 안의 모든 코드는 동기화된다.

```
void synchronizedExample2() {
    synchronized (this){
        code...
    }
}
```

[맨위로](#java)

## static method를 동기화할 수 있나요?
동기화 할 수 있습니다.   
static method와 block은 클래스에서 동기화됩니다.   
instance method와 block은 클래스의 인스턴스에서 동기화됩니다.   
static synchorinized method와 instance synchronized method는 서로 영향을 주지 않습니다.   

[맨위로](#java)

## Thread 클래스의 join 메서드에 대한 설명
thread의 join 메서드를 호출하면 해당 thread가 실행을 완료할 때까지 main 메소드의 실행을 강제로 중지합니다.   
join메서드에 ms 단위의 시간을 매개 변수로 받는 오버로드된 메서드도 있습니다.   

```
thread.join(2000);
```
위 코드를 예로 들면 메인 메서드는 2000ms 또는 해당 스레드의 실행 종료 중 최소 시간 동안 중지합니다.     

[맨위로](#java)

## Thread 클래스의 주요 메서드
yield 메서드
* static method입니다.   
* 다른 스레드에게 실행을 양보하는 개념입니다.   
  * 스레드 상태를 RUNNING에서 RUNNABLE로 변경합니다.   
  * 하지만 해당 스레드가 가장 우선순위가 높은 스레드일 경우 다시 RUNNING 상태로 변경될 수 있습니다.   

sleep 메서드
* static method입니다.  
* InterruptedException을 던질 수 있습니다.   
* 실행중인 스레드가 지정된 시간(ms) 동안 절전 모드로 전환됩니다.   

[맨위로](#java)

## 교착상태(deadlock)이란?
thread1이 thread2를 기다리고 thread2가 thread1을 기다리고 있는 상황을 교착상태라고 합니다.      
교착 상태에서 이 두 스레드는 서로를 영원히 기다립니다.   

[맨위로](#java)

## 스레드 간 통신을 위해 중요한 Method는?
wait, notify, notifyAll 메서드입니다.   

[맨위로](#java)

## wait 메서드
Object 클래스에 정의되어 있습니다.   
notify를 받을때까지 스레드가 대기하게 됩니다.   

[맨위로](#java)

## notify 메서드
Object 클래스에 정의되어 있습니다.   
다른 wait 중인 스레드에게 notify하는 것입니다.   
* [wait 메서드](#wait-메서드) 설명 참고   

[맨위로](#java)

## notifyAll 메서드
둘 이상의 스레드가 wait 상태인 경우 notifyAll 메서드를 사용하여 모든 스레드에게 notify 할 수 있습니다.   

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

결과
```
Million done
499999500000
Ten Million done
```

[맨위로](#java)

## Java에서 synchronization의 대안책은 무엇입니까?
Java는 스레드의 동시성을 해결을 위해 Concurrent Collections을 도입했습니다.   

[맨위로](#java)

## immutable class가 무엇입니까?
생성되면 상태를 변경할 수 없는 객체입니다.   
* ex) String, Integer ...

[맨위로](#java)

## immutable class를 만드는 방법은 무엇입니까?
* final 클래스로 만듭니다.
  * 클래스를 final 클래스로 만들면 클래스를 확장할 수 없으므로 이 클래스의 메서드를 재정의할 수 없습니다.   
* 모든 인스턴스 변수를 private final로 선언합니다.
  * 인스턴스 변수를 private으로 설정하면 외부 클래스가 인스턴스 변수에 접근할 수 없으며, final로 설정하면 변경할 수 없습니다.   
* setter 메서드를 만들지 않습니다.
  * 인스턴스 변수에 대한 setter 메서드를 만들지 않으면 인스턴스 변수를 변경할 방법은 없습니다.
* 생성자에서 모든 변수를 초기화합니다.
* getter 메서드에서 mutable 객체로 복사하여 리턴합니다.
  * 원래 객체가 리턴되지 않으므로 원래 객체는 그대로 유지됩니다.

[맨위로](#java)

## 아래의 Employee 클래스는 immutable인가요?
```
package org.arpit.java2blog.bean;
import java.util.ArrayList;
 
public final class Employee {
 
    private final String name;
    private final ArrayList addresses;

    public Employee(String name, ArrayList addresses) {
        super();
        this.name = name;
        ArrayList tempAdd=new ArrayList();
        for (int i = 0; i < addresses.size(); i++) {
            tempAdd.add(addresses.get(i));
        }
        this.addresses = tempAdd;
    }
    
    public String getName() {
        return name;
    }

    public ArrayList getAddresses() {
        return addresses;
    } 

}
```
immutable 클래스가 아닙니다.   
왜냐하면 employee.getAddress().add("New address")를 통해 직원을 계속 추가할 수 있기 때문입니다.   

[맨위로](#java)

## 위의 Employee 클래스를 immutable로 만드려면 어떻게 해야 합니까?
```
public ArrayList getAddresses() {
    return (ArrayList) addresses.clone();
}
```
getAddress() 메서드에서 addresses의 clone 객체를 반환해야 합니다.   
그러면 employee.getAddress().add("New address")를 해도 실제 addresses에는 아무 영향이 없습니다.   

[맨위로](#java)

## immutable 클래스의 예시
```
package org.arpit.java2blog.bean;
 
import java.util.ArrayList;
 
public final class Country {

    // declared private final instance variable
    private final String countryName;
    // Mutable object
    private final ArrayList listOfStates;

    public Country(String countryName, ArrayList listOfStates) {
        super();
        this.countryName = countryName;
        // Creating deep copy for mutable object
        ArrayList tempList = new ArrayList();

        for (int i = 0; i < listOfStates.size(); i++) {
            tempList.add(listOfStates.get(i));
        }
        this.listOfStates = tempList;
    }

    public String getCountryName() {
        // Do not need to do cloning as it is immutable object
        return countryName;
    }

    public ArrayList getListOfStates() {
        // Returning cloned object 
        return (ArrayList) listOfStates.clone();
    }
}
```

[맨위로](#java)

## immutable 클래스는 Thread safe 합니까?
Immutable 클래스는 객체의 상태를 변경할 수 없으므로 thread safe 합니다.   
그래서 두 개의 스레드가 동시에 접근해도 아무 문제가 없습니다.   

[맨위로](#java)

## mutable 인스턴스 변수를 사용하는 경우 어떤 조치를 취해야 합니까?
* 생성자에서 변수를 초기화합니다.   
* 해당 인스턴스 변수의 getter에서 인스턴스 변수의 클론 객체를 반환합니다.   

[맨위로](#java)

## immutable 객체가 HashMap에 적합한 key로 간주되는 이유는 무엇입니까?
Immutable 객체의 해시코드는 변경되지 않습니다.   
즉, 각 key에 따른 해시코드를 캐싱할 수 있으므로 key 검색 속도가 빨라집니다.   

mutable 객체의 경우 mutable 필드에 의해 해시코드가 변경이 될 수 있습니다.   
만약 필드 값이 변경되면 해시 코드가 변경될 수 있으므로 HashMap에서 key를 찾을 수 없습니다.   

[맨위로](#java)

## immutable 클래스의 좋은 예
String, Integer, Long, Double, Character, Boolean 등이 있습니다.   
Date는 immutable 클래스가 아닙니다.   

[맨위로](#java)

## ConcurrentHashMap이란 무엇입니까?
동기화된 HashMap 구현을 대체하는 JDK 1.5에 추가된 Concurrent Collection 클래스입니다.   
HashTable 및 동기화된 HashMap 보다 성능 및 확장성이 뛰어나고 위험성은 거의 없습니다.   

[맨위로](#java)

## ConcurrentHashMap은 Thread-safe 합니까?
ConcurrentHashMap은 Thread-safe 합니다.   
즉, 두 개의 스레드가 내부 데이터 구조를 손상시키지 않고 map을 수정할 수 있습니다.   

Thread-safe하지 않는 HashMap은 여러 스레드에 노출되면 내부 데이터 구조가 손상될 수 있으며 잘못된 element를 가져오게 될 수 있습니다.

[맨위로](#java)

## ConcurrentHashMap은 어떤 원리로 thread-safe 합니까?
Map을 분할하고 전체 Map을 Locking 하는 대신 필요한 부분(segment)만 Locking하는 방식으로 Thread-safe를 달성합니다.  
즉, HashMap과 달리 map 전체를 locking하는게 아니기 때문에 성능이 향상됩니다.   
이 기술을 lock stripping이라고도 합니다.   

[맨위로](#java)

## 여러 스레드가 동시에 ConcurrentHashMap 값을 읽을 수 있습니까?
ConcurrentHashMap은 읽기 작업에 Locking을 하지 않으므로 동시 읽기를 허용합니다.   

[맨위로](#java)

## ConcurrentHashMap에서 동시에 한 스레드는 읽고 다른 스레드는 쓰기 작업을 할 수 있습니까?
각기 다른 부분(segment)에 대한 작업이라면 가능하지만, 같은 부분(segment)을 작업하는 것이라면 쓰기 작업이 완료될 때까지 읽기 작업이 차단됩니다.   

[맨위로](#java)

## ConcurrentHashMap 내부적으로 어떻게 작동합니까?
key/value를 저장하고 조회하는 것은 HashMap과 유사하게 작동합니다.   
차이점은 동시성과 Thread-safe을 구현하는 방법에 있습니다.   
디폴트로 16개의 부분(segment)로 나눠지고, 이를 동기화 레벨이라고도 합니다.

전체 Map이 Locking 되지 않고 관련된 부분(segment)만 Locking 되기 때문에 concurrent한 get(), put(), contains() 작업을 할 수 있습니다.   
이것은 읽기와 쓰기 작업이 동시에 될 수 있고 제한된 수의 쓰기 작업이 동시에 가능하다는 것을 의미합니다.   
그 결과 처리량과 확장성이 향상됩니다.   

기본적으로 버킷과 해시 엔트리가 LinkedList로 구성되어있는 미니 해시 테이블에 불과합니다.   

[맨위로](#java)

## ConcurrentHashMap에서 값을 어떻게 자동으로 업데이트합니까?
기존에 존재하는 값을 원자적으로 수정하려는 경우 replace()를 사용할 수 있습니다.  

기존 값과 새로운 값을 모두 받은 후 Map의 기존 값이 제공받은 기존 값과 일치하는 경우에만 Map을 수정합니다.   
즉, Map이 호출되는 동안 동시에 수정되지 않습니다.   

기존 값이 변경되어 제공받은 기존 값과 일치하지 않으면 false을 반환받으며 실패합니다.   
아래와 같이 성공할 때까지 while문에서 replace() 메서드를 호출할 수 있습니다.    
```
ConcurrentMap<String, Long> populationByCities = new ConcurrentHashMap<>();
do{
    Long currentValue = populationByCities.get("New York");
    Long newValue = currentValue == null ? 1 : currentValue + 1;
} while(!populationByCities.replace("New York", currentValue, newValue));
```

[맨위로](#java)

## ConcurrentHashMap을 순회하면서 map을 제거하려면 어떻게 해야 합니까?
```
Map<String, Integer> bookAndPrice = new ConcurrentHashMap<>();
bookAndPrice.put("Effective Java", 42);
bookAndPrice.put("Head First Java", 29);
bookAndPrice.put("Java Concurrency in Practice", 33);
bookAndPrice.put("Head First Design Patterns", 41);

System.out.println("before removing : " + bookAndPrice);
Iterator<String> iterator = bookAndPrice.keySet().iterator();

while(iterator.hasNext()){
    if(iterator.next().contains("Java")){
        iterator.remove();
    }
}

System.out.println("after removing : " + bookAndPrice);
```

출력
```
before removing : {Java Concurrency in Practice=33,
    Head First Design Patterns=41, Effective Java=42, Head First Java=29}
after removing : {Head First Design Patterns=41}
```

[맨위로](#java)

## ConcurrentHashMap의 Iterator는 fail-safe 입니까 fail-fast 입니까?
fail-safe하며 이것은 ConcurrentModificationException을 발생시키지 않음을 의미합니다.   
따라서 순회하는 동안 map을 locking할 필요가 없습니다.   

[맨위로](#java)

## 한 스레드가 반복되는 동안 ConcurrentHashMap에 새로운 매핑을 추가하면 어떻게 됩니까?
ConcurrentHashMap의 iterator는 fail-safe하기 때문에 ConcurrentModificationException으로 실패하지 않습니다.   
그러나 반복이 시작되면 아무것도 수정되지 않을 수 있습니다.   
구현에 따라 다르지만, JDK는 일반적으로 기존 ConcurrentHashMap을 통해 반복하는 대신 별도의 ConcurrentHashMap 복사본을 생성합니다.   

[맨위로](#java)

## Map 타입 변수에 ConcurrentHahsMap를 전달할 수 있습니까?
전달할 수 있습니다.   
ConcurrentHashMap은 Map 인터페이스를 구현하기 때문입니다.   
따라서 아래와 같은 코드가 가능합니다.   
```
Map<String, Integer> bookAndPrice = new ConcurrentHashMap<>();
```

하지만 이는 ConcurrentHashMap 클래스에 선언된 메서드는 사용하지 못할 수 있습니다.   
* ex) Java 8에 추가된 forEachKey() 또는 forEachValue()

[맨위로](#java)

## Atomic 데이터 타입이 무엇입니까?
Java에서 java.util.concurrent.atomic에는 AtomicBoolean, AtomicInteger, AtomicLong, AtomicReference, AtomicLongArray 등의 클래스가 있습니다.   
이 클래스들에는 get(), set(int value), lazySet(int value), compareAndSet(int expect, int update) 등의 값을 읽고 쓰는데 사용되는 메서드들이 있습니다.   

Atomic 클래스는 구현하는 방법은 다르지만 volatile + synchronzied와 동일한 효과가 있습니다.   
내부적으로 Atomic 클래스 구현을 살펴보면 어떠한 동기화도 선언되지 않았음을 알 수 있습니다.   
하지만 Atomic 변수는 단일 변수에 대해 무잠금 thread-safe 프로래밍이 정의되어 있기 때문에 동기화가 됩니다.   
Atomic 클래스 내부적으로 value 값은 volatile variable로 저장됩니다.   

[맨위로](#java)

## Atomic 데이터 타입의 종류
모든 Atomic 데이터 유형은 java.util.concurrent.atomic 내에 정의됩니다.   
모든 Atomic 데이터 타입에는 get(), set() 메서드가 포함되어 있습니다.   
* AtomicInteger
  * int형 값을 원자적으로 읽고 쓰는데 사용됩니다.
  * getAndDecrement(), getAndIncrement(), incrementAndGet(), decrementAndGet(), addAndGet(), getAndAdd() 등의 메서드가 있습니다.
* AtomicBoolean
  * boolean형 값을 원자적으로 읽고 쓰는데 사용됩니다.
  * getAndSet, weakCompareAndSetPlain, getPlain(),compareAndExchange 등의 메서드가 있습니다.   
* AtomicIntegerArray
  * 기본적인 int형 배열에 대한 operation들을 제공하며, 원자적으로 읽고 쓸 수 있습니다.   
  * addAndGet, compareAndSet, decrementAndGet, getAndDecrement, getAndIncrement 등의 atomic operation 도 있습니다.   
* AtomicIntegerFieldUpdater
  * 지정된 클래스의 지정된 volatile int형 필드를 atomic 업데이트를 할 수 있는 유틸리티 입니다.
  * getAndIncrement, getAndDecrement, getAndAdd, incrementAndGet, decrementAndGet 등과 같은 메서드가 있습니다.
* AtomicMarkableReference
  * 객체에 대한 참조와 boolean 플래그를 모두 캡슐화하는 일반적인 클래스입니다.   
  * 이 두 필드는 함께 또는 개별적으로 결합되며 원자적으로 업데이트 될 수 있습니다.
  * compareAndSet, attemptMark, weakCompareAndSet 등과 같은 메서드가 있습니다.   
* AtomicReference
  * 원자적으로 읽고 쓸 수 있는 객체 참조 변수를 제공합니다.
  * 동일한 AtomicReference를 변경하려고 시도하는 여러 스레드가 AtomicReference를 불일치 상태로 만들지 않음을 의미합니다.   
  * compareAndSet, weakCompareAndSetPlain, getAndAccumulate 등의 메서드가 있습니다.

long 타입의 경우 AtomicLong, AtomicLongArray, AtomicLongFieldUpdater 등의 유형이 있습니다.   
AtomicReference의 경우 추가적으로 AtomicReferenceArray, AtomicReferenceFieldUpdater, AtomicStampedReference 등의 유형이 있습니다.

[맨위로](#java)

## Atomic 데이터 타입은 언제 사용할 수 있습니까?
아래 예제에서 두 스레드의 각 스레드에서 for문을 통해 일반 변수, volatile 변수, atomic 변수의 값을 하나씩 증가시키고 있습니다.   
```
public class AtomicTest {

	public static int result = 0;
	public static volatile int volatileResult = 0;
	public static volatile AtomicInteger atomicResult = new AtomicInteger();
	public static Object lock = new Object();

	public static void main(String[] args) throws InterruptedException {

		Thread t1 = new Thread(new Runnable() {
			@Override
			public void run() {
				for (int i = 0; i < 100000; i++) {
					result++;
					volatileResult++;
					atomicResult.incrementAndGet();
				}

			}
		});

		Thread t2 = new Thread(new Runnable() {
			@Override
			public void run() {
				for (int i = 0; i < 100000; i++) {
					result++;
					volatileResult++;
					atomicResult.incrementAndGet();
				}

			}
		});
		t1.start();
		t2.start();
		t1.join();
		t2.join();

		System.out.println("result value -> " + result);
		System.out.println("volatileResult value -> " + volatileResult);
		System.out.println("atomicResult value -> " + atomicResult);
	}

}
```

실행 결과
```
result value -> 182462
volatileResult value -> 179853
atomicResult value -> 200000
```

atomic 변수는 올바른 결과가 출력되고, 나머지는 값이 부족하게 출력되었습니다.   
여기서 atomic 변수의 incrementAndGet() 메서드는 여러 스레드로 방해할 수 없으므로 올바른 결과가 출력됩니다.   

Atomic 데이터 클래스 내의 작업은 여러 스레드에 의해 간섭될 수 없습니다.   
따라서 여러 스레드에서 데이터를 반복적으로 수정하는 경우 Atomic 데이터 타입을 사용할 수 있습니다.   
이러한 경우 Atomic 데이터 타입을 사용하지 않으면 동기화 처리가 필요하며 이는 성능에 영향을 줄 수 있습니다.   

[맨위로](#java)

## Atomic 데이터 타입, volatile 변수, synchronization의 차이점은 무엇입니까?
Volatile Variable
* 값을 수정하면 변수의 실제 메모리에 즉시 영향을 미칩니다.
* 컴파일러는 변수에 대한 참조를 최적화 할 수 없습니다.
* 하나의 스레드가 변수를 수정하면 다른 모든 스레드가 새 값을 즉시 확인할 수 있습니다.

Atomic Variables
* 변수에 대해 수행된 작업이 원자적으로 수행되도록 보장합니다.
* 작업이 실행되는 스레드 내에서 완료되며 다른 스레드에 의해 중단되지 않습니다.
* 예를들어 증가 테스트를 수행하려면 변수를 증가시킨 다음 다른 값과 비교해야 합니다.   
* atomic 연산은 이 두 단계가 마치 하나의 중단 불가능한 작업인 것처럼 완료되도록 보장합니다.

Synchronization
* 변수에 대한 접근흘 동기화하는 것은 한 번에 하나의 스레드만 변수에 접근할 수 있습니다.   
* 그리고 다른 스레드들은 해당 스레드가 변수에 대한 접근을 해제할 때까지 기다리게 합니다. 

Synchronization은 atomic과 유사하지만, atomic은 좀 더 세부적인 수준의 프로그래밍에서 구현됩니다.
일부는 동기화하고 일부는 동기화하지 않는 작업이 가능합니다.   
* ex) 모든 write 작업은 동기화하고 읽기 작업은 동기화 하지 않는 것

atomic, volatile, synchronization 모두 독립적인 속성이지만 변수 접근을 하기 위한 적절한 스레드 협력을 적용하는데 함께 사용됩니다.   

[맨위로](#java)

## JVM, JRE, JDK의 차이점
JVM
* Java Virtual Machine
* java 바이트코드를 해석하고 실행하는 가상 머신입니다.
* java 프로그램을 컴파일하면 바이트코드로 이루어진 .class 파일이 생성됩니다.
* JVM은 바이트코드를 해석하고 .class 파일을 실행할 수 있습니다.
* 윈도우, 리눅스 등 OS 별로 JVM이 구현되어 있습니다.
  * 각 JVM은 모두 동일한 .class 파일을 실행할 수 있습니다.
  * 이러한 이유로 Java는 플랫폼에 독립적입니다.   
    * [Java가 플랫폼에 독립적인 이유 상세 설명]()

JRE
* Java Runtime Environment
* JVM을 구현합니다.
  * Java 프로그램을 실행하기 위해 필요한 라이브러리 및 기타 구성 요소를 지원합니다.
* Java 프로그램의 두 가지 배포 방법을 가능하게 하는 구성요소를 제공합니다.

JDK
* Java Development Kit
* JRE + (개발자가 Java 프로그램을 개발하는데 필요한 컴파일러, 디버거 등의 툴)

[맨위로](#java)

## Java가 플랫폼에 독립적인 이유
Java 프로그램을 컴파일하면 바이트코드로 이루어진 .class 파일이 생성됩니다.   
JVM은 바이트코드를 해석하고 Java 프로그램을 실행시켜줍니다.   
JVM은 특정 플랫폼(윈도우, 리눅스 등) 별로 구현됩니다.   
각 플랫폼 별 JVM은 동일한 .class 파일을 실행시킬 수 있습니다.   
따라서 Java는 한번 작성 및 컴파일하면 모든 플랫폼에서 실행시킬 수 있기 때문에 플랫폼에 독립적인 것입니다.   

[맨위로](#java)

## 바이트코드(bytecode)
개발자가 프로그램을 개발할 때 사용하는 언어인 Java와 프로그램을 실행하는 기계어의 중간 언어입니다.   
Java 프로그램을 컴파일하면 바이트코드로 이루어진 .class 파일이 생성됩니다.   
JVM은 클래스 로더를 통해 Java 클래스를 로드하고 실행시킵니다.   

[맨위로](#java)

## JVM이 Java 프로그램을 실행하는 방법
Java 프로그램(.java 파일)은 컴파일러(javac)를 통해 바이트코드(.class 파일)로 컴파일됩니다.   
클래스 로더는 컴파일된 Java 바이트코드를 런타임 데이터 영역으로 로드합니다.   
Java 실행 엔진은 Java 바이트 코드를 실행합니다.   

[맨위로](#java)

## 클래스 로더(Class Loader)
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

## 클래스 로더 종류
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

## 클래스 로드 단계
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

## Runtime Data Area(런타임 데이터 영역)
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

## JVM의 Java 프로그램 실행 단계
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

## 참고
* [Java - Variables Interview Questions and Answers](https://www.interviewgrid.com/interview_questions/java/java_variables)
* [Java Synchronization Interview Questions](http://www.javainterview.in/p/java-synchronization-interview-questions.html)
* [Immutable class interview questions](https://java2blog.com/immutable-class-interview-questions/)
* [Top 10 Java ConcurrentHashMap Interview](https://javarevisited.blogspot.com/2017/08/top-10-java-concurrenthashmap-interview.html)
* [Java Atomic Datatype: Interview Reference | by Anish Antony ...](https://medium.com/javarevisited/java-atomic-datatype-interview-reference-a463632d0d1a)
* [Java - JVM Internals Interview Questions and Answers](https://www.interviewgrid.com/interview_questions/java/java_jvm_internals)

[맨위로](#java)
