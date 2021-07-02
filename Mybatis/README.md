# Mybatis
* [Mybatis](#mybatis-1)
* [mybatis의 장점](#mybatis의-장점)
* [mybatis의 단점](#mybatis의-단점)
* [Mybatis와 Hibernate의 차이점](#mybatis와-hibernate의-차이점)
* [#{}와 ${}의 차이점](#와-의-차이점)
* [엔티티 클래스의 필드명과 테이블의 필드명 매핑 방법]()
* [like문 작성 방법]()
* [Dao 인터페이스의 작동 원리](#dao-인터페이스의-작동-원리)
* [페이징 처리 방법]()
* [SQL 실행 결과를 객체로 매핑하는 방법]()
* [Batch insert 하는 방법]()
* [자동 생성 key 생성 방법]()
* [Mapper에서 여러 매개 변수를 전달하는 방법]()
* [동적 SQL]()
* [XMl 매핑 파일 태그 종류]()
* [서로 다른 XML 매핑 파일 간 ID 중복 가능 여부]()
* [Mybatis가 완전한 ORM 매핑 도구가 아닌 이유]()
* [일대일, 일대다 연관관계 쿼리 작성 방법](#일대일-일대다-연관관계-쿼리-작성-방법)
* [일대일 연관관계 구현 방법]()
* [일대다 연관관계 구현 방법]()
* [지연 로딩]()
* [primiary 및 secondary 캐시]()
* [인터페이스 바인딩]()
* [어노테이션 바인딩과 xml 바인딩]()
* [Mapper 인터페이스 정의하는 방법]()
* [iBatis 및 MyBatis의 핵심 처리 클래스]()
* [iBatis와 MyBatis의 차이점 및 개선된 점]()
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## Mybatis
* Java 기반 영속성 계층 프레임워크입니다.
* 내부적으로 jdbc를 캡슐화하므로 개발자가 Driver 로드, Connection 생성, Statement 생성 등의 복잡한 프로세스를 처리할 필요 없이 SQL문 자체에만 신경쓰면 됩니다.   
* xml 또는 annotation으로 실행할 다양한 statement을 구성하고, java 객체에 있는 sql의 동적 파라미터와 statement를 매핑하여 최종 실행된 SQL문을 생성합니다.   
* sql을 실행하고 결과를 Java 객체에 매핑한 후 반환합니다.   
* 사용자 정의 SQL, 저장 프로시저, 고급 매핑을 지원합니다.   
* 거의 모든 JDBC 코드를 사용하지 않고 수동으로 매개 변수를 설정하고 결과를 가져옵니다.   
* xml 또는 annotation을 사용하여 매핑 인터페이스 및 Java POJO를 데이터베이스의 레코드에 구성하고 매핑할 수 있습니다.   
* SQL 자체에 중점을 두고 있으며 충분히 유연한 DAO 계층 솔루션입니다.

[맨위로](#Mybatis)

## mybatis의 장점
* Hibernate에 비해 배우기 쉽고 사용하기 쉽습니다.   
  * Mybatis는 SQL 프로그래밍을 기반으로 하기 때문입니다.
* JDBC와 비교하여 코드량을 50% 이상 줄여 JDBC 대용량 중복 코드를 제거하며, 수동으로 Connection을 생성할 필요가 없습니다.   
* 다양한 데이터베이스와 호환됩니다.   
* Spring과 잘 통합됩니다.   
* 매우 유연하며 애플리케이션 또는 데이터베이스의 기존 설계에 영향을 미치지 않습니다.   
* SQL은 프로그램 코드와 완전히 분리된 XML로 작성되며 SQL과 프로그램 코드 간의 결합을 제거하여 관리 및 최적화가 용이합니다.
* 재사용성이 좋습니다.   
* 동적 SQL statement를 지원하는 XML 태그를 제공합니다.
* 객체 및 데이터베이스 간 ORM 필드 관계 매핑을 지원하는 매핑 기능을 제공합니다.   
* 객체간 연관 관계를 지원하기 위한 객체 관계 매핑 기능을 제공합니다.    

[맨위로](#Mybatis)

## mybatis의 단점
* 필드와 관련 테이블이 많은 경우 SQL문 작성 규모가 커집니다.   
* SQL문은 데이터베이스에 따라 달라지므로 데이터베이스를 변경하기가 어렵다.   

[맨위로](#Mybatis)

## Mybatis와 Hibernate의 차이점
* mybatis는 ORM 프레임워크가 아닙니다.   
  * 프로그래머가 SQL문을 직접 작성해야하기 때문입니다.   
* mybatis는 학습 임계값이 낮고 배우기 쉽습니다.  
  * SQL 프로그래밍을 기반으로 하기 때문입니다.   
* mybatis는 데이터베이스와 독립적이지 않습니다.   
  * 여러 데이터베이스를 지원하는 소프트웨어를 구현해야 하는 경우 여러 세트의 SQL 매핑 파일을 사용자가 정의해야하기 때문입니다.
* Hibernate는 데이터베이스와 독립적입니다.    
  * mybatis보다 더 많은 코드를 줄이고 효율성을 향상시킬 수 있습니다.
* Hibernate는 높은 학습 임계값과 높은 숙련도가 필요합니다.   
  * ORM 매핑 설계 및 성능과 객체 모델의 균형을 조정하는 방법 등은 많은 경험과 능력을 필요로 합니다.     

[맨위로](#Mybatis)

## #{}와 ${}의 차이점
#{}
* 미리 컴파일됩니다.
* SQL의 #{}이 ```?```로 대체되고 PreparedStatement의 set 메서드를 호출하여 값을 할당합니다.     
* SQL injection을 효과적으로 방지하고 시스템 보안을 향상시킬 수 있습니다.   

${}
* 문자열을 대체합니다.   
* ${}가 변수 값으로 대체됩니다.   

[맨위로](#Mybatis)

## 엔티티 클래스의 필드명과 테이블의 필드명 매핑 방법
case1: SQL문 필드 이름의 alias를 엔티티 클래스의 필드명으로 정의합니다.      
```
<select id=”selectorder” parametertype=”int” resultetype=”me.gacl.domain.order”>
    select order_id id, order_no orderno ,order_price price form orders where order_id=#{id};
</select>
```

case2: 필드 이름과 엔티티 클래스 속성 이름 간의 일대일 대응 관계를 \<resultMap>에 매핑합니다.   
```
<select id="getOrder" parameterType="int" resultMap="orderresultmap">
    select * from orders where order_id=#{id}
</select>

<resultMap type=”me.gacl.domain.order” id=”orderresultmap”>
    <!– 기본 key 필드를 id 속성에 매핑합니다 –>
    <id property=”id” column=”order_id”>

    <!– 기본 key 필드가 아닌 필드들을 엔티티 클래스 속성에 매핑합니다. –>
    <result property = “orderno” column =”order_no”/>
    <result property=”price” column=”order_price” />
</reslutMap>
```

[맨위로](#Mybatis)

## like문 작성 방법
case1: Java 코드에 SQL 와일드카드를 추가합니다.   
```
string wildcardname = "%smi%";
list<name> names = mapper.selectlike(wildcardname);

<select id="selectlike">
  select * from foo where bar like #{value}
</select>
```

case2: SQL문에 와일드카드를 작성합니다.   
```
string wildcardname = "smi";
list<name> names = mapper.selectlike(wildcardname);

<select id="selectlike">
      select * from foo where bar like "%"#{value}"%"
</select>
```

[맨위로](#Mybatis)

## Dao 인터페이스의 작동 원리
Dao 인터페이스는 Mapper 인터페이스입니다.   
인터페이스 이름은 매핑 파일의 namespace 값입니다.   
인터페이스 메서드의 이름은 매핑 파일에 있는 MappedStatement의 ID 값입니다.   
* MappedStatement 객체 종류
  * \<select>, \<insert>, \<update>, \<delete>   

인터페이스 메서드의 매개 변수는 SQL의 매개 변수로 전달됩니다.   
Mapper 인터페이스는 구현 클래스가 없습니다.   
인터페이스 메서드가 호출되면 인터페이스 이름 + 메서드 이름을 조합한 문자열이 key 값으로 사용됩니다.   
이 key 값을 통해 연결된 MapperStatement를 찾을 수 있습니다.   
* 예시) com.mybatis3.mappers.StudentDao.findStudentById
  * com.mybatis3.mappers.StudentDao를 통해 고유한 namespace를 찾을 수 있습니다.
  * findStudentById를 통해 해당 id 값을 갖는 MappedStatement를 찾을 수 있습니다.  
즉, Dao 인터페이스의 메서드는 인터페이스명 + 메서드명에 대한 저장 및 검색 전략이므로 오버로드할 수 없습니다.   

Dao 인터페이스의 작동 원리는 JDK Dynamic Proxy입니다.   
Mybatis는 JDK Dynamic Proxy를 사용하여 Dao 인터페이스에 대한 Proxy 객체를 생성합니다.   
프록시는 인터페이스 메서드를 인터셉트 한 다음 해당하는 MappedStatement를 찾아 SQL을 실행한 다음 SQL 실행 결과를 반환합니다.

[맨위로](#Mybatis)

## 페이징 처리 방법
Mybatis는 페이징을 하기 위해 RowBounds 객체를 사용할 수 있습니다.   
이것은 물리적인 페이지가 아니라 ResultSet 결과에 대한 메모리 페이지입니다.      

또한, SQL에서 매개 변수를 직접 작성하여 물리적 페이징 기능을 구현할 수 있습니다.

[맨위로](#Mybatis)

## SQL 실행 결과를 객체로 매핑하는 방법
첫번째 방법은 \<resultMap> 태그를 사용하여 열 이름과 객체 속성 이름 간의 맵핑을 하나씩 정의하는 것입니다.     
두번째는 SQL 열에 alias를 사용하여 객체 속성 이름으로 alias를 쓰는 것 입니다.
* 예시) T_NAME AS NAME   

일반적으로 객체 속성 이름은 소문자이지만 열 이름은 대소문자를 구분하지 않으므로   
mybatis는 열 이름의 대소 문자를 무시합니다.   

[맨위로](#Mybatis)

## Batch insert 하는 방법
먼저 간단한 insert문을 작성합니다.   
```
<insert id=”insertname”>
      insert into names (name) values (#{value})
</insert>
```

그런 다음 Java 코드로 아래와 같이 batch insert를 수행합니다.   
```
list<string> names = new arraylist();
names.add(“fred”);
names.add(“barney”);
names.add(“betty”);
names.add(“wilma”);

// executortype.batch 참고
sqlsession sqlsession = sqlsessionfactory.opensession(executortype.batch);
try {
  namemapper mapper = sqlsession.getmapper(namemapper.class);
  for (string name : names) {
      mapper.insertname(name);
  }
  sqlsession.commit();
}catch(Exception e){
  e.printStackTrace();
  sqlSession.rollback(); 
  throw e; 
}
  finally {
      sqlsession.close();
}
```

[맨위로](#Mybatis)

## 자동 생성 key 생성 방법
insert 메서드는 항상 int 값을 반환합니다.   
* 이 값은 insert된 행의 수를 나타냅니다.      

자동 증가 key값은 insert 메서드가 실행된 후 전달된 매개 변수 객체로 설정할 수 있습니다.   
```
<insert id=”insertname” usegeneratedkeys=”true” keyproperty=”id”>
     insert into names (name) values (#{name})
</insert>
```

```
name name = new name();
name.setname(“fred”);

int rows = mapper.insertname(name);
// 완료 후 id가 객체로 설정되었습니다.
system.out.println(“rows inserted = ” + rows);
system.out.println(“generated key value = ” + name.getid());
```

[맨위로](#Mybatis)

## Mapper에서 여러 매개 변수를 전달하는 방법
* 방법1: #{0}은 첫 번째 매개 변수를 나타내고, #{1}은 두 번째 매개 변수를 나타냅니다.   
```
//DAO 메서드
Public UserselectUser(String name,String area);  

<select id="selectUser"resultMap="BaseResultMap">  
    select *  fromuser_user_t   whereuser_name = #{0} anduser_area=#{1}  
</select>  
```
* 방법2: \@Param 애노테이션 사용
```
user selectuser(@param(“username”) string username, @param(“hashedpassword”) string hashedpassword);

<select id=”selectuser” resulttype=”user”>
         select id, username, hashedpassword
         from some_table
         where username = #{username}
         and hashedpassword = #{hashedpassword}
</select>
```
* 방법3: 여러 매개 변수를 Map에 캡슐화
```
try{
    Map<String, Object> map = new HashMap();
     map.put("start", start);
     map.put("end", end);
     return sqlSession.selectList("StudentID.pagination", map);
 } catch(Exception e){
     e.printStackTrace();
     sqlSession.rollback();
    throw e; 
} finally{
 MybatisUtil.closeSqlSession();
 }
```

[맨위로](#Mybatis)

## 동적 SQL
Mybatis 동적 SQL을 사용하면 동적 sql을 XML 매핑 파일에 태그 형식으로 작성하여 논리 판단 및 동적 쿼리를 작성할 수 있습니다.   
 
실행원리는 OGNL(Object Graph Navigation Language)를 사용하여 sql 파라미터 객체의 식 값을 계산하고,   
식 값에 따라 sql을 동적으로 분할하여 동적 sql 함수를 완성합니다.    

[맨위로](#Mybatis)

## XMl 매핑 파일 태그 종류
동적 SQL 태그
* trim, where, set, foreach, if, choose, when, otherwhise, bind

이외 다른 태그
* resultMap, parameterMap, sql, include, selectKey

여기서 \<sql>은 sql fragment 태그이고, sql fragment는 \<include> 태그를 통해 삽입됩니다.    
\<selectKey>는 자동 증가를 지원하지 않는 기본 키에 대한 정책 태그를 생성합니다.   

[맨위로](#Mybatis)

## 서로 다른 XML 매핑 파일 간 ID 중복 가능 여부
다른 XML 맵핑 파일, 다른 namespace일 경우 id를 반복 사용할 수 있습니다.   
* namepsace가 구성되지 않은 경우에는 id를 반복할 수 없습니다.   
* namaspace는 필수가 아닌 권장 사항입니다.   

그 이유는 namespace + id가 Map<String, MappedStatement>의 key로 사용되기 때문입니다.  
namespace가 없으면 id만 남아 있습니다.   
그러면 id가 서로 겹치게 됩니다.     
따라서 서로 다른 namespace를 사용하면 namespace + id가 다르기 때문에 id를 반복할 수 있습니다.

[맨위로](#Mybatis)

## Mybatis가 완전한 자동 ORM 매핑 도구가 아닌 이유
Hibernate는 완전한 자동 ORM 매핑 도구입니다.   
Hibernate를 사용하여 연관 객체 또는 연관 컬렉션 객체를 쿼리하는 경우 객체 관계 모델에 따라 직접 가져올 수 있으므로 완전 자동입니다.  
Mybatis는 연관 객체 또는 연관 컬렉션 캑체를 쿼리하려면 SQL을 수동으로 작성해야 하므로 반자동 ORM 매핑 도구라고 합니다.   

[맨위로](#Mybatis)

## 일대일, 일대다 연관관계 쿼리 작성 방법
* 일대일 연관 관계
```
<select id="getClass" parameterType="int" resultMap="ClassesResultMap">
    select * from class c,teacher t where c.teacher_id=t.t_id and c.c_id=#{id}
</select>

<resultMap type="com.lcb.user.Classes" id="ClassesResultMap">
    <!-- 엔티티 클래스의 필드명과 테이블의 필드명을 매핑합니다. -->
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

## 일대일 연관관계 구현 방법
조인을 사용하는 방법과 여러번의 쿼리를 사용하는 방법이 있습니다.   

조인을 사용하는 방법   
* 한번만 쿼리하면 됩니다.   
* resultMap에 association 태그를 구성해야 합니다.   

여러번의 쿼리를 사용하는 방법
* 먼저 한 테이블을 조회합니다.   
* 조회한 결과에서 외래키 값을 가져와서 다른 테이블을 조회합니다.   

[맨위로](#Mybatis)

## 일대다 연관관계 구현 방법
조인을 사용하는 방법과 여러번의 쿼리를 사용하는 방법이 있습니다.   

조인을 사용하는 방법   
* 한번만 쿼리하면 됩니다.   
* resultMap에 collection 태그를 구성해야 합니다.  

여러번의 쿼리를 사용하는 방법
* 먼저 한 테이블을 조회합니다.   
* 조회한 결과에서 외래키 값을 가져와서 다른 테이블을 조회합니다.   

[맨위로](#Mybatis)

## 지연 로딩
Mybatis는 지연로딩만 지원합니다.   
* 일대일, 일대다 조회만 해당 됩니다.   

Mybatis config 파일에서 lazyLoadingEnabled = true | false 를 통해 지연 로딩을 할지 말지 구성할 수 있습니다.   

### 구현 원리
CGLIB(Code Generator Library)를 사용하여 대상 객체의 프록시 객체를 생성합니다.   
메소드를 호출할 때 a.getB().getName()과 같은 메서드를 호출하면 인터셉터 invoke()메서드가 a.getB()가 null 값임을 알게 됩니다.   
그 다음 이전에 저장된 B객체와 연관된 SQL쿼리가 별도로 전송되며, 쿼리가 실행된 다음 a.setB(b)가 호출되어 a에 B객체가 로딩되게 됩니다.    

[맨위로](#Mybatis)

## primiary 및 secondary 캐시
* primary 캐시
  * HashMap 로컬 캐시입니다.
  * 저장 범위는 세션입니다.   
  * 세션을 flush 하거나 close 하면 모든 캐시가 지워지고 primary 캐시가 디폴트로 사용됩니다.   

* secondary 캐시
  * 매커니즘은 primary 캐시와 동일합니다.
  * 저장 범위는 Mapper(namespace)입니다.
  * 저장 소스를 사용자 정의할 수 있다는 점만 제외하고 기본값은 PerpetualCache, HashMap 스토리지 입니다.   
  * secondary 캐시는 디폴트가 아닙니다.   
  * secondary 캐시를 활성화하려면 secondary 캐시 속성 클래스가 Serializable 인터페이스를 구현해야 합니다.
  * 매핑 파일에 \<cache/>로 구성할 수 있다.

캐시 데이터 업데이트 메커니즘의 경우,   
C/U/D 작업이 session 또는 namepsace 범위에서 수행되면 모든 캐시가 지워집니다.   

[맨위로](#Mybatis)

## 인터페이스 바인딩
인터페이스 매핑은 Mybatis에서 인터페이스를 임의로 정의한 다음 인터페이스 내부의 메서드를 SQL 문에 바인딩하는 것입니다.   

인터페이스 메서드를 직접 호출할 수 있으므로 원래 SqlSession 메서드보다 더 유연한 옵션과 설정을 사용할 수 있다.   

### 구현 방식
두 가지 방법이 있습니다.   
* 어노테이션 바인딩
  * 바인딩할 SQL문을 포함하는 인터페이스 메서드에 \@Select, \@Update 및 기타 애노테이션을 추가하는 것입니다.   

* xml을 통한 SQL 작성
  * xml 매핑 파일의 namespace를 인터페이스의 전체 경로로 설정해야 합니다.  
  
[맨위로](#Mybatis)

## 어노테이션 바인딩과 xml 바인딩
SQL문이 비교적 간단한 경우 어노테이션 바인딩을 사용하고   
SQL문이 더 복잡한 경우 일반적으로 xml 바인딩을 사용합니다.   

[맨위로](#Mybatis)

## Mapper 인터페이스 정의하는 방법
* Mapper 인터페이스 메서드 이름은 xml에 정의된 각 SQL의 ID와 동일해야 합니다.
* Mapper 인터페이스 메서드의 파라미터 타입은 xml에 정의된 SQL의 파라미터 타입과 동일해야 합니다.   
* Mapper 인터페이스 메서드의 리턴 타입은 xml에 정의된 SQL의 리턴 타입과 동일해야 합니다.
* xml 파일의 namepsace는 Mapper 인터페이스 클래스의 경로와 동일해야 합니다.   

[맨위로](#Mybatis)

## iBatis 및 MyBatis의 핵심 처리 클래스
iBatis의 핵심 처리 클래스는 SqlMapClient입니다.   
MyBatis의 핵심 처리 클래스는 SQLSession입니다.   

[맨위로](#Mybatis)

## iBatis와 MyBatis의 차이점 및 개선된 점
* SQL에서 변수 이름이 #variable#에서 #{variable}로 변경되었습니다.   
* SQL에서 변수 이름이 $variable$에서 ${variable}로 변경되었습니다.
* queryForObject와 queryForList가 selectOne과 selectList로 변경되었습니다.
* 인터페이스 바인딩
  * 어노테이션 바인딩
  * xml 바인딩
* 동적 SQL이 기본 node 구성에서 OGNL 표현식으로 변경되었습니다.   
* 일대일, 일대다 연관 관계가 resultMap의 association과 collection을 통해 구현됩니다.  

[맨위로](#Mybatis)

## 참고
* [Mybatis three common interview questions](https://www.programmersought.com/article/8568335616/)

[맨위로](#Mybatis)