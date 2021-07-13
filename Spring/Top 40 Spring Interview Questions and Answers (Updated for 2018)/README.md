# Top 40 Spring Interview Questions and Answers (Updated for 2018)
* [강한 결합(Tight Coupling)](#강한-결합tight-coupling)
* [느슨한 결합(Loose Coupling)](#느슨한-결합loose-coupling)
* [스프링 빈(Bean)](#스프링-빈bean)
* [빈 생성 프로세스](#빈-생성-프로세스)
* [@Primary](#primary)
* [의존성 주입(Dependency Injection)](#의존성-주입dependency-injection)
* [IoC(Inversion of Control, 제어의 역전)](#iocinversion-of-control-제어의-역전)
* [IoC 컨테이너](#ioc-컨테이너)
* [ApplicationContext](#applicationcontext)
* [ApplicationContext 생성 프로세스](#applicationcontext-생성-프로세스)
* [컴포넌트 스캔(Component Scan)](#컴포넌트-스캔component-scan)
* [스프링 부트에서 컴포넌트 스캔하는 방법](#스프링-부트에서-컴포넌트-스캔하는-방법)
* [@Component, @Repository, @Service, @Controller](#component-repository-service-controller)
* [빈(bean)의 scope(범위)](#빈bean의-scope범위)
* [의존성 주입 유형](#의존성-주입-유형)
* [XML 설정과 애노테이션 설정의 차이점](#xml-설정과-애노테이션-설정의-차이점)
* [Autowiring 방법](#autowiring-방법)
* [Dirty Read](#dirty-read)
* [스프링 프레임워크 4.0과 5.0의 새로운 기능](#스프링-프레임워크-40과-50의-새로운-기능)
* [FrontController](#frontcontroller)
* [ViewResolver](#viewresolver)
* [참고](#참고)

[Spring 목차로](https://github.com/smpark1020/tech-interview/tree/master/Spring)

## 강한 결합(Tight Coupling)
클래스(클래스A)가 다른 클래스의 객체(클래스B)에 의존된 경우 클래스 A가 클래스 B와 강하게 결합된다고 말합니다.   
스프링을 사용하면 강한 결합을 제거하고 느슨한 결합을 수행할 수 있는 클래스를 만들 수 있습니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 느슨한 결합(Loose Coupling)
느슨한 결합은 클래스(클래스A)에 대한 객체(클래스B)의 의존성을 제거합니다.   
느슨한 결합은 인터페이스와 setter/getter 메서드를 만들거나 인터페이스 객체를 가져오는 생성자를 사용하여 구현할 수 있습니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 스프링 빈(Bean)
클래스에 @Component를 사용하는 경우 이러한 클래스를 스프링의 빈이라고 합니다.   
빈은 ApplicationContext를 통해 관리됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 빈 생성 프로세스
1. @Component이 붙은 클래스(c1)로 시작합니다.
2. @Component이 붙은 클래스(c1)가 의존되어 있는지 확인합니다.
3. 의존되어 있는 경우 스프링은 해당 클래스(c2)를 위한 빈(bean)도 만듭니다.
4. 두 클래스(c1과 c2)에 @Autowired를 사용하거나 생성자 또는 setter 메서드를 통해서 autowiring이 발생합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## @Primary
이 애노테이션은 가장 우선으로 스프링에 의해 사용되어야 하는 클래스에 사용됩니다.   
예를 들어, 클래스X에 @Component가 붙어있고 클래스X가 클래스1과 클래스2(둘 다 @Component가 붙어있음)에 의존되어 있으면 컴파일러가 오류를 발생시킵니다.  
클래스1과 클래스2 사이에 더 우선으로 사용될 클래스를 표시하기 위해 @Primary를 사용합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 의존성 주입(Dependency Injection)
의존성 주입은 스프링이 빈을 검색하여 주입하는 것입니다.
  * 적절한 빈이 발견되면 의존 클래스에 빈을 자동으로 주입시킵니다.   
의존성 주입은 스프링 프레임워크가 빈을 찾고 의존성을 식별하여 빈 인스턴스를 생성하고 그들을 주입하는 프로세스 입니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## IoC(Inversion of Control, 제어의 역전)
강한 결합(Tight Coupling)에서 의존 클래스는 의존성 생성에 대한 책임을 갖습니다.   
반면, 느슨한 결합(Loose Coupling)에서는 의존 클래스(또는 참조)에 @Autowired를 사용하고 스프링이 인스턴스를 생성을 제어하고 의존성을 주입합니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## IoC 컨테이너
IoC 컨테이너는 다음과 같은 작업을 수행합니다.
1. 빈을 찾습니다.
2. 의존성을 파악하고 의존성을 주입합니다.
3. 빈의 라이프사이클(생성~소멸)을 관리합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## ApplicationContext
IoC 컨테이너의 고급 버전입니다.   
BeanFactory의 모든 기능과 AOP, 국제화 기능 등의 기능을 제공합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## ApplicationContext 생성 프로세스
ApplicationContext는 XML을 사용하는 방법과 @Configuration을 사용하는 방법으로 정의할 수 있습니다.   
위의 방법들로 설정이 완료되면, ApplicationContext는 new ClassPathXmlApplicationContext()을 통해 생성됩니다.   
ClassPathXmlApplicationContext는 두 가지 방법 중 하나를 사용하여 XML 파일을 찾습니다.   
또 다른 방법은 AnnotationConfigApplicationContext를 사용하는 것입니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 컴포넌트 스캔(Component Scan)
컴포넌트 스캔은 스프링에게 스프링 관리 컴포넌트를 검색하도록 요청하는 방법 중 하나이며, 이 검색에 대한 입력은 패키지입니다.   
컴포넌트 스캔을 정의하는 방법에는 두 가지가 있습니다.   
1. Java 설정
* 여기서는 @Component를 사용하며, 이 애노테이션에 대해 스프링이 검색을 수행합니다.
2. XML 설정
* \<context:component-scan base-package=”com.demo.compscanex”/>를 사용합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 스프링 부트에서 컴포넌트 스캔하는 방법
스프링 부트에서 스캔을 수행하는데 사용되는 애노테이션은 @SpringBootApplication 입니다.   
이 애노테이션이 붙은 클래스의 패키지 내에 있는 컴포넌트들을 자동으로 스캔합니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## @Component, @Repository, @Service, @Controller
일반적으로 웹 애플리케이션은 컨트롤러(클라이언트 통신의 진입 지점), 비즈니스(애플리케이션의 실제 코드 또는 로직이 작성되는 곳), DAO(데이터베이스 연결 및 통신이 발생하는 곳)와 같은 계층으로 개발됩니다.   
이러한 웹 애플리케이션 아키텍처에서는 @Component를 모든 계층에서 사용할 수 있습니다.   
반면, @Controller는 컨트롤러/웹 계층에서 사용됩니다.  
@Service는 비즈니스 계층에서 사용되고 @Repository는 DAO 계층에서 사용됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 빈(bean)의 scope(범위)
1. 싱글톤(Singleton)
* 스프링 컨텍스트 전체에서 인스턴스 하나만 생성됩니다.   
2. 프로토타입(Prototype)
* 요청될 때마다 새로운 빈이 생성됩니다.   
3. Request
* 모든 HTTP 요청마다 빈이 생성됩니다.
4. 세션(Session)
* HTTP 세션마다 빈이 생성됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 의존성 주입 유형
1. setter 주입
2. 생성자 주입

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## XML 설정과 애노테이션 설정의 차이점
애노테이션 설정을 사용할 경우 더 적은 양의 코드로 XML 방식과 동일한 결과를 낼 수 있습니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## Autowiring 방법
1. byType
2. byName
3. Constructor (byType과 동일하지만 생성자를 통해 주입합니다.)

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## Dirty Read
트랜잭션(t1)이 다른 트랜잭션(t2)에 의해 변경된 내용을 읽으려고 하고 트랜잭션 t2가 아직 커밋되지 않은 경우입니다.
이러한 경우 트랜잭션 t1을 Direy Read 트랜잭션이라고 합니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 스프링 프레임워크 4.0과 5.0의 새로운 기능
스프링 4.0은 Java8 기능을 처음으로 지원했습니다.   
스프링 5.0은 Reactive Programming 및 코틀린을 지원합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## FrontController
FrontController에서 서블릿은 첫번째 요청을 받지 못합니다.   
첫 번째 요청은 FrontController로 이동되며 해당 요청은 올바른 서블릿으로 전달됩니다.   
즉, DispatcherServlet은 클라이언트의 모든 요청을 가로챈 다음 적절한 컨트롤러로 보내는 FrontController 입니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## ViewResolver
ViewResolver는 웹 애플리케이션이 view를 동적으로 선택할 수 있게 해줍니다.   
ViewResolver는 /WEB-INF/views/ + a.jsp에서 a 라는 이름을 가져옵니다.   
내용은 모두 HTML 페이지에 표시됩니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 참고
* [Top 40 Spring Interview Questions and Answers (Updated for 2018)](https://www.greycampus.com/blog/programming/top-spring-interview-questions-and-answers)

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)
