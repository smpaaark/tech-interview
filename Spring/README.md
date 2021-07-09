# Spring
* [Spring](#spring-1)
* [Spring Framework 모듈](#spring-framework-모듈)
* [주요 스프링 애노테이션](#주요-스프링-애노테이션)
* [Spring Bean(빈)](#spring-bean빈)
* [DispatcherServlet과 ContextLoaderListener](#dispatcherservlet과-contextloaderlistener)
* [Constructor(생성자) 주입과 Setter 주입의 차이점]()
* [Autowiring](#autowiring)
* [Spring 프레임워크에서의 Exception 처리 방법](#spring-프레임워크에서의-exception-처리-방법)
* [Spring에서 지원하는 트랜잭션 관리(Transaction Management) 유형](#spring에서-지원하는-트랜잭션-관리transaction-management-유형)
* [Spring 프레임워크 버전별 주요 특징]()
* [Spring 프레임워크의 장점]()
* [Spring 프레임워크의 주요 기능]()
* [스프링 설정 파일(Spring configuration file)]()
* [스프링 애플리케이션의 구성 요소]()
* [스프링 IOC 컨테이너]()
* [의존성 주입 방법]()
* [IOC 컨테이너의 종류]()
* [BeanFactory와 ApplicationContext의 차이점]()
* [IoC의 장점]()
* [스프링 빈]()
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## Spring
Java용 애플래케이션 프레임워크 및 IOC 컨테이너(Inversion of Control Container) 입니다.
Spring은 모든 Java 애플리케이션에서 사용될 수 있습니다.
* Spring은 Enterprise 애플리케이션 개발의 복잡성을 줄이기 위해 만들어진 강력한 오픈 소스 애플리케이션 프레임워크 입니다.
* 경량이며 느슨하게 결합되어 있습니다.
* 사용할 구성요소를 선택할 수 있는 계층형 아키텍처이며 J2EE 애플리케이션 개발을 위한 통합 프레임워크를 제공합니다.   

[맨위로](#spring)

## Spring Framework 모듈
Core Container, Data Access/Integration, Web, AOP (Aspect Oriented Programming), Instrumentation , Test로 구성된 약 20개의 모듈이 있습니다.

* Spring Core Container
  * 스프링 프레임워크의 핵심입니다.
    * Spring Core
    * Spring Bean
    * SpEL (Spring Expression Language)
    * Spring Context
      * 의존성 주입(Dependency Injection)
* Data Access/Integration
  * 데이터베이스와 상호 작용할 수 있도록 지원합니다.
    * JDBC (Java DataBase Connectivity)
      * JDBC 및 DataSource 지원
    * ORM (Object Relational Mapping)
      * Hibernate와 같은 ORM 도구 지원
    * OXM (Object XML Mappers)
    * JMS (Java Messaging Service)
    * Transaction
* Web
  * 웹 애플리케이션 생성을 지원합니다.
    * Web
    * Web – MVC
    * Web – Socket
    * Web – Portlet
* Aspect Oriented Programming (AOP)
  * Advices, Pointcuts 등을 사용하여 코드를 분리할 수 있습니다.
* Instrumentation
  * 클래스로더 구현을 지원합니다.
* Test
  * JUnit 및 TestNG를 사용한 테스트를 지원합니다.
* Messaging
  * STOMP(Simple/Stream Text Oriented Messaging Protocol)에 대한 지원을 제공합니다.
  * WebSocket 클라이언트의 STOMP 메시지를 라우팅 및 처리하는데 사용되는 애노테이션 프로그래밍 모델을 지원합니다.
* Aspects
  * AspectJ와의 통합을 지원합니다.

![5](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/5.PNG)

[맨위로](#spring)

## 주요 스프링 애노테이션
* @Required
* @Autowired
  * 스프링 빈 의존성 주입
* @Qualifier
  * @Autowired과 함께 사용하면 빈 유형의 인스턴스가 여러개 있을 때 혼동을 방지할 수 있습니다.
* @Resource
* @PostConstruct
* @PreDestroy
* @Controller
  * 컨트롤러 클래스
* @RequestMapping
  * 컨트롤러 메서드의 URI 매핑 설정
* @ResponseBody
  * Response를 객체로 보내는데 사용되며 보통 XML 또는 JSON 데이터를 응답으로 보냅니다.
* @PathVariable
  * URI의 동적인 값들을 메서드 매개 변수로 매핑하는데 사용됩니다.
* @Service
  * 서비스 클래스
* @Scope
  * 스프링 빈의 scoper을 설정합니다.
* @Configuration, @ComponentScan, @Bean
  * 설정 관련

AspectJ 애노테이션으로는 @Aspect, @Before, @After, @Around, @Pointcut 등이 있습니다.

[맨위로](#spring)

## Spring Bean(빈)
스프링 애플리케이션에서 가장 중요한 역할을 하는 객체입니다.   
스프링 빈은 스프링 IoC 컨테이너에 의해 관리됩니다.   
즉, 스프링 빈은 IoC 컨테이너에 의해 인스턴스화, 조립, 관리되는 객체입니다.   

스프링 빈에는 5가지 scoper이 정의되어 있습니다.      
![6](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/6.PNG)
* Singleton
  * 각 컨테이너에 단 한개의 인스턴스만 생성됩니다.
  * 스프링 빈의 default scope입니다.   
  * 스프링 빈의 인스턴스 변수는 사용할 때 주의가 필요합니다.
    * Thread-safe 하지 않기 때문에 데이터 불일치 문제가 발생할 수 있습니다.
* Prototype
  * 빈이 요청될 때마다 새 인스턴스가 생성됩니다.
* Request
  * Prototype과 scope이 동일하지만 웹 애플리케이션용으로 사용해야 합니다.
  * 각 HTTP 요청마다 새 인스턴스가 생성됩니다.
* Session
  * 컨테이너에 의해 각 HTTP 세션마다 새 인스턴스가 생성됩니다.
* Global-session
  * Portlet(포틀릿) 애플리케이션을 위한 Global Session 빈을 생성하는데 사용됩니다.

[맨위로](#spring)

## DispatcherServlet과 ContextLoaderListener
DispatcherServlet
* 스프링 빈 Config 파일을 로드하고 구성된 모든 빈을 초기화하는 Spring MVC 애플리케이션의 전방 컨트롤러 입니다.
* @Component, @Controller, @Repository, @Service 애노테이션이 붙은 빈들을 설정하기 위해 패키지를 스캔합니다.

![7](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/7.PNG)

ContextLoaderListener
* 스프링 루트에서 WebApplicationContext를 시작하고 종료하는 Listener입니다.
* 주요 기능은 ApplicationContext 라이프 사이클을 ServletContext의 라이프 사이클과 연결하고, ApplicationContext 생성을 자동화합니다.

![8](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/8.PNG)

[맨위로](#spring)

## Constructor(생성자) 주입과 Setter 주입의 차이점
Constructor(생성자) 주입
* 부분 주입이 없습니다.
* 수정이 발생한 경우 새 인스턴스를 생성합니다.
* 속성이 많은 경우 적합합니다.

Setter 주입
* 부분 주입입니다.
* 속성 값을 변경하더라도 새 인스턴스가 생성되지 않습니다.
* 속성이 적은 경우 적합합니다.

[맨위로](#spring)

## Autowiring
Autowiring은 프로그래머가 자동으로 빈을 주입할 수 있게 해줍니다.   
빈을 주입하는 로직을 사용할 필요가 없어집니다.  

예시
```
<bean id=“emp”class=“com.javatpoint.Employee”autowire=“byName” />  
```

autowiring 모드
* no
  * default 모드이며, autowiring을 사용할 수 없습니다.
* byName
  * 속성 이름을 기준으로 빈을 주입합니다.
  * setter 메서드를 사용합니다.
* byType
  * 속성 타입을 기준으로 빈을 주입합니다.
  * setter 메서드를 사용합니다.
* constructor
  * 생성자를 이용하여 빈을 주입합니다.

[맨위로](#spring)

## Spring 프레임워크에서의 Exception 처리 방법
Controller Based
* 컨트롤러 클래스에 ExceptionHandler 메서드를 정의할 수 있습니다.
* @ExceptionHandler 애노테이션을 붙이면 됩니다.

Global Exception Handler
* Spring은 모든 클래스에서 Global Exception Handler를 정의할 수 있는 @ControllerAdvice 애노테이션을 제공합니다.

HandlerExceptionResolver 구현
* 일반적인 Exception의 경우 대부분 정적 페이지를 제공합니다.
* Spring 프레임워크는 global exception handler를 생성하기 위해 구현할 수 있는 HandlerExceptionResolver를 제공합니다.

[맨위로](#spring)

## Spring에서 지원하는 트랜잭션 관리(Transaction Management) 유형
Spring에서는 2가지 트랜잭션 관리 유형을 지원합니다.
* Programmatic transaction management(프로그래밍 방식)
  * 유연성은 좋지만 유지 보수하기가 어렵습니다.
* Declarative transaction management(선언적 방식)
  * 애노테이션 또는 XML 기반의 설정들로 트랜잭션을 관리합니다.

[맨위로](#spring)

## Spring 프레임워크 버전별 주요 특징
Spring 2.5
* 2007년에 출시되었습니다.
* 애노테이션을 지원한 첫번째 버전입니다.

Spring 3.0
* 2009년에 출시되었습니다.
* Java5의 향상된 기능을 본격적으로 활용했으며 JEE6에 대한 지원도 제공했습니다.

Spring 4.0
* 2013년에 출시되었습니다.
* Java8을 완전히 지원하는 첫 번째 버전입니다.

[맨위로](#spring)

## Spring 프레임워크의 장점
* 계층형 아키텍처이기 때문에 필요한 것만 선택하여 사용할 수 있습니다.
* 지속적인 통합과 테스트를 가능하게 하는 POJO 프로그래밍을 할 수 있습니다.
* Dependency Injection(의존성 주입)과 Inversion of Control(제어의 역전)으로 인해 JDBC가 간소화 됩니다.
* 오픈소스이며 벤더에 종속되지 않습니다.

[맨위로](#spring)

## Spring 프레임워크의 주요 기능
* Lightweight(경량)
  * 크기와 투명도에 대해 가볍습니다.
* Inversion of control (IOC)
  * 객체는 의존하는 객체를 생성하거나 찾는 대신 의존성을 제공합니다.
  * 시스템 서비스로부터 비즈니스 로직을 분리하므로써 응집력 있는 개발을 지원합니다.
* Container(컨테이너)
  * 애플리케이션 객체의 생명 주기 및 설정을 생성하고 관리합니다.
* MVC Framework(MVC 프레임워크)
* Transaction Management(트랜잭션 관리)
  * 트랜잭션 관리를 위한 추상 계층을 제공합니다.
  * 스프링의 트랜잭션 지원은 컨테이너가 없는 환경에서도 사용 가능합니다.
* JDBC Exception Handling
  * JDBC 추상 계층은 Exception 계층을 제공하여 에러 처리 전략을 단순화합니다.

[맨위로](#spring)

## 스프링 설정 파일(Spring configuration file)
XML 파일입니다.   
주로 클래스 정보가 포함되어 있습니다.   
이 클래스들이 어떻게 설정 되고 어떻게 연결되는지에 대해서 설명합니다.  
올바르게 계획되고 작성되지 않으면 프로젝트 관리가 어려워 집니다.   

[맨위로](#spring)

## 스프링 애플리케이션의 구성 요소
* 인터페이스
  * 기능을 정의합니다.
* 빈
  * 속성, setter/getter, 기능 등이 포함됩니다.
* AOP
  * 공통 관심 사항(cross-cutting) 처리 기능을 제공합니다.
* 빈 설정 파일
  * 클래스 정보와 설정 방법을 포함합니다.   
* User program
  * 기능을 사용합니다.

[맨위로](#spring)

## 스프링 IOC 컨테이너
![9](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/9.PNG)   
스프링 프레임워크의 core에는 스프링 컨테이너가 있습니다.   
컨테이너는 객체를 생성, 연결, 구성하고 생명 주기를 관리합니다.   
스프링 컨테이너는 의존성 주입을 사용하여 애플리케이션을 구성하는 요소들을 관리합니다.   
컨테이너는 제공된 설정 메타데이터를 읽어서 인스턴스화, 설정, 조립할 객체에 대한 정보를 수신합니다.
이 메타데이터는 XML, 애노테이션, Java 코드로 제공될 수 있습니다.

[맨위로](#spring)

## 의존성 주입(Dependency Injection)
의존성 주입은 객체를 생성할 필요가 없고 객체를 생성되는 방법을 설명하는 것입니다.   
구성 요소와 서비스를 코드로 직접 연결하는 것이 아니라 설정 파일의 구성 요소에 필요한 서비스를 명시합니다.   
그러면 IoC 컨테이너가 이들을 주입시켜서 연결합니다.

[맨위로](#spring)

## 의존성 주입 방법
* Constructor Injection
* Setter Injection

## IOC 컨테이너의 종류
* BeanFactory
  * 빈 팩토리는 빈들을 갖고 있는 팩토리 클래스입니다.   
  * 클라이언트가 요청할 때마다 빈을 인스턴스화 합니다.
* ApplicationContext
  * ApplicationContext 인터페이스는 BeanFactory 인터페이스를 상속받습니다.
  * BeanFactory에서 몇가지 추가 기능을 더 제공합니다.

[맨위로](#spring)

## BeanFactory와 ApplicationContext의 차이점
BeanFactory
* org.springframework.beans.factory.BeanFactory에 정의된 인터페이스입니다.
* Lazy 초기화를 사용합니다.
* syntax를 사용하여 리소스 객체를 명시적으로 제공합니다.
* 국제화를 지원하지 않습니다.
* 애노테이션 기반 의존성을 지원하지 않습니다.

ApplicationContext
* org.springframework.context.ApplicationContext에 정의된 인터페이스입니다.
* Eager/Aggressive 초기화를 사용합니다.
* 리소스 객체를 자체적으로 생성하고 관리합니다.
* 국제화를 지원합니다.
* 애노테이션 기반 의존성을 지원합니다.

[맨위로](#spring)

## IoC의 장점
* 애플리케이션의 코드 양이 줄어듭니다.
* 유닛 테스트 케이스에 싱글톤이나 JNDI 조회 메커니즘이 필요하지 않기 때문에 테스트가 쉬워집니다.
* 느슨한 결합을 촉진합니다.
* 서비스를 빠르게 인스턴스화하고 Lazy 로딩할 수 있도록 지원합니다.

[맨위로](#spring)

## 스프링 빈
* 애플리케이션의 핵심이되는 객체입니다. 
* IoC 컨테이너에 의해 인스턴스화, 설정, 연결, 관리됩니다.
* 사용자가 컨테이너에 제공하는 설정 메타데이터에 의해 빈이 생성됩니다.

[맨위로](#spring)

## 설정 메타데이터(configuration metadata)
설정 메타데이터는 다음과 같은 방법으로 스프링 컨테이너에 제공됩니다.   
* XML 기반 설정
  * 스프링 빈으로부터 필요한 의존성 및 서비스는 XMl 형식의 설정 파일에 설정됩니다.
  * 설정 파일에는 빈 설정들과 애플리케이션 설정 옵션들이 포함됩니다.
  * \<bean> 태그로 시작합니다.
```
<bean id="studentbean" class="org.edureka.firstSpring.StudentBean">
  <property name="name" value="Edureka"></property>
</bean>
```
* 애노테이션 기반 설정
  * 애노테이션을 사용하여 클래스, 메서드, 필드

## 참고
* [100+ Java Interview Questions And Answers For 2021 | Edureka](https://www.edureka.co/blog/interview-questions/java-interview-questions/)
* [Top 50 Spring Interview Questions For 2021 | Edureka](https://www.edureka.co/blog/interview-questions/spring-interview-questions/)

[맨위로](#spring)
