# Spring
<<<<<<< HEAD
* [Spring]]()
* [Spring Framework 모듈]()
* [주요 스프링 설정 애노테이션]()
* [Spring Bean(빈)]()
=======
* [Spring](#spring-1)
* [Spring Framework 모듈](#spring-framework-모듈)
>>>>>>> 38d1d69c8c218adde43f07edb47c12e83d8b211b
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

![5]()

[맨위로](#spring)

## 주요 스프링 설정 애노테이션
* @Required
* @Autowired
* @Qualifier
* @Resource
* @PostConstruct
* @PreDestroy

[맨위로](#spring)

## Spring Bean(빈)
스프링 애플리케이션에서 가장 중요한 역할을 하는 객체입니다.   
스프링 빈은 스프링 IoC 컨테이너에 의해 관리됩니다.   
즉, 스프링 빈은 IoC 컨테이너에 의해 인스턴스화, 조립, 관리되는 객체입니다.   

스프링 빈에는 5가지 scoper이 정의되어 있습니다.      
![6]()
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



## 참고
* [100+ Java Interview Questions And Answers For 2021 | Edureka](https://www.edureka.co/blog/interview-questions/java-interview-questions/)

[맨위로](#spring)
