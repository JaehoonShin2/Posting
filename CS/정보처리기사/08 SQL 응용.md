# 08. SQL 응용

### DML

Data Manipulation Language. 데이터 조작 언어

사용자가 저장된 데이터를 실질적으로 관리하는데 사용하는 언어.

- SELECT
- INSERT
- UPDATE
- DELETE

### DDL

Data Define Language. 데이터 정의 언어

DB 를 구축하거나 수정할 목적으로 사용하는 언어.

- CREATE
    
    
    **ON DELETE CASCADE**
    
    참조하고 있는 테이블도 함께 제거하는 명령어.
    
    **ON UPDATE CASCADE**
    
    참조하고 있는 테이블도 함께 업데이트하는 명령어.
    
    오라클에서는 해당 옵션을 지원하지 않기 때문에 트리거를 활용해야 한다.
    

- ALTER
- DROP

### DCL

Data Controll Language. 데이터 제어 언어

데이터의 보안, 무결성, 회복, 병행 제어 등을 정의하는데 사용하는 언어.

- COMMIT
- ROLLBACK
- GRANT
- REVOKE
- SAVEPOINT : 트랜잭션 내에 ROLLBACK 할 위치인 저장점을 지정하는 명령어

### 122. DML-SELECT-2

WINDOW 함수 : GROUP BY 절을 이용하지 않고 속성의 값을 집계할 함수를 기술.

- PARTTITION BY : WINDOW 함수의 적용 범위가 될 속성을 지정.
- ORDER BY : PARTTITION 안에서 정렬 기준으로 사용할 속성을 지정
- 종류
    - ROW_NUMBER() : 윈도우별로 각 레코드에 대한 일련번호를 반환
    - RANK() : 윈도우 별로 순위를 반환, 공동 순위를 반영
    - DENSE_RANK() : 윈도우별로 순위를 반환, 공동 순위를 무시하고 순위를 부여
    

### 123. JOIN

JOIN : 연관된 튜플들을 결합하여 하나의 새로운 릴레이션을 반환.

INNER JOIN

- EQUI JOIN(NATUAL JOIN)
- NON-EQUI JOIN

OUTER JOIN

- LEFT OUTER JOIN
- RIGHT OUTER JOIN
- FULL OUTER JOIN

### 124. 프로시저

프로시저 : SQL 를 사용해 작성한 일련의 작업을 저장해두고 호출을 통해 원할 때마다 저장한 작업을 수행하도록 하는 절차형 SQL

프로시저의 구성도

```sql
DECLARE (필수)
BEGIN (필수)
	CONTROL
	SQL
	EXCEPTION
	TRANSACTION
END (필수)
```

- DECLARE : 프로시저의 명칭, 면수, 인수, 데이터 타입을 정의하는 선언부
- BEGIN / END : 프로시저의 시작과 종료를 의미
- CONTROL : 조건문 또는 반복문이 삽입되어 순차적으로 처리
- SQL : DML, DDL, DCL 이 삽입되어 데이터 관리를 위한 조회, 추가, 수정, 삭제 작업이 수행된다.
- EXCEPTION : BEGIN~END 안의 구문 실행 시 예외가 발생하면 이를 처리하는 방법을 정의
- TRANSACTION : 수행된 데이터 작업들을 DB 에 적용할지 취소할 지를 결정하는 처리부

### 125. 트리커

트리거 : 이벤트(삽입, 갱신, 삭제 등) 가 발생할 때 관련 작업이 자동적으로 수행되게 하는 절차형 SQL

### 129. DBMS 접속

- JDBC
- ODBC
- MYBATIS

DYNAMIC SQL : SQL 구문을 동적으로 변경하여 처리할 수 있는 SQL 처리 방식

### 132. 쿼리 성능 최적화

옵티마이저 : 작성된 SQL 이 가장 효율적으로 수행되도록 최적의 경로를 찾아 주는 모듈