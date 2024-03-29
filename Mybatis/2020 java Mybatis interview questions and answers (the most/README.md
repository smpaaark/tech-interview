# 2020 java Mybatis interview questions and answers (the most ...
* [Mybatis](#mybatis)
* [Mybatis의 장점](#mybatis의-장점)
* [MyBatis 프레임워크의 단점](#mybatis-프레임워크의-단점)
* [참고](#참고)

[Mybatis 목차로](https://github.com/smpark1020/tech-interview/tree/master/Mybatis#mybatis)

## Mybatis
1. mybatis는 jdbc를 내부적으로 캡슐화하는 우수한 Java 기반 영속성 계층 프레임워크이므로 개발자는 드라이버 로드, 커넥션 생성, Statements 생성 등의 복잡한 프로세스를 처리하지 않고 SQL문 자체에만 신경쓰면 됩니다.   
2. mybatis는 xml이나 애노테이션으로 실행될 다양한 statement를 설정하고, sql의 동적 파라미터를 자바 객체와 statement에 매핑하여 최종적으로 실행되는 SQL문을 생성합니다.      
마지막으로 mybatis 프레임워크는 sql을 실행하고 결과를 Java 객체에 매핑하고 반환합니다.   
3. MyBatis는 사용자 정의 SQL, 저장 프로시저 및 고급 매핑을 지원합니다.    
MyBatis는 거의 모든 JDBC 코드를 피하고 수동으로 매개변수를 설정하고 Result Set을 가져옵니다.    
MyBatis는 기본 정보, 매핑 인터페이스 및 Java POJO를 데이터베이스의 레코드에 구성하고 매핑하기 위해 간단한 XML 또는 애노테이션을 사용할 수 있습니다.   

[맨위로](#2020-java-mybatis-interview-questions-and-answers-the-most-)

## Mybatis의 장점
1. 배우기 쉽고 사용하기 쉽습니다(Hibernate에 비해)
  * SQL 프로그래밍 기반
2. JDBC와 비교하여 코드 양을 50% 이상 줄이고 JDBC의 방대한 중복 코드를 제거하며 수동 스위치 연결이 필요하지 않습니다.
3. 다양한 데이터베이스와 매우 호환됩니다(MyBatis는 데이터베이스에 연결하기 위해 JDBC를 사용하므로 Java용 jar가 있는 한 MyBatis와 호환 가능), 개발자는 데이터베이스의 차이점을 고려할 필요가 없습니다.   
4. 다수의 타사 플러그인(페이징 플러그인/역설계)이 제공됩니다.
5. Spring과의 통합이 잘됩니다.
6. MyBatis는 매우 유연하며 애플리케이션이나 데이터베이스의 기존 디자인에 영향을 주지 않습니다.   
SQL은 XML로 작성되어 프로그램 코드와 완전히 분리되어 있으며, sql과 프로그램 코드 간의 결합을 제거하여 통합 관리 및 최적화가 용이합니다.    
재사용 가능합니다.
7. 동적 SQL문 작성을 지원하기 위해 XML 태그를 제공합니다.
8. 객체와 데이터베이스 간의 ORM 필드 관계 매핑을 지원하기 위해 매핑 태그를 제공합니다.
9. 객체 관계 그룹 유지 관리를 지원하기 위해 객체 관계 매핑 태그를 제공합니다.

[맨위로](#2020-java-mybatis-interview-questions-and-answers-the-most-)

## MyBatis 프레임워크의 단점
1. SQL문 작성 비용이 상대적으로 큽니다.    
필드와 관련 테이블이 많을 때 특히 그렇습니다.   
개발자가 SQL문을 작성하기 위한 특정 요구 사항이 있습니다.   
2. SQL문은 데이터베이스에 의존하므로 데이터베이스의 이식성이 떨어지고 데이터베이스를 임의로 변경할 수 없습니다.

[맨위로](#2020-java-mybatis-interview-questions-and-answers-the-most-)

## 참고
* [2020 java Mybatis interview questions and answers (the most ...](https://www.programmersought.com/article/87845365114/)

[맨위로](#2020-java-mybatis-interview-questions-and-answers-the-most-)
