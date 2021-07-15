# Top 50+ Spring Boot Interview Questions and Answers you should know in 2021
* [스프링 부트(Spring Boot)](#스프링-부트spring-boot)
* [톰캣에서 스프링 부트 애플리케이션 배포하는 방법](#톰캣에서-스프링-부트-애플리케이션-배포하는-방법)
* [스프링과 스프링 부트의 차이점](#스프링과-스프링-부트의-차이점)
* [스프링 부트 actuator](#스프링-부트-actuator)
* [포트 변경 방법](#포트-변경-방법)
* [war 파일 생성 방법](#war-파일-생성-방법)
* [JPA](#jpa)
* [데이터베이스에 데이터를 저장하는 방법](#데이터베이스에-데이터를-저장하는-방법)
* [자동 설정(auto configuration)](#자동-설정auto-configuration)
* [Whitelabel 에러 페이지 해결 방법](#whitelabel-에러-페이지-해결-방법)
* [데이터베이스에서 데이터를 insert하는 방법](#데이터베이스에서-데이터를-insert하는-방법)
* [ResponseEntity](#responseentity)
* [logger 사용 방법](#logger-사용-방법)
* [스프링 부트 프로젝트 생성 방법](#스프링-부트-프로젝트-생성-방법)
* [도입 년도](#도입-년도)
* [jar 파일 생성 방법](#jar-파일-생성-방법)
* [예외 처리 방법](#예외-처리-방법)
* [의존성 주입](#의존성-주입)
* [Hibernate 설정 방법](#hibernate-설정-방법)
* [스프링 부트를 마이크로 서비스에 사용하는 이유](#스프링-부트를-마이크로-서비스에-사용하는-이유)
* [스프링 부트의 장점](#스프링-부트의-장점)
* [스프링 Actuator](#스프링-actuator)
* [타임리프(Thymeleaf)](#타임리프thymeleaf)
* [Spring Boot DevTools](#spring-boot-devtools)
* [@RequestMapping, @RestController](#requestmapping-restcontroller)
* [스프링 부트 Actuator에서 사용자 지정 endpoint 생성](#스프링-부트-actuator에서-사용자-지정-endpoint-생성)
* [자동 설정(auto-configuration) 사용하지 않는 방법](#자동-설정auto-configuration-사용하지-않는-방법)
* [트랜잭션 관리에서 ReadOnly](#트랜잭션-관리에서-readonly)
* [yaml 파일의 장점과 로딩 방법](#yaml-파일의-장점과-로딩-방법)
* [스프링 데이터 REST](#스프링-데이터-rest)
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

## 포트 변경 방법
스프링 부트 애플리케이션을 시작하는 기본 포트 번호는 8080입니다.   

포트 번호를 변경하려면 application.properties 파일에 server.port=8084(포트 번호) 속성을 추가하고 애플리케이션을 시작해야 합니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## war 파일 생성 방법
스프링 부트에서 war 파일을 생성하려면 pom.xml(maven 프로젝트인 경우)에서 packaging file을 war로 정의해야 합니다.   

그런 다음 maven clean을 하고 애플리케이션을 새로 빌드하면 됩니다.   
빌드가 성공적으로 완료되면 target 폴더로 이동하면 애플리케이션에 대해 생성된 .war 파일을 볼 수 있습니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## JPA
JPA는 Java Persistence API 입니다.   
관계형 데이터베이스에 연결할 때 ORM(Object-Relational Mapping)을 수행하는 스펙입니다.

Java 애플리케이션에서 관계형 데이터베이스에 연결해야 하는 경우 JDBC를 사용하고 SQL 쿼리를 실행한 다음 결과를 가져와 객체 인스턴스로 변환할 수 있어야 합니다.   

ORM은 쿼리를 직접 작성할 필요 없이 SQL 테이블과 엔티티 클래스를 매핑할 수 있게 해주는 프레임워크입니다.   

JPA는 ORM을 사용하는 수단이며, 엔티티 클래스를 설정하여 프레임워크가 나머지를 수행할 수 있도록 프레임워크에 전달해주는 API 입니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 데이터베이스에 데이터를 저장하는 방법
1. 먼저 스프링 부트 애플리케이션에 mysql을 설정합니다.
2. 그런 다음 JPA를 사용하여 엔티티를 DB 테이블과 매핑합니다.
3. JPA의 save() 메서드를 사용하면 데이터를 데이터베이스에 직접 insert 할 수 있습니다.
```
@RestController
@RequestMapping("/greatleasrning")
public class Controller {

  @Autowired
  private final GreatLearningRepository greatLearningRepository;

  public Controller(GreatLearningRepository greatLearningRepository) {

  }

  @RequestMapping(method = RequestMethod.POST)
  ResponseEntity<?> insert(@RequestBody Course course) {
    greatLearningRepository.save(course);
    return ResponseEntity.accepted().build();
  }

}
```

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 자동 설정(auto configuration)
스프링 부트가 모든 빈들을 자동으로 설정하는 프로세스입니다.   
애플리케이션 classpath에 존재하는 의존성에 따라 JPA, 스프링 시큐리티 등과 같은 스프링 모듈의 기본 빈/객체들을 선언합니다.   

예를들어 스프링 JDBC를 사용하면 스프링 부트 자동 설정 기능이 자동으로 DataSource 및 JDBCTemplate 빈을 등록합니다.   
xml 코드나 Java 설정 코드 작성 없이 프레임워크 고유의 빈을 자동으로 선언하는 이 과정 전체를 자동 설정이라고 하며 이 작업은 @EnableAutoconfiguration 또는 @SpringBootApplication을 사용하여 스프링 부트를 통해 수행됩니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## Whitelabel 에러 페이지 해결 방법
스프링 부트 애플리케이션에서 자주 발생하는 에러이며 404(page not found) 에러 입니다.   

이 문제는 3가지 방법으로 해결할 수 있습니다.   
1. 커스텀 에러 컨트롤러(Custom Error Controller)
  * 스프링 프레임워크에서 제공하는 ErrorController 인터페이스를 구현하고 getErrorPath()를 재정의하여 이러한 유형의 에러가 발생할 때마다 사용자 지정 경로를 반환할 수 있습니다.
2. 커스텀 에러 페이지 표시
  * error.html 페이지를 생성하여 src/main/resources/templates 경로에 배치하기만 하면 됩니다.
  * 스프링 부트의 BasicErrorController는 디폴트로 이 파일을 자동으로 선택합니다.
3. Whitelabel 에러 페이지 disable 처리
  * 가장 쉬운 방법이며 application.properties 파일에서 server.error.whitelabel.enabled 속성을 false로 설정하여 Whitelabel 에러 페이지를 disable 처리합니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 데이터베이스에서 데이터를 insert하는 방법
1. 먼저 MySQL에 데이터베이스를 생성합니다.
2. DB 내에 테이블을 생성합니다.
```
CREATE TABLE student(
  studentid INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
  studentname VARCHAR(255)
);
```
3. 스프링 부트 애플리케이션을 생성하고 JDBC, MySQL 및 웹 의존성을 추가합니다.
4. application.properties에 데이터베이스를 설정합니다.
```
spring.datasource.url=jdbc:mysql://localhost:3306/studentDetails
spring.datasource.username=system123 
spring.datasource.password=system123 
spring.jpa.hibernate.ddl-auto=create-drop 
```
5. 컨트롤러 클래스에서 요청을 처리합니다.
```
package com.student;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.web.bind.annotation.RestController;
@RestController
public class JdbcController {
  @Autowired
  JdbcTemplate jdbc;

  @RequestMapping("/save")
  public String index(){
    jdbc.execute("insert into student (name)values(GreatLearnings)");
    return "Data Entry Successful";
  }

}
```
6. 애플리케이션을 실행하고 데이터베이스를 확인합니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## ResponseEntity
ResponseEntity는 기본적으로 헤더, 상태 코드, 응답 본문을 포함하는 HTTP 응답입니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## logger 사용 방법
스프링 부트에서는 다양한 로깅 옵션을 사용할 수 있습니다.   
* log4j2 사용
```
import org.apache.logging.log4j.Logger;
import org.apache.logging.log4j.LogManager;
// [...]
Logger logger = LogManager.getLogger(LoggingController.class);
```

* Lombok 사용
  * pom.xml에 org.projectlombok 의존성을 추가합니다.   
  ```
  <dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.4</version>
    <scope>provided</scope>
  </dependency>
  ```   
  * 컨트롤러를 생성하고 여기에 @Slf4j를 추가합니다.
  * 여기서는 logger 인스턴스를 생성하지 않습니다.   
  ```
  @RestController
  @Slf4j
  public class LoggingController {

    @RequestMapping("/logging")
    public String index() {
      log.trace("A TRACE Message");
      log.debug("A DEBUG Message");
      log.info("An INFO Message");
      log.warn("A WARN Message");
      log.error("An ERROR Message");
      
      return "Here are your logs!”;
    }

  }
  ```

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트 프로젝트 생성 방법
스프링 부트 애플리케이션을 생성하는 방법 중 하나는 스프링 이니셜라이저를 사용하는 것입니다.   
스프링 공식 웹 사이트에 가서 버전을 선택하고, groupID, artifactId, 필요한 의존성들을 추가합니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 도입 년도
스프링 부트는 2002년에 도입되었습니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## jar 파일 생성 방법
스프링 부트에서 jar 파일을 생성하려면 pom.xml(메이븐인 경우)에서 packaging file을 jar로 설정해야 합니다.   

그다음 maven pacakage를 통해 애플리케이션을 빌드합니다.

빌드가 성공하면 target 폴더에 .jar 파일이 생성된 것을 볼 수 있습니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 예외 처리 방법
@ControllerAdvice를 사용하여 전체적으로 예외를 처리할 수 있습니다.    

@ExceptionHandler를 사용하여 특정 예외를 처리하고 사용자 지정 응답을 보낼 수 있습니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 의존성 주입
의존성 주입은 스프링 컨테이너가 한 객체를 다른 객체에 주입하는 것입니다.   
이렇게 하면 컴포넌트들이 느슨하게 결합됩니다.   

예를들어 학생 클래스가 학과 클래스를 속성으로 갖는다면 학생 클래스가 학과 클래스에 의존한다고 말합니다.    
학생 클래스에서 학과 클래스를 사용할 수 있도록 학과 클래스의 인스턴스를 만들어줘야 하는데 이를 의존성 주입이라고 합니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## Hibernate 설정 방법
Hibernate를 구성하는데 필요한 의존성은 다음과 같습니다.
1. spring-boot-starter-data-jpa
2. h2(다른 데이터베이스도 가능합니다.)

이제 application.properties에 모든 데이터베이스 연결 속성을 작성하여 JPA 코드를 데이터베이스에 연결합니다.   
```
spring.datasource.url=jdbc:h2:file:~/test
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=test
spring.datasource.password=test
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
```

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트를 마이크로 서비스에 사용하는 이유
마이크로서비스에서는 단일 기능에 대한 코드를 작성할 수 있습니다.   
기술에 따라 서로 다른 마이크로 서비스 마다 다른 기술 스택을 사용할 수 있습니다.   

스프링 부트는 설정보다 규약을 우선시하므로 이러한 유형의 마이크로 서비스를 매우 빠르게 개발할 수 있으며 이는 개발자의 생산설을 높입니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트의 장점
1. 설정보다 규약을 우선시하므로 xml 설정을 피할 수 있습니다.
2. 많은 개발 시간을 단축하고 생상성 향상에 도움이 됩니다.
3. 많은 설정 코드들을 줄일 수 있습니다.
4. Tomcat, Jetty 등과 같은 내장된 HTTP 서버와 함께 제공됩니다.
5. CLI(Command Line Interface) 도구를 제공하여 CMD에서 애플리케이션을 개발하고 테스트할 수 있도록 지원합니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 Actuator
애플리케이션을 모니터링하고 관리하는데 도움이 되는 상용 기능으로 구성된 스프링 부트의 기능 중 하나입니다.   

Actuator의 도움을 받아 실행 중인 애플리케이션 내에서 무슨 일이 일어나고 있는지 모니터링할 수 있습니다.   
Actuator 의존성은 통계를 파악하고 애플리케이션의 새로운 endpoint로 사용할 수 있도록 하고 웹에서 필요한 모든 정보를 검색합니다.   
Actuator를 사용하여 빈, 애플리케이션 상태, CPU 사용량 등을 식별할 수 있습니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 타임리프(Thymeleaf)
타임리프는 HTML, XML, JavaScript, CSS, text를 처리하고 생성하는 데 도움이 되는 서버측 Java 템프릿 엔진입니다.   
pom.xml 의존성이 발견되면 스프링 부트는 동적 Web 컨텐츠를 제공하도록 타임리프를 자동으로 설정합니다.   

의존성
* spring-boot-starter-thymeleaf

src/main/resources/templates/ 경로에 HTML 파일인 타임리프 템플릿을 배치하면 스프링 부트가 이 파일들을 선택하고 필요에 따라 렌더링 합니다.   

타임리프는 html을 분석하고 동적 값을 컨트롤러 클래스에서 전달된 실제 값으로 바꿉니다.   
이렇게 스프링 애플리케이션을 실행하면 메시지가 웹 브라우저에 렌더링 됩니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## Spring Boot DevTools
스프링 부트가 제공하는 기능 중 하나로, 코드가 변경될 때마다 스프링 부트 애플리케이션을 다시 시작합니다.   

이 때, 애플리케이션을 반복해서 실행할 필요가 없습니다.   
Spring Boot devtools는 코드가 변경될 때마다 이를 수행합니다.  

의존성 추가
* spring-boot-devtools

이 모듈의 중요한 목표는 스프링 애플리케이션으로 작업하는 동안 개발 시간을 단축하는 것입니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## @RequestMapping, @RestController
@RequestMapping은 컨트롤러 클래스의 클레스 레벨 또는 메서드 레벨에 사용할 수 있습니다.   

컨트롤러 클래스 전체에 매핑해야 하는 request path는 클래스 레벨에 @RequestMapping을 사용해야 합니다.   
```
@RestController
@RequestMapping("/greatLearning")
  public class GreatLearningController {

  @RequestMapping("/")
  String greatLearning(){
    return "Hello from greatLearning ";
  }

  @RequestMapping("/welcome")
  String welcome(){
    return "Welcome from GreatLearning";
  }

}
```

@RestController는 클래스 레벨에서 사용됩니다.   

@RestController는 @Controller와 @ResponseBody로 구성되어 있어 모든 메서드에 @ResponseBody를 붙일 필요가 없습니다.   
```
@RestController
@RequestMapping(“bank-details”)
public class DemoRestController{
  @GetMapping(“/{id}”,produces =”application/json”)
  public Bank getBankDetails(@PathVariable int id){
    return findBankDetailsById();
  }
}
```
클래스에 @RestController가 추가되어있으므로 @ResponseBody가 필요하지 않습니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 부트 Actuator에서 사용자 지정 endpoint 생성
@Endpoint를 사용하여 사용자 정의 endpoint를 생성할 수 있습니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 자동 설정(auto-configuration) 사용하지 않는 방법
1. @EnableAutoConfiguration 속성을 제거하여 비활성화 할 수 있습니다.   
2. property 파일을 사용합니다.   
예를 들어   
```
spring.autoconfigure.exclude= 
org.springframework.boot.autoconfigure.mongo.MongoAutoConfiguration,
org.springframework.boot.autoconfigure.data.MongoDataConfiguration,
```
위의 예시는 MongoDB의 자동 설정을 비활성화 한 것입니다.   

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 트랜잭션 관리에서 ReadOnly
데이터베이스에서 읽기 작업만 할 때는 readonly로 설정합니다.

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## yaml 파일의 장점과 로딩 방법
yaml 파일은 스프링 부트에 있습니다.   

yaml은 더 명확하고 인간 친화적입니다.   
map, list, 다른 scalar 유형도 지원합니다.   

yaml은 반복 및 들여쓰기를 방지하는 데 도움이 되는 계층적 특성을 가지고 있습니다.

개발, 테스트, 운영과 같이 배포 프로파일이 다르고 각 환경에 대해 설정이 다를 수 있는데, 각 환경에 대해 새 파일을 생성하는 대신 단일 yaml 파일에 설정할 수 있습니다.   
properties 파일의 경우에는 이렇게 할 수 없습니다.

예시
```
spring:
  profiles:
    active:
      -test
---
spring:
  profiles:
    active:
      -prod
---
spring:
  profiles:
    active:
      -development
```

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)

## 스프링 데이터 REST
스프링 데이터 Rest를 사용하면 스프링 데이터 저장소 주변의 모든 RESTful 리소스에 액세스할 수 있습니다.
```
@RepositoryRestResource(collectionResourceRel = "greatlearning", path = "sample")
public interface GreatLearningRepo extends CustomerRepository< greatlearning, Long> {

}
```


## 참고
* [Top 50+ Spring Boot Interview Questions and Answers you should know in 2021](https://www.mygreatlearning.com/blog/spring-boot-interview-questions/)

[맨위로](#top-50-spring-boot-interview-questions-and-answers-you-should-know-in-2021)
