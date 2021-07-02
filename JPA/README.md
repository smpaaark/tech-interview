# JPA
* [JPA(Java Persistence API)]()
* [ORM(Object-Relational Mapping)]()
* [JPA의 장점](#jpa의-장점)
* [임베디드(@Embeddable) 클래스]()
* [JPQL]()
* [엔티티 객체의 영속화 과정](#엔티티-객체의-영속화-과정)
* [엔티티 매핑의 방향]()
* [엔티티 매핑의 종류](#엔티티-매핑의-종류)
* [orphanRemoval]()
* [객체의 영속성 생명 주기](#객체의-영속성-생명-주기)
* [식별자 생성 유형](#식별자-생성-유형)
* [엔티티]()
* [EntityManager의 역할]()
* [엔티티 클래스의 제약조건](#엔티티-클래스의-제약조건)
* [JPA에서 Java 컬렉션의 목적은 무엇입니까?](#jpa에서-java-컬렉션의-목적은-무엇입니까)
* [JPA 컬렉션 매핑에 저장할 수 있는 객체 타입은 무엇입니까?](#jpa-컬렉션-매핑에-저장할-수-있는-객체-타입은-무엇입니까)
* [JPA에서 사용할 수 있는 컬렉션 타입은 무엇입니까?](#jpa에서-사용할-수-있는-컬렉션-타입은-무엇입니까)
* [JPA Cascade의 목적은 무엇입니까?](#jpa-cascade의-목적은-무엇입니까)
* [JPA가 지원하는 Cascade 유형은 무엇입니까?](#jpa가-지원하는-cascade-유형은-무엇입니까)
* [JPQL이란 무엇입니까?](#jpql이란-무엇입니까)
* [JPQL의 특징](#jpql의-특징)
* [Criteria API란 무엇입니까?](#criteria-api란-무엇입니까)
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## JPA(Java Persistence API)
JPA는 Java 객체와 관계형 데이터베이스 간에 데이터를 유지하는데 사용하는 Java의 스펙입니다.   
JPA는 객체 지향 도메인 모델과 관계형 데이터베이스 간의 연결 다리 역할을 합니다.   
JPA는 스펙에 불과하기 때문에 자체적으로 어떠한 작업도 수행하지 않습니다.   
* 구현이 필요합니다.
* Hibernate 같은 ORM 도구가 JPA 스펙을 구현합니다.
* 즉 JPA는 데이터 접근, 유지, 관리와 같은 실제 작업을 직접 수행하지 않습니다.

[맨위로](#JPA)

## ORM(Object-Relational Mapping)
ORM은 객체 상태를 데이터베이스 컬럼에 매핑하여 객체와 관계형 데이터베이스 간의 관계를 개발하고 유지하는데 사용되는 메커니즘입니다.   
프로그래밍 코드의 속성을 테이블의 컬럼으로 변환합니다.   
select, insert, update, delete 등과 같은 다양한 데이터베이스 작업을 쉽게 처리할 수 있습니다.

![1](https://raw.githubusercontent.com/smpark1020/tech-interview/master/JPA/1.PNG)

[맨위로](#JPA)

## JPA의 장점
* JPA를 사용하면 데이터베이스와 상호 작용해야 하는 부담을 크게 줄일 수 있습니다.
* 객체 관계 매핑과 데이터베이스 접근 처리를 숨김으로서 개발자는 프로그래밍하기 더 쉬워진다.   
* 어노테이션을 사용함으로서 정의 파일 생성 비용이 절감됩니다.
* 사용된 애플리케이션을 다른 JPA 공급체와 병합할 수 있습니다.
* JPA 표준 스펙에 기능을 추가할 수 있습니다.   

[맨위로](#JPA)

## 임베디드(@Embeddable) 클래스
임베디드 클래스는 엔티티의 상태를 나타내지만 고유한 ID가 없습니다.   
이러한 클래스의 객체는 해당 객체를 소유한 엔티티 클래스의 ID를 공유합니다.   
엔티티는 단일 값 또는 다중 값 임베디드 클래스 속성을 가질 수 있습니다.

[맨위로](#JPA)

## JPQL
JPQL은 JPA 스펙에 정의된 Java 영속성 쿼리 언어입니다.   
쿼리를 구성하는데 사용됩니다.   

[맨위로](#JPA)

## 엔티티 객체의 영속화 과정
* EntityManagerFactory 객체를 생성합니다.
  *  java.persistence 패키지에 있는 EntityManagerFactory 인터페이스는 엔티티 관리자를 제공하는데 사용됩니다.   
```
EntityManagerFactory emf = Persistence.createEntityManagerFactory("Student_details");  
```

* EntityManagerFactory에서 EntityManager를 가져옵니다.   
```
EntityManager em = emf.createEntityManager();  
```

* EntityManager를 초기화합니다.   
```
em.getTransaction().begin();  
```

* 데이터를 관계형 데이터베이스에 영속화합니다.
```
em.persist(s1);
```

* 트랜잭션을 커밋합니다.
```
em.getTransaction().commit();  
```

* EntityManagerFactory와 EntityManager를 종료합니다.
```
emf.close();  
em.close();  
```

[맨위로](#JPA)

### 엔티티를 저장하는 과정
EntityManager는 레코드를 추가하는 persist() 메서드를 제공합니다.   
* 엔티티 클래스를 생성합니다.
* persistence.xml 파일에서 엔티티 클래스 및 기타 데이터베이스 구성을 매핑합니다.
* 저장 작업을 하기 위한 클래스를 생성하고 아래와 같이 작업합니다.
```
package com.javatpoint.jpa.persist;  
  
import com.javatpoint.jpa.student.*;  
import javax.persistence.*;  
public class PersistStudent {  
      
    public static void main(String args[])  
    {  
          
        EntityManagerFactory emf=Persistence.createEntityManagerFactory("Student_details");  
        EntityManager em=emf.createEntityManager();  
        em.getTransaction().begin();  
          
        StudentEntity s1=new StudentEntity();  
        s1.setS_name("Gaurav");  

        em.persist(s1);  

        em.getTransaction().commit();  
        emf.close();  
        em.close();  
    }  
}  
```

[맨위로](#JPA)

### 엔티티를 조회하는 과정
엔티티를 조회하기 위해 EntityManager 인터페이스는 기본 키를 기준으로 조회하는 find() 메서드를 제공합니다.   
* 엔티티 클래스를 생성합니다.
* persistence.xml 파일에서 엔티티 클래스 및 기타 데이터베이스 구성을 매핑합니다.
* 조회 작업을 하기 위한 클래스를 생성하고 아래와 같이 작업합니다.
```
package com.javatpoint.jpa.find;  
import javax.persistence.*;  
  
import com.javatpoint.jpa.student.*;  
  
public class FindStudent {  
    public static void main(String args[])  
    {  
        EntityManagerFactory emf=Persistence.createEntityManagerFactory("Student_details");  
        EntityManager em=emf.createEntityManager();  
          
        StudentEntity s=em.find(StudentEntity.class,101);  
          
        System.out.println("Student id = "+s.getS_id());  
        System.out.println("Student Name = "+s.getS_name());  
        System.out.println("Student Age = "+s.getS_age());  
          
    }  
}  
```

[맨위로](#JPA)

### 엔티티를 수정하는 과정
JPA를 사용하면 엔티티를 업데이트하여 데이터베이스의 레코드를 변경할 수 있습니다.
* 엔티티 클래스를 생성합니다.
* persistence.xml 파일에서 엔티티 클래스 및 기타 데이터베이스 구성을 매핑합니다.
* 수정 작업을 하기 위한 클래스를 생성하고 아래와 같이 작업합니다.
```
package com.javatpoint.jpa.update;  
import javax.persistence.*;  
  
import com.javatpoint.jpa.student.*;  
public class UpdateStudent {  
      
    public static void main(String args[])  
    {  
        EntityManagerFactory emf=Persistence.createEntityManagerFactory("Student_details");  
        EntityManager em=emf.createEntityManager();  

        StudentEntity s=em.find(StudentEntity.class,102);  
        System.out.println("Before Updation");  
        System.out.println("Student Name = "+s.getS_name());  

        s.setName("Ayush");  
        System.out.println("After Updation");  
        System.out.println("Student Name = "+s.getS_name());  
    }  
}  
```

[맨위로](#JPA)

### 엔티티를 삭제하는 과정
데이터베이스에서 레코드를 삭제하기 위해 EntityManager 인터페이스는 remove() 메서드를 제공합니다.   
remove() 메서드는 기본 키를 사용하여 특정 레코드를 삭제합니다.   
* 엔티티 클래스를 생성합니다.
* persistence.xml 파일에서 엔티티 클래스 및 기타 데이터베이스 구성을 매핑합니다.
* 삭제 작업을 하기 위한 클래스를 생성하고 아래와 같이 작업합니다.
```
package com.javatpoint.jpa.delete;  
import javax.persistence.*;  
import com.javatpoint.jpa.student.*;  
  
public class DeleteStudent {  
  
    public static void main(String args[]) {  
        EntityManagerFactory emf=Persistence.createEntityManagerFactory("Student_details");  
        EntityManager em=emf.createEntityManager();  
        em.getTransaction().begin();  
        
        StudentEntity s=em.find(StudentEntity.class,102);  
        em.remove(s);  

        em.getTransaction().commit();  
        emf.close();  
        em.close();  
    }  
}  
```

[맨위로](#JPA)

## 엔티티 매핑의 방향
매핑의 방향은 단방향 또는 양방향일 수 있습니다.   
단방향 매핑에서는 한 엔티티에만 다른 엔티티를 매핑하고,   
양방향 매핑에서는 각 엔티티를 다른 엔티티에 매핑합니다.   

[맨위로](#JPA)

## 엔티티 매핑의 종류
* 일대일 매핑(OneToOne)
  * 한 엔티티의 인스턴스가 다른 엔티티의 인스턴스와 연결되는 단일 연결을 나타냅니다.
  * 엔티티의 인스턴스 하나를 대상 엔티티의 인스턴스 하나와 매핑합니다.
* 일대다 매핑(OneToMany)
  * 엔티티가 다른 엔티티 컬렉션과 연결된 것입니다.
  * 한 엔티티의 인스턴스를 다른 엔티티의 인스턴스 수에 관계없이 매핑할 수 있습니다.
* 다대일 매핑(ManyToOne)
  * 엔티티 컬렉션을 다른 엔티티와 연결할 수 있는 단일 연결을 나타냅니다.
  * 관계형 데이터베이스에서 둘 이상의 엔티티 행이 다른 엔티티의 동일한 행을 참조합니다.
* 다대다 매핑(ManyToMany)
  * 원하는 수의 엔티티를 다른 엔티티 컬렉션과 연결하는 것입니다.
  * 관계형 데이터베이스에서 둘 이상의 엔티티 행이 다른 엔티티의 여러 행을 참조할 수 있습니다.

[맨위로](#JPA)

## orphanRemoval
일대일 또는 일대다 연결의 대상 엔티티가 매핑에서 제거되면 삭제 작업이 엔티티에 수행될 수 있습니다.   
이러한 대상 엔티티를 고아(orpahns)라고 하며 orphanRemoval 속성을 사용하여 매핑이 끊어진 엔티티를 삭제해야 함을 지정할 수 있습니다.   

[맨위로](#JPA)

## 객체의 영속성 생명 주기
* Transient
  * new 키워드를 사용하여 방금 선언된 객체는 transient 상태에 있다고 호출됩니다.
  * 객체가 transient 상태로 유지되면 데이터베이스에 기본 key가 포함되지 않습니다.
* Persistence
  * 객체가 세션과 연결되고 데이터베이스에 저장되거나 데이터베이스에서 검색됩니다.   
  * 객체가 영속성 상태로 유지되면 데이터베이스의 행과 식별자 값을 포함하게 됩니다.
  * 객체를 Hibernate 세션과 연결하여 영속성 객체로 만들 수 있습니다.   
* Detached
  * Hibernate 세션이 닫히면 객체가 분리된 상태가 됩니다.
  * 분리된 객체에 대한 변경 내용은 데이터베이스에 저장되지 않습니다.

[맨위로](#JPA)

## 식별자 생성 유형
@GeneratedValue 어노테이션으로 지정하는데 필요한 ID 생성 전략 유형입니다.
* 자동 ID 생성
  * 애플리케이션은 ID 생성 종류에 상관하지 않습니다.   
  * 값을 명시적으로 지정하지 않으면 기본적으로 생성 타입이 auto로 설정됩니다.
* 테이블을 사용하여 ID 생성
  * 데이터베이스 테이블을 사용하여 식별자를 생성할 수 있습니다.
* 데이터베이스 시퀀스를 사용한 ID 생성
  * 데이터베이스는 시퀀스라고 하는 ID 생성을 위한 내부 메커니즘을 지원합니다.
  * 데이터베이스 시퀀스 이름을 사용자 정의하려면 @SequenceGenerator 애노테이션을 사용합니다.
* 데이터베이스 ID를 사용한 ID 생성
  * 테이블에 행을 삽입할 때마다 고유 식별자가 ID 열에 할당되어 객체의 식별자를 생성하는데 사용할 수 있습니다.

[맨위로](#JPA)

## 엔티티
엔티티는 단일 단위로 함께 연결된 상태 그룹입니다.   
엔티티는 객체로서 동작하며 객체 지향 패러다임의 주요 구성 요소가 됩니다.   
즉, 엔티티는 Java Persistence Library의 애플리케이션 정의 객체라고 할 수 있습니다.   
각 엔티티는 XML 또는 애노테이션 형식으로 정보를 나타내는 메타데이터와 연결됩니다.   

[맨위로](#JPA)

## EntityManager의 역할
* API를 구현하고 모든 API를 단일 인터페이스 내에 캡슐화합니다.   
* 엔티티를 읽고 삭제하고 쓰는데 사용됩니다.
* 엔티티가 참조하는 객체를 관리합니다.

[맨위로](#JPA)

## 엔티티 클래스의 제약조건
* NoArgumentConstructor가 있어야 합니다.   
* 클래스가 final 일 수 없습니다.    
* @Entity가 있어야 합니다.   
* detached 상태의 빈 인스턴스를 객체로 전달하는 경우 Serializable 인터페이스를 구현해야 합니다.   

[맨위로](#JPA)

## JPA에서 Java 컬렉션의 목적은 무엇입니까?
래퍼 클래스 및 문자열 객체의 영속성을 유지하기 위해 사용합니다.   

[맨위로](#JPA)

## JPA 컬렉션 매핑에 저장할 수 있는 객체 타입은 무엇입니까?
* 기본 타입
* 엔티티
* Embeddable 타입

[맨위로](#JPA)

## JPA에서 사용할 수 있는 컬렉션 타입은 무엇입니까?
* List
* Set
* Map

[맨위로](#JPA)

## JPA Cascade의 목적은 무엇입니까?
한 엔티티에 작업을 적용한 다음 cascade를 사용하면 관련 엔티티에도 해당 작업을 적용할 수 있습니다.

[맨위로](#JPA)

## JPA가 지원하는 Cascade 유형은 무엇입니까?
* PERSIST
  * 상위 엔티티가 영속화되면 모든 관련 엔티티도 영속화됩니다.   
* MERGE
  * 상위 엔티티가 병합되면 모든 관련 엔티티도 병합됩니다.
* DETACH
  * 상위 엔티티가 분리되면 모든 관련 엔티티도 분리됩니다.
* REFRESH
  * 상위 엔티티가 REFRESH되면 모든 관련 엔티티도 REFRESH 됩니다.   
* REMOVE
  * 상위 엔티티가 제거되면 모든 관련 엔티티도 제거됩니다.
* ALL
  * 위의 모든 유형을 상위 엔티티와 관련된 엔티티에 적용할 수 있습니다.

[맨위로](#JPA)

## JPQL이란 무엇입니까?
JPQL(Java Persistence Query Language)는 영속성 엔티티에 대한 조회를 정의하는 JPA 스펙의 일부입니다.   
영속성 엔티티에 대한 데이터베이스 작업을 수행하는 데 사용되는 객체 지향 쿼리 언어입니다.   
데이터베이스 테이블 대신 JPQL은 엔티티 객체 모델을 사용하여 SQL 조회를 작동합니다.   
여기서 JPA의 역할은 JPQL을 SQL로 변환하는 것입니다.   
개발자가 SQL 작업을 쉽게 처리할 수 있는 플랫폼을 제공합니다.   

[맨위로](#JPA)

## JPQL의 특징
* 간단하고 견고합니다.
* 플랫폼 독립적인 쿼리 언어입니다.
* 정적, 동적 쿼리가 모두 가능합니다.
* MySQL, Oracle과 같은 모든 데이터베이스에서 사용할 수 있습니다.

[맨위로](#JPA)

## Criteria API란 무엇입니까?
Java API를 사용하여 작성된 Type-safe한 쿼리를 제공하는 스펙입니다.   
엔티티 및 영속 상태에 대한 쿼리를 구성하는 방법 중 하나입니다.   
JPA 쿼리를 정의하는 방법입니다.   
Java 언어로 작성된 플랫폼 독립적인 쿼리를 정의합니다.   
JPA 2.0부터 제공되었습니다.   
주된 목적은 쿼리를 Type-safe하게 작성하도록 하는 것입니다.   

[맨위로](#JPA)

## 참고
* [Top 30 JPA Interview Questions (2021) - javatpoint](https://www.javatpoint.com/jpa-interview-questions)

[맨위로](#JPA)
