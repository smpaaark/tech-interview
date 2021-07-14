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
* [MVC 아키텍처 흐름]()
* [ModelAttribute]()
* [SessionAttribute]()
* [@InitBinder]()
* [@ControllerAdvice]()
* [스프링 부트를 사용하는 이유]()
* [스프링 vs 스프링 MVC vs 스프링 부트]()
* [@SpringBootApplication]()
* [스프링 부트의 내장 서버(Embedded Server)]()
* [application.properties]()
* [Spring JDBC]()
* [JDBC와 Spring JDBC의 차이점]()
* [JPA]()
* [Hibernate]()
* [생성자 주입과 setter 주입]()
* [pom.xml]()
* [@RequestParam]()
* [스프링 시큐리티(Spring Security)]()
* [CSRF(Cross-site request forgery)]()
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


## MVC 아키텍처 흐름
1. 브라우저가 DispatcherServlet으로 요청을 전송합니다.
2. DispatcherServlet은 HanderMapping을 통해 적절한 컨트롤러를 찾습니다.   
3. 컨트롤러는 요청을 실행하고 모델에 데이터를 입력한 후 뷰 이름을 DispatcherServlet에 반환합니다.
4. DispatcherServlet은 뷰 이름과 ViewResolver를 사용하여 뷰에 매핑합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## ModelAttribute
@ModelAttribute는 일반적으로 컨트롤러 내부의 메서드에 붙습니다.   
컨트롤러에서 사용할 수 있는 모든 다른 메서드에서 이 메서드를 사용할 수 있게 해줍니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## SessionAttribute
@SessionAttributes("매개변수")는 클래스(컨트롤러)에 붙습니다.   
모델에 있는 attribute(매개변수)를 세션에서 사용할 수 있습니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## @InitBinder
날짜 형식을 선언하는 메서드로 사용되며, 클래스 전체에서 정의된 날짜 형식이 사용됩니다.   
날짜 필드가 바인딩 될 때마다 @InitBinder가 발생합니다. 
* CustomDateEditor을 사용하고 CustomDateEditor에는 @InitBinder에 설정한 날짜 형식이 사용됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## @ControllerAdvice
로직을 여러 클래스(컨트롤러)에서 공통적으로 구현해야 할 때 사용됩니다.   
예를 들어, 클래스에서 Exception(또는 하위 클래스 Exception)이 발생하면 @ExceptionHandler이 붙은 메서드에 의해 처리됩니다.   
컨트롤러에서 Exception이 발생할 때마다 Exception은 @ExceptionHandler가 붙은 메서드에 의해 처리됩니다.      
@ExceptionHandler가 하나의 클래스에 대한 것이라면 @ControllerAdvice는 모든 @Controller 즉, 전역에서 발생할 수 있는 예외를 잡아 처리해주는 애노테이션입니다.   
@ExceptionHandler를 정의한 클래스를 만든 후 클래스에 @ControllerAdvice를 붙여주면 됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 스프링 부트를 사용하는 이유
스프링 기반 애플리케이션은 많은 설정 코드들이 있습니다.   
스프링 MVC에서는 컴포넌트 스캔, DispatcherServlet, ViewResolver 등 많은 설정들이 필요합니다.
반면, 스프링 부트에서는 이러한 설정 코드들이 필요하지 않습니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 스프링 vs 스프링 MVC vs 스프링 부트
스프링
* 스프링의 가장 중요한 기능은 의존성 주입과 IoC(제어의 역전) 입니다.

스프링 MVC
* 스프링 MVC는 웹 애플리케이션 개발에 있어 계층에 따른 분리 방식을 제공합니다.
* DispatcherServlet, ModelAndView, ViewResolver과 같은 것들을 통해 웹 애플리케이션을 쉽게 개발할 수 있습니다.

스프링 부트
* 스프링 부트는 자동 설정(Auto Configuration) 기능을 사용하여 많은 설정들을 매우 쉽게 자동으로 설정해주며, 이를 통해 DispatcherServlet이 스프링에 의해 내부적으로 수행됩니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## @SpringBootApplication
전체 애플리케이션을 시작하는 데 사용됩니다.   
내부적으로 @SpringBootApplication은 다음을 수행합니다.   
* @SpringBootConfiguration
  * 스프링 애플리케이션의 @Configuration과 동일합니다.
* @EnableAutoConfiguration
  * classpath에서 사용할 수 있는 클래스들을 자동 설정 해줍니다.      
* @ComponentScan
  * 패키지 내에서 사용할 수 있는 모든 클래스가 스캔됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 스프링 부트의 내장 서버(Embedded Server)
웹 애플리케이션을 배포하려면 톰캣(Tomcat)과 같은 서버가 필요합니다.   
스프링 부트는 jar에서 톰캣과 같은 내장 서버를 사용할 수 있습니다.     
내장 서버는 애플리케이션 배포를 매우 쉽고 독립적으로 할 수 있도록 해줍니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## application.properties
application.properties 파일은 데이터베이스 상세 정보, 로그 생성, 보안(사용자이름/패스워드), 직렬화 등을 설정하는 데 사용됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## Spring JDBC
Spring JDBC는 update, execute, query와 같은 메서드를 사용하여 데이터베이스와 통신합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## JDBC와 Spring JDBC의 차이점
JDBC에서는 CheckedException을 작성해야 합니다.   
반면에 스프링 JDBC에서는 RuntimeException으로 발생합니다.   
즉, 스프링 JDBC에서는 예외 처리를 수동으로 하지 않습니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## JPA
Java Persistence API (JPA)는 Java 객체와 데이터베이스 테이블 간의 매핑을 정의합니다.   
Java 객체를 데이터베이스 테이블의 행에 매핑하는 절차는 JPA에 정의되어 있습니다.   
JPA는 클래스 와 테이블 간의 관계를 정의하는 유용한 애노테이션을 많이 제공합니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## Hibernate
매핑이 완료되면 Hibernate(JPA 구현체)가 쿼리를 생성하고 데이터베이스와 통신할 수 있도록 해줍니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 생성자 주입과 setter 주입
의존성 주입이 필수인 경우 생성자 주입 방식을 사용합니다.   
의존성 주입이 선택인 경우 setter 주입 방식을 사용합니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## pom.xml
Project Object Model (POM)은 maven 프로젝트의 모든 설정이 정의되는 xml 형식의 파일입니다.   
pom.xml에서 가장 일반적으로 사용되는 태그는 \<groupid>, \<artifactId>, \<version>, \<packaging> 입니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## @RequestParam
서버 측에서 데이터를 읽고 메서드에 들어오는 매개 변수에 자동으로 바인딩 할 수 있습니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 스프링 시큐리티(Spring Security)
스프링 시큐리티는 J2EE 애플리케이션에 보안 서비스를 제공합니다.   
스프링 시큐리티는 ServletFilter를 사용하여 구현됩니다.   
ServletFilter는 웹 요청을 사전 또는 사후 처리하는 데 사용됩니다.

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## CSRF(Cross-site request forgery)
CSRF(Cross-site request forgery)는 부정 웹 사이트가 사용자가 로그인한 웹 애플리케이션에서 이벤트를 수행하도록 속이려는 보안 공격입니다.   
예를 들어, 사용자가 온라인 은행 계좌에 로그인한 경우 사용자를 속여서 알 수 없는 사람에게 돈을 송금하도록 합니다.   

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)

## 참고
* [Top 40 Spring Interview Questions and Answers (Updated for 2018)](https://www.greycampus.com/blog/programming/top-spring-interview-questions-and-answers)

[맨위로](#top-40-spring-interview-questions-and-answers-updated-for-2018)
