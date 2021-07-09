# Spring
* [Spring](#spring-1)
* [Spring Framework 모듈](#spring-framework-모듈)
* [주요 스프링 애노테이션](#주요-스프링-애노테이션)
* [Spring Bean(빈)](#spring-bean빈)
* [DispatcherServlet과 ContextLoaderListener](#dispatcherservlet과-contextloaderlistener)
* [생성자 주입과 Setter 주입의 차이점](#constructor생성자-주입과-setter-주입의-차이점)
* [Autowiring](#autowiring)
* [Spring 프레임워크에서의 Exception 처리 방법](#spring-프레임워크에서의-exception-처리-방법)
* [Spring에서 지원하는 트랜잭션 관리(Transaction Management) 유형](#spring에서-지원하는-트랜잭션-관리transaction-management-유형)
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## Spring
Java용 애플래케이션 프레임워크 및 IOC 컨테이너(Inversion of Control Container) 입니다.
Spring은 모든 Java 애플리케이션에서 사용될 수 있으며, Java EE 플랫폼 위에 웹 애플리케이션을 구축하기 위한 확장 기능도 있습니다.
Spring은 Java EE 애플리케이션 개발을 위해 사용되는 경량 통합 프레임워크 입니다.

[맨위로](#spring)

## Spring Framework 모듈
* Spring Context
  * 의존성 주입(Dependency Injection)
* Spring AOP
  * 관점 지향 프로그래밍(Aspect Oriented Programming)
* Spring DAO
  * DAO 패턴을 사용하는 데이터베이스 작업
* Spring JDBC
  * JDBC 및 DataSource 지원
* Spring ORM
  * Hibernate와 같은 ORM 도구 지원
* Spring Web Module
  * 웹 애플리케이션 생성
* Spring MVC
  * 웹 애플리케이션, 웹 서비스 등을 생성하기 위한 Model-View-Controller 구현

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

## 참고
* [100+ Java Interview Questions And Answers For 2021 | Edureka](https://www.edureka.co/blog/interview-questions/java-interview-questions/)

[맨위로](#spring)
