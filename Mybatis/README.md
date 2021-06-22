# Mybatis
* [mybatis란?]()
* [mybatis의 장점]()
* [mybatis의 단점]()
* [mybatis를 사용하면 좋은 경우]()
* [Mybatis와 Hibernate의 차이점]()
* [#{}와 ${}의 차이점]()
* [엔티티 클래스의 필드명이 테이블의 필드명과 다른 경우 어떻게 해야될까?]()
* [Dao 인터페이스의 작동 원리]()
* [Dao 인터페이스의 메소드는 매개 변수가 다른 경우 메소드를 오버로드 할 수 있나요?]()
* [Mybatis는 어떻게 페이징됩니까?]()
* [페이징 플러그인의 원리]()
* [Mybatis는 SQL 실행 결과를 대상 객체로 어떻게 캡슐화하고 반환합니까?]()
* [bulk(대용량) insert는 어떻게 수행합니까?]()
* [자동 증가 key값은 어떻게 얻습니까?]()
* [Mapper에서 여러 매개 변수를 전달하는 방법은?]()
* [Mybatis 동적 SQL의 기능은 무엇입니까?]()
* [XML 맵핑 파일에서 일반적인 select, insert, update, delete 태그 외에 어떤 다른 태그가 있습니까?]()
* [Mybatis의 XML 맵핑 파일에서 다른 XML 맵핑 파일의 id를 사용할 수 있습니까?]()
* [Mybatis를 왜 반자동 ORM 매핑 도구라고 하나요?]()
* [일대일, 일대다 연관관계 쿼리 작성 방법]()
* [Mybatis는 일대일 연관관계를 어떻게 구현합니까?]()
* [Mybatis는 일대다 연관관계를 어떻게 구현합니까?]()
* [Mybatis 플러그인의 작동 방식]()
* [Mybatis 플러그인 작성 방법]()
* [Mybatis는 지연 로딩을 지원합니까?]()
* [Mybatis 지연 로딩 구현 원리]()

## mybatis란?
* jdbc를 내부적으로 캡슐화하는 java 기반 영속성 계층 프레임워크이다.
  * 개발자는 드라이버 로드, 커넥션 생성 등의 복잡한 프로세스를 처리하지 않고 SQL 쿼리문 자체에만 집중하면 된다.
* xml 또는 annotation으로 실행할 다양한 쿼리를 작성하고, java 객체와 쿼리문의 동적 매개 변수를 매핑하여 최종 실행된 SQL문을 생성한다.
  * 마지막으로 mybatis 프레임 워크는 SQL을 실행하고 결과를 Java 객체에 매핑하여 반환한다.
* 사용자 지정 SQL, 프로시저 및 고급 매핑을 지원한다.
  * mybatis는 거의 모든 JDBC 코드를 피하고 수동으로 매개 변수를 설정하고 결과를 가져온다.
  * 간단한 XML 또는 주석을 사용하여 기본 정보, 매핑 인터페이스 및 Java POJO를 데이터베이스의 레코드에 구성하고 매핑할 수 있다.

[맨위로](#Mybatis)

## mybatis의 장점
* Hibernate에 비해 배우기 쉽고 사용하기 쉽다.
  * SQL 프로그래밍 기반
* JDBC에 비해 코드량을 50% 이상 줄이고, JDBC 대용량 중복 코드를 제거하며, 수동으로 커넥션을 연결할 필요가 없다.
* 다양한 데이터베이스와 호환된다.
* 다양한 플러그인이 제공된다.
* Spring과의 결합도가 좋다.
* 매우 유연하며 애플리케이션 또는 데이터베이스의 기존 디자인에 영향을 주지 않는다.
  * SQL은 프로그램 코드와 완전히 분리된 XML로 작성되며 SQL과 프로그램 코드 간의 결합이 제거되어 통합 관리 및 최적화가 용이하다.
  * 재사용 가능하다.
* 동적 SQL문 작성을 지원하는 XML 태그를 제공한다.
* 객체와 데이터베이스 간의 ORM 필드 관계 매핑을 지원하는 매핑 라벨을 제공한다.
* 객체 관계 그룹 유지 관리를 지원하기 위해 객체 관계 매핑 라벨을 제공한다.

[맨위로](#Mybatis)

## mybatis의 단점
* 필드와 테이블이 많은 경우 SQL문 작성 많아진다.
* SQL문은 데이터베이스에 의존하여 데이터베이스의 이식성이 떨어지고, 데이터베이스를 마음대로 변경할 수 없다.

[맨위로](#Mybatis)

## mybatis를 사용하면 좋은 경우
웹 프로젝트와 같이 고성능 요구 사항이나 더 많은 수요 변화가 있는 프로젝트에 적합하다.

[맨위로](#Mybatis)

## Mybatis와 Hibernate의 차이점
* mybatis는 ORM 프레임워크가 아니다.
  * mybatis는 프로그래머가 Sql문을 직접 작성해야 한다.
* mybatis는 학습 임계값이 낮고 배우기 쉽다.
  * 프로그래머는 SQL의 실행 성능을 제어할 수 있고 유연성이 높은 SQL을 직접 작성한다.
  * 인터넷 소프트웨어 및 기업 운영과 같은 관계형 데이터 모델에 대한 요구사항이 낮은 소프트웨어 개발에 매우 적합하다.
  * 소프트웨어는 수요 변화에 따라 빠른 수정이 필요하다.
  * 그러나 여러 데이터베이스를 지원하는 소프트웨어를 구현해야 하는 경우 많은 SQL 매핑 파일을 만들어야 한다.
* Hibernate를 사용하면 더 많은 코드를 절약하고 효율성을 높일 수 있다.
  * 그러나 Hibernate의 단점은 높은 학습 임계값과 ORM 매핑 설계가 매우 잘되어야 한다는 것이다.
  * 이것은 많은 경험과 능력이 필요하다.

[맨위로](#Mybatis)

## #{}와 ${}의 차이점
#{}은 프리컴파일되고 ${}은 문자열을 대체한다.   
> 프리컴파일: 고급언어를 기계어로 번역하는 컴파일(Complie) 전에 수행하는 작업으로, 필요한 라이브러리를 불러오거나 코드에 삽입된 SQL문을 DB와 연결하는 작업을 수행한다.   

mybatis는 #{}을 처리할 때 sql의 #{}를 ?로 바꾸고 PreparedStatement의 set 메서드를 호출하여 값을 할당한다.   
mybatisrk ${}를 처리할 때 ${}를 변수 값으로 바꾼다.   
#{}를 사용하면 SQL injection을 효과적으로 방지하고 시스템 보안을 향상시킬 수  있다.   

[맨위로](#Mybatis)

## 엔티티 클래스의 필드명이 테이블의 필드명과 다른 경우 어떻게 해야될까?
* case1: 쿼리의 SQL문에서 테이블 필드를 엔티티 클래스의 필드명과 같게 alias를 정의한다.
* case2: <resultMap>을 사용하여 테이블 필드와 엔티티 클래스 필드를 매핑한다.

[맨위로](#Mybatis)

## Dao 인터페이스의 작동 원리
인터페이스의 이름은 매핑 파일의 namespace 값이다.   
인터페이스의 메서드 이름은 매핑 파일에 있는 MappedStatement의 id 값이다.   
인터페이스 메서드의 매개 변수는 sql로 전달된다.   
Mapper 인터페이스는 구현 클래스가 없다.   
인터페이스 메서드가 호출되면 인터페이스 이름 + 메서드 이름을 연결한 문자열이 key값으로 사용된다.   
이를 통해 MappedStatement를 찾을 수 있다.      
ex) com.mybatis3.mappers.StudentDto.findStudentById
Mybatis에서 각 <select>, <insert>, <update>, <delete> 태그는 MappedStatement Object로 파싱된다.

Dao 인터페이스의 작동 원리는 JDK 동적 프록시이다.   
Mybatis 런타임은 JDK 동적 프록시를 사용하여 Dao 인터페이스에 대한 프록시 객체를 생성한다.   
프록시는 인터페이스 메소드를 캐치해서 MappedStatement가 나타내는 sql을 실행한 후 SQL 실행 결과를 반환한다.

[맨위로](#Mybatis)

## Dao 인터페이스의 메소드는 매개 변수가 다른 경우 메소드를 오버로드 할 수 있나요?
Dao 인터페이스의 메서드는 인터페이스명 + 메서드명에 대한 저장 및 검색 전략이므로 오버로드할 수 없다.

[맨위로](#Mybatis)

## Mybatis는 어떻게 페이징됩니까?
Mybatis는 페이징에 RowBounds 객체를 사용한다.   
실제 페이지가 아니라 ResultSet 결과에 대한 메모리 페이지이다.   
SQL에서 물리적 페이징을 사용하여 매개 변수를 직접 작성하여 수행하거나 페이징 플러그인을 사용하여 수행할 수 있다.   

[맨위로](#Mybatis)

## 페이징 플러그인의 원리
페이징 플러그인의 기본 원리는 Mybatis에서 제공하는 플러그인 인터페이스를 사용하여 사용자 정의 플러그인을 구현하고,   
플러그인 인터셉션 메서드에서 실행될 SQL을 가로챈 다음 방언에 따라 SQL을 다시 작성하고 해당 물리적 페이징 명령문 및 물리적 페이징 매개 변수를 추가한다.   

[맨위로](#Mybatis)

## Mybatis는 SQL 실행 결과를 대상 객체로 어떻게 캡슐화하고 반환합니까?
첫번째, <resultMap> 태그를 사용하여 열 이름과 객체 속성 이름 간의 맵핑을 하나씩 정의한다.   
두번째, SQL 열의 alias 함수를 사용하여 열 alias를 T_NAME AS NAME과 같은 객체 속성 이름으로 쓴다.   
객체 속성 이름은 일반적으로 이름, 소문자이지만 mybatis는 열 이름의 대소 문자를 구분하지 않는다.   
열 이름과 속성 이름 간의 맵핑을 통해 Mybatis는 리플렉션을 통해 객체를 만들고 리플렉션을 사용하여 객체의 속성을 하나씩 할당하고 반환한다.   
맵핑 관계를 찾을 수 없는 경우에는 할당을 완료할 수 없다.

[맨위로](#Mybatis)

## bulk(대용량) insert는 어떻게 수행합니까?
insert문을 만든 후 Java 코드에서 반복문을 통해 insert를 수행해야 한다.   

[맨위로](#Mybatis)

## 자동 증가 key값은 어떻게 얻습니까?
insert 메서드는 항상 int 값을 반환한다.   
이 값은 insert된 행의 수를 나타낸다.   
자동 증가 key값은 insert 메서드가 실행된 후 전달된 매개 변수 객체로 설정될 수 있다.   
```
<insert id="insertname" useGeneratedKeys="true" keyProperty="order_id">
    insert into names (name) values (#{name})
</insert>
```

[맨위로](#Mybatis)

## Mapper에서 여러 매개 변수를 전달하는 방법은?
* 전달한 매개변수 순서대로 #{0}, #{1}, ... 으로 사용할 수 있다.   
```
//DAO layer function
Public UserselectUser(String name,String area);  
 
 //The corresponding xml, #{0} represents the first parameter in the dao layer, and #{1} represents the second parameter in the dao layer. More parameters can be added later.
<select id="selectUser"resultMap="BaseResultMap">  
    select *  fromuser_user_t   whereuser_name = #{0} anduser_area=#{1}  
</select>  
```
* \@Param 애노테이션 사용
```
user selectuser(@param(“username”) string username, @param(“hashedpassword”) string hashedpassword);

<select id=”selectuser” resulttype=”user”>
         select id, username, hashedpassword
         from some_table
         where username = #{username}
         and hashedpassword = #{hashedpassword}
</select>
```
* Map이나 객체로 전달하여 key 값 또는 객체의 필드명을 사용할 수 있다.

[맨위로](#Mybatis)

## Mybatis 동적 SQL의 기능은 무엇입니까?
Mybatis 동적 SQL을 사용하면 XML 매핑 파일에 태그 형태로 동적 SQL을 작성하여 논리 판단 및 동적 SQL 기능을 수행할 수 있다.   
Mybatis는 9개의 동적 SQL 태그를 제공한다.
  * trim
  * where
  * set
  * foreach
  * if
  * choose
  * when
  * otherwise
  * bind   
실행원리는 OGNL(Object Graph Navigation Language)를 사용하여 sql 매개 변수 객체에서 식의 값을 계산하고, 식의 값에 따라 SQL이 동적으로 연결되어 동적 SQL의 기능을 완성한다.   

[맨위로](#Mybatis)

## XML 맵핑 파일에서 일반적인 select, insert, update, delete 태그 외에 어떤 다른 태그가 있습니까?
<resultMap>, <parameterMap>, <sql>, <include>, <selectKey> 및 동적 SQL에 대한 9개의 태그가 있다.   
trim, where, set, foreach, if, choose, otherwhise, bind 등등   
여기서 <sql>은 sql fragment 태그, sql fragment는 <include> 태그를 통해 도입되고, <selectKey>는 자동 증가를 지원하지 않는 기본 키에 대한 정책 태그를 생성한다.   

[맨위로](#Mybatis)

## Mybatis의 XML 맵핑 파일에서 다른 XML 맵핑 파일의 id를 사용할 수 있습니까?
다른 XML 맵핑 파일, 다른 namespace일 경우 id를 반복 사용할 수 있다.   
namepsace가 구성되지 않은 경우에는 id를 반복할 수 없다.   
(namaspace는 필수가 아닌 모범 사례이다.)   

그 이유는 namespace + id가 Map<String, MappedStatement> 형태로 사용되기 때문이다.   
namespace가 없으면 id만 남는다.   
그러면 id가 서로 겹치게 된다.   
따라서 namespace를 사용하면 id가 반복되더라도 namepsace가 다르기때문에 반복 사용할 수 있다.

[맨위로](#Mybatis)

## Mybatis를 왜 반자동 ORM 매핑 도구라고 하나요?
Hibernate는 완전 자동 ORM 매핑 도구이다.   
Hibernate를 사용하여 관련 객체 또는 관련 컬렉션 객체를 쿼리할 때 객체 관계 모델에 따라 직접 얻을 수 있으므로 완전 자동이다.   
Mybatis는 쿼리 관련 객체 또는 관련 컬렉션 객체를 완성하기 위해 SQL을 수동으로 작성해야하므로 반자동 ORM 매핑 도구라고 한다.   

[맨위로](#Mybatis)

## 일대일, 일대다 연관관계 쿼리 작성 방법
* 일대일 연관 관계
```
<select id="getClass" parameterType="int" resultMap="ClassesResultMap">
    select * from class c,teacher t where c.teacher_id=t.t_id and c.c_id=#{id}
</select>

<resultMap type="com.lcb.user.Classes" id="ClassesResultMap">
    <!-- Field name of entity class and field name mapping of data table -->
    <id property="id" column="c_id"/>
    <result property="name" column="c_name"/>
    <association property="teacher" javaType="com.lcb.user.Teacher">
        <id property="id" column="t_id"/>
        <result property="name" column="t_name"/>
    </association>
</resultMap>
```
* 일대다 연관 관계
```
<select id="getClass2" parameterType="int" resultMap="ClassesResultMap2">
    select * from class c,teacher t,student s where c.teacher_id=t.t_id and c.c_id=s.class_id and c.c_id=#{id}
</select>

<resultMap type="com.lcb.user.Classes" id="ClassesResultMap2">
    <id property="id" column="c_id"/>
    <result property="name" column="c_name"/>
    <association property="teacher" javaType="com.lcb.user.Teacher">
        <id property="id" column="t_id"/>
        <result property="name" column="t_name"/>
    </association>

    <collection property="student" ofType="com.lcb.user.Student">
        <id property="id" column="s_id"/>
        <result property="name" column="s_name"/>
    </collection>
</resultMap>
```

[맨위로](#Mybatis)

## Mybatis는 일대일 연관관계를 어떻게 구현합니까?
일대일 관계를 구성하기 위해 resultMap에서 association 태그를 사용한다.   

[맨위로](#Mybatis)

## Mybatis는 일대다 연관관계를 어떻게 구현합니까?
일대다 관계를 구성하기 위해 resultMap에서 collection 태그를 사용한다.

[맨위로](#Mybatis)

## Mybatis 플러그인의 작동 방식
Mybatis는 ParameterHandler, ResultSetHandler, StatementHandler, Executor 네 가지 인터페이스에 대한 플러그인만 작성할 수 있다.   
Mybatis는 JDK의 동적 프록시를 사용하여 인터페이스에 대한 프록시 객체를 생성한다.   
이 인터페이스가 실행될 때마다 객체의 메서드가 InvocationHandler의 invoke() 메서드에 들어간다.   
물론 인터셉트하도록 지정한 메서드만 인터셉트한다.   

[맨위로](#Mybatis)

## Mybatis 플러그인 작성 방법
Mybatis의 인터셉터 인터페이스를 구현하고 intercept() 메서드를 재정의 한 다음    
플러그인에 대한 애노테이션을 작성하고 어떤 인터페이스를 인터셉트하는 메서드인지 명시한다.   
그리고 작성한 플러그인을 config 파일에 구성한다.   

[맨위로](#Mybatis)

## Mybatis는 지연 로딩을 지원합니까?
Mybatis는 지연로딩만 지원한다.   
Mybatis config 파일에서 lazyLoadingEnabled = true | false 를 통해 활성화 한다.   

[맨위로](#Mybatis)

## Mybatis 지연 로딩 구현 원리
CGLIB(Code Generator Library)를 사용하여 대상 객체의 프록시 객체를 만든다.   
메소드를 호출할 때 a.getB().getName()과 같은 메서드를 호출하면 인터셉터 invoke()메서드가 a.getB()가 null 값임을 확인한 다음   
이전에 저장된 B객체와 연관된 SQL쿼리가 별도로 전송되고 쿼리가 실행된 다음 a.setB(b)가 호출되어 a에 B객체가 로딩되게 된다.   

[맨위로](#Mybatis)

## 참고
* [Mybatis three common interview questions](https://www.programmersought.com/article/8568335616/)

[맨위로](#Mybatis)