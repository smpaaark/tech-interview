# Java
* [JDK, JRE, JVM 설명](#jdk-jre-jvm-설명)
* [public static void main (String args []) 설명](#public-static-void-main-string-args--설명)

## JDK, JRE, JVM 설명
### JDK
자바 개발도구(Java Development Kit)    
Java 프로그램을 컴파일, 문서화, 패키징하는데 필요한 도구        
JRE + 개발 도구가 포함되어 있다.    

### JRE
자바 실행 환경(Java Runtime Environment)   
Java 바이트 코드를 실행할 수 있는 런타임 환경이다.   
JVM의 구현을 담당한다.   

### JVM
자바 가상 머신(Java Virtual Machine)   
Java 바이트 코드를 실행할 수 있는 런타임 환경을 제공하는 규격이다.

## public static void main (String args []) 설명
Java 프로그램의 진입점이다.   
항상 ```public static void main (String [] args```)```로 작성된다.     
* public
  * 접근 제어자이다.
  * public은 이 메서드가 모든 클래스에서 접근할 수 있음을 의미한다.
* static
  * 클래스 기반을 나타내는 Java의 키워드이다.
  * Class의 인스턴스를 만들지 않고도 접근할 수 있다.
  * main이 static으로 만들어지지 않는 경우에는 JVM이 main을 호출할 수 없으므로 컴파일 오류가 발생한다.   
* void
  * return 타입이다.
  * 값을 반환하지 않는 메서드라는 의미이다.
* main
  * JVM에서 애플리케이션을 실행할 때 검색하는 메서드의 이름이다.
  * 프로그램이 실행되게 하는 메서드이다.
* String args[]
  * main 메서드에 전달되는 매개 변수이다.

## 참고
* [100+ Java Interview Questions You Must Prepare In 2021](https://www.edureka.co/blog/interview-questions/java-interview-questions/)
