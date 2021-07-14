# Top 50+ Spring Boot Interview Questions and Answers you should know in 2021
* [스프링 부트(Spring Boot)](#스프링-부트spring-boot)
* [톰캣에서 스프링 부트 애플리케이션 배포하는 방법]()
* [스프링과 스프링 부트의 차이점]()
* [스프링 부트 actuator]()
* [스프링 부트에서 포트 변경 방법]()
* [스프링 부트에서 war 파일 생성 방법]()
* [스프링 부트에서의 JPA]()
* [참고](#참고)

[Spring Boot 목차로](https://github.com/smpark1020/tech-interview/tree/master/Spring%20Boot)

## 스프링 부트(Spring Boot)
스프링 부트는 스프링 프레임워크 위에 구축된 마이크로서비스 프레임워크라고 불립니다.   
개발자는 설정보다 관례에 더 집중할 수 있습니다.   

1. 스프링 부트의 주 목적은 바로 사용할 수 있는 애플리케이션을 제공하는 것입니다.   
  * 스프링 부트 프로젝트를 생성하는 즉시 실행 가능하며 서버에서 실행/배포할 수 있습니다.   
2. 자동 설정, 의존성 주입, 내장 서버, 보안, 상태 체크 등의 기능이 제공되어 개발자의 생산성을 향상시킵니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 톰캣에서 스프링 부트 애플리케이션 배포하는 방법
스프링 부트 애플리케이션을 생성하고 실행할 때마다 스프링 부트는 내장된 톰캣 서버를 자동으로 감지하여 톰캣에 애플리케이션을 배포합니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링과 스프링 부트의 차이점
스프링
1. 의존성 주입 프레임워크 입니다.
2. 기본적으로 Java 클래스(bean)의 생명 주기를 관리하는 데 사용됩니다.
3. 많은 설정 코드들로 구성되어 있습니다.
  * XML 기반 설정을 사용합니다.
4. 스프링 애플리케이션을 가동하는데 시간이 오래 걸리며, 이유는 많은 설정 코드들 때문입니다.   

스프링 부트
1. 많은 설정 코드들을 제거하는데 도움이 되는 미리 설정된 프레임워크 및 기술 모음입니다.  
2. 애노테이션을 사용합니다.
3. 상용화된 코드를 생성하는데 사용됩니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트 actuator
Actuator는 애플리케이션을 모니터링하고 관리하는 데 도움이 되는 상용 기능으로 구성된 스프링 부트의 가장 좋은 기능 중 하나입니다.   

Actuator의 도움을 받아 실행 중인 애플리케이션 내에서 어떤 일이 일어나고 있는지 모니터링 할 수 있습니다.   
Actuator 의존성은 통계를 파악하고 웹에서 필요한 모든 정보를 검색합니다.   
Actuator를 사용하여 빈, 애플리케이션의 상태, CPU 사용량 등을 식별할 수 있습니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트에서 포트 변경 방법
스프링 부트 애플리케이션을 시작하는 기본 포트 번호는 8080입니다.   

포트 번호를 변경하려면 application.properties 파일에 server.port=8084(포트 번호) 속성을 추가하고 애플리케이션을 시작해야 합니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트에서 war 파일 생성 방법
스프링 부트에서 war 파일을 생성하려면 pom.xml(maven 프로젝트인 경우)에서 packaging file을 war로 정의해야 합니다.   

그런 다음 maven clean을 하고 애플리케이션을 새로 빌드하면 됩니다.   
빌드가 성공적으로 완료되면 target 폴더로 이동하면 애플리케이션에 대해 생성된 .war 파일을 볼 수 있습니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트에서의 JPA


## 참고
* [Top 50+ Spring Boot Interview Questions and Answers you should know in 2021](https://www.mygreatlearning.com/blog/spring-boot-interview-questions/)

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)
