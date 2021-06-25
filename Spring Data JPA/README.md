# Spring Data JPA
* [JPA란 무엇입니까?](#jpa란-무엇입니까)
* [JPA를 사용할 때의 장점은 무엇입니까?]()
* [Spring data repository란 무엇입니까?]()
* [Spring Data Repository 인터페이스에서 조회에 대한 명명 규칙은 무엇입니까?]()
* [JPA를 통해 데이터 접근, 영속, 관리와 같은 작업을 수행할 수 있습니까?]()
* [Spring Data JPA에서 Repository를 생성하려면 어떻게 해야 합니까?]()
* [PagingAndSortingRepository란 무엇입니까?]()
* [@Query의 용도는 무엇입니까?]()
* [JPQL과 함께 @Query 애노테이션을 사용하는 예]()
* [엔티티 매핑 유형]()
* [PlatformTransactionManager란 무엇입니까?]()
* [Spring Data JPA 기능을 활성화하는 방법은 무엇입니까?]()
* [findById()와 getOne()의 차이점]()
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## JPA란 무엇입니까?
JPA는 Java Persistence API의 약자입니다.   
관계형 데이터베이스와 Java 객체 간의 데이터를 영속하는데 사용되는 Java 스펙입니다.   
객체 지향 도메인 모델과 관계형 데이터베이스 간의 연결 다리 역할을 합니다.   
데이터베이스와 Java 애플리케이션의 상호 작용은 매우 일반적이기 때문에, JPA는 이러한 상호 작용을 표준화하기 위해 만들어졌습니다.   

Java에서는 Hibernate와 같은 많은 인기 있는 JPA 구현체들이 있습니다.   

![1]()

[맨위로](#spring-data-jpa)

## JPA를 사용할 때의 장점은 무엇입니까?
* 데이터베이스와 상호 작용해야 하는 부담을 줄여줍니다.   
* 어노테이션을 사용하여 설정 파일 생성 비용이 절감됩니다.   
* 사용하기 편리합니다.

[맨위로](#spring-data-jpa)

## Spring data repository란 무엇입니까?
많은 코드를 줄이는데 도움이 됩니다.   
또한, 에러 발생 가능성도 크게 감소합니다.   
Repository 인터페이스를 사용합니다.   
도메인 클래스와 도메인 클래스의 ID 유형을 관리하는 Type Arguments가 필요합니다.   

[맨위로](#spring-data-jpa)

## Spring Data Repository 인터페이스에서 조회에 대한 명명 규칙은 무엇입니까?
"find"와 변수 이름을 차례로 사용해야 합니다.   
* ex) findByLastName()

[맨위로](#spring-data-jpa)

## JPA를 통해 데이터 접근, 영속, 관리와 같은 작업을 수행할 수 있습니까?
아니요, JPA는 Java 스펙에 불과하기 때문에 불가능합니다.   

[맨위로](#spring-data-jpa)

## Spring Data JPA에서 Repository를 생성하려면 어떻게 해야 합니까?
다음 인터페이스 중 하나를 확장해야합니다.   
* Repository
* PagingAndSortingRepository
* CrudRepository
* JpaRepository
* QueryByExampleRepository

[맨위로](#spring-data-jpa)

## PagingAndSortingRepository란 무엇입니까?
페이징 및 정렬을 사용하여 엔티티를 조회하는 기능을 제공합니다.   
또한 CrudRepository 인터페이스를 확장합니다.   

[맨위로](#spring-data-jpa)

## @Query의 용도는 무엇입니까?
JPQL 및 네이티브 SQL 쿼리를 실행하는데 사용되는 애노테이션입니다.   

[맨위로](#spring-data-jpa)

## JPQL과 함께 @Query 애노테이션을 사용하는 예
```
@Query("SELECT order FROM Orders o WHERE o.Disabled= 0")
Collection<User> findAllActiveOrders();
```

```
@Query("select e from Employee e where se.name = ?1") 
List<Employee> getEmployees(String name); 
```

[맨위로](#spring-data-jpa)

## 엔티티 매핑 유형
일대일, 일대다, 다대일, 다대다 매핑이 있습니다.   

[맨위로](#spring-data-jpa)

## PlatformTransactionManager란 무엇입니까?
TransactionManager를 확장한 인터페이스입니다.   
Spring 트랜잭션의 중심이 되는 인터페이스입니다.   

[맨위로](#spring-data-jpa)

## Spring Data JPA 기능을 활성화하는 방법은 무엇입니까?
먼저 Config 클래스를 생성한 다음 @EnableJpaRepositoties 애노테이션을 사용하면 기능이 활성화됩니다.   

[맨위로](#spring-data-jpa)

## findById()와 getOne()의 차이점
findById()는 CrudRepository에서 사용할 수 있고, getOne()은 JpaRepository에서 사용할 수 있습니다.   
findById()는 레코드가 없으면 null을 리턴하고, getOne()은 EntityNotFoundException을 발생시킵니다.   

[맨위로](#spring-data-jpa)

## 참고
* [Top 15 Spring Data JPA Interview Questions with ... - Java67](https://www.java67.com/2021/01/spring-data-jpa-interview-questions-answers-java.html)

[맨위로](#spring-data-jpa)
