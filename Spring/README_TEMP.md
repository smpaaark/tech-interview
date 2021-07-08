# Spring
* [데이터베이스 트랜잭션이란 무엇입니까?](#데이터베이스-트랜잭션이란-무엇입니까)
* [애플리케이션 트랜잭션이란 무엇입니까?](#애플리케이션-트랜잭션이란-무엇입니까)
* [Transaction Management란 무엇입니까?](#transaction-management란-무엇입니까)
* [Spring Boot에서 Transaction Management를 구현하는 방법은 무엇입니까?](#spring-boot에서-transaction-management를-구현하는-방법은-무엇입니까)
* [Transaction Propagation(전파) 유형](#transaction-propagation전파-유형)
* [Checked Exception에 대한 트랜잭션 처리 방법은 무엇입니까?](#checked-exception에-대한-트랜잭션-처리-방법은-무엇입니까)
* [Transaction Isolation Level이란 무엇입니까?](#transaction-isolation-level-유형)
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## 데이터베이스 트랜잭션이란 무엇입니까?
데이터베이스 내용에 접근하고 수정할 수 있는 단일 논리적 작업 단위입니다.   
하나의 논리적 기능을 수행하는데 실행되어야 하는 쿼리 시퀀스라고 할 수 있습니다.   

![1](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/1.PNG)

[맨위로](#spring)

## 애플리케이션 트랜잭션이란 무엇입니까?
애플리케이션에 의해 단일 논리 단위로 간주되는 작업입니다.     
* 예시
  * 조직에 가입하는 기능이 있을 때 직원 정보 등록과 건강보험 정보를 등록하는 과정을 하나의 트랜잭션으로 간주합니다.   

![2](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/2.PNG)

[맨위로](#spring)

## Transaction Management란 무엇입니까?
Transaction Manager는 하나 이상의 리소스에 대한 트랜잭션을 제어하는 애플리케이션의 일부입니다.   
Transaction Manager는 트랜잭션 객체를 생성하고 해당 객체의 내구성과 원자성을 관리할 책임이 있습니다.   

[맨위로](#spring)

## Spring Boot에서 Transaction Management를 구현하는 방법은 무엇입니까?
@Transactional 애노테이션을 사용하여 트랜잭션 관리를 구현합니다.   
스프링 부트에서 트랜잭션은 AOP를 사용하여 구현됩니다.   

![3](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/3.PNG)
```
package com.javainuse.service.impl;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

import com.javainuse.model.Employee;
import com.javainuse.model.EmployeeHealthInsurance;
import com.javainuse.service.EmployeeService;
import com.javainuse.service.HealthInsuranceService;
import com.javainuse.service.OrganizationService;

@Service
public class OrganzationServiceImpl implements OrganizationService {

	@Autowired
	EmployeeService employeeService;

	@Autowired
	HealthInsuranceService healthInsuranceService;

	@Override
	@Transactional
	public void joinOrganization(Employee employee, EmployeeHealthInsurance employeeHealthInsurance) {
		employeeService.insertEmployee(employee);
		if (employee.getEmpId().equals("emp1")) {
			throw new RuntimeException("thowing exception to test transaction rollback");
		}
		healthInsuranceService.registerEmployeeHealthInsurance(employeeHealthInsurance);
	}

	@Override
	@Transactional
	public void leaveOrganization(Employee employee, EmployeeHealthInsurance employeeHealthInsurance) {
		employeeService.deleteEmployeeById(employee.getEmpId());
		healthInsuranceService.deleteEmployeeHealthInsuranceById(employeeHealthInsurance.getEmpId());
	}
}
```
Spring Boot는 @Transactional이 붙은 메서드에 대한 프록시를 생성합니다.   
프록시는 메서드 호출을 시작할 때 트랜잭션을 생성하고 메서드가 실행된 이후에 트랜잭션을 커밋하는 Wrapper처럼 작동합니다.   

![4](https://raw.githubusercontent.com/smpark1020/tech-interview/master/Spring/4.PNG)   
EmployeeService와 같이 @Transactional이 붙은 메서드를 인터셉트하는 컴포넌트입니다.   

[맨위로](#spring)

## Transaction Propagation(전파) 유형
Spring Boot용 Transaction Propagation 유형은 아래와 같습니다.   
* REQUIRED 
* SUPPORTS
* NOT_SUPPORTED
* REQUIRES_NEW
* NEVER
* MANDATORY

[맨위로](#spring)

## Checked Exception에 대한 트랜잭션 처리 방법은 무엇입니까?
Checked Exception에 대한 롤백을 수행하려면 rollbackFor를 사용하여 롤백을 지정해야 합니다.   

[맨위로](#spring)

## Transaction Isolation Level 유형
* READ_UNCOMMITTED 
* READ_COMMITTED
* REPEATABLE_READ
* SERIALIZABLE
* DEFAULT

[맨위로](#spring)

## 참고
* [Spring Transaction Management Interview Questions](https://www.javainuse.com/spring/transaction-interview)

[맨위로](#spring)
