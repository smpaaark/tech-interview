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
* [ConcurrentHashMap이란 무엇입니까?]()
* [ConcurrentHashMap은 Thread-safe 합니까?]()
* [ConcurrentHashMap은 어떤 원리로 thread-safe 합니까?]()
* [여러 스레드가 동시에 ConcurrentHashMap 값을 읽을 수 있습니까?]()
* [ConcurrentHashMap 내부적으로 어떻게 작동합니까?]()
* [ConcurrentHashMap에서 값을 어떻게 자동으로 업데이트합니까?]()
* [ConcurrentHashMap을 순회하면서 map을 제거하려면 어떻게 해야 합니까?]()
* [ConcurrentHashMap의 Iterator는 fail-safe 입니까 fail-fast 입니까?]()
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

## 참고
* [Java - Variables Interview Questions and Answers](https://www.interviewgrid.com/interview_questions/java/java_variables)
* [Java Synchronization Interview Questions](http://www.javainterview.in/p/java-synchronization-interview-questions.html)
* [Immutable class interview questions](https://java2blog.com/immutable-class-interview-questions/)
* [Top 10 Java ConcurrentHashMap Interview](https://javarevisited.blogspot.com/2017/08/top-10-java-concurrenthashmap-interview.html)

[맨위로](#java)
