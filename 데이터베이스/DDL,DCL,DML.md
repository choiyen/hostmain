### 데이터 정의어(Data Definition Language)
- 데이터를 정의하는 언어로 데이터를 담는 그릇을 정의함
- 테이블과 같은 데이터 구조를 결정하는 명령어로 생성, 삭제, 이름 바꾸는 데이터 구조와 관련된 명령어를 말함
- 대표적인 것들론 생성을 담당하는 CREATE, 수정을 담당하는 ALTER, 삭제를 담당하는 DROP, TRUNCATE가 있다.

### CREATE TABLE
1. 테이블을 생성하는 명령어
2. 하나의 칼럼에 대해 칼럼명 데이터 타입 제약 조건의 순서로 구성됨

#### 사용방법
CREATE TABLE 사원
{
  사번 VARCHAR(10) PRIMARY KEY,
  업무 VARCHAR(20) FOREIGN KEY REFEFENCES 부서(부서코드),
  이름 VARCHAR(10) UNIQUE,
  생년월일 CHAR(8) NOT NULL,
  성별 CHAR(1) CHECK(성별 = 'M' OR 성별 = 'F'),
  입사일 DATA DEFAULT SYSDATE -- SYSDATE는 현재시간/날짜

};

### CREATE의 대표적 제약 조건
- PRIMARY KEY : 테이블의 기본 키를 정의, 유일하게 테이블의 각 행을 식별
- FOREIGN KEY : 외래 키, 열과 참조된 테이블의 외래키 관계를 정의
- UNIGUE : 유일값을 갖게 하는 제약조건, 즉 값이 중복될 수 없음
- NOT NULL :  값이 비어있을 수 없다는 의미
- DEFAULT : 데이터를 삽입할 때 해당 값을 넣지 않은 경우 자동으로 값을 지정해주는 것
- CHECK : 들어갈 수 있는 값을 정의함

### ALTER TABLE
- 테이블을 수정하는 명령어임
- ALTER TABLE 테이블명  ADD 칼럼명 데이터 타입[제약조건];
- 단, 제약조건의 변경의 경우, CREATE 당시에 제약 조건을 명시해야 수정 가능함
- ADD 대신에 DROP을 넣으면 해당 칼럼만 삭제 시킬 수 있음

### DROP TABLE
- 테이블을 삭제하는 명령어
- DROP TABLE 테이블명 [CASCADE || RESTRICT];
- CASCADE 는 참조 테이블까지, RESTRICT는 참조 테이블이 존재하면 삭제가 기능할 수 없게 하는 것.

### TRUNCATE TABLE [테이블 명]
- 테이블 내의 모든 데이터를 지우는 것

### CRATE VIEW
- 뷰를 생성하는 명령어
- CRATE VIEW 뷰명칭 AS 조회쿼리;
- 조회 쿼리에는 주로 SELECT문이 들어감
- 따로 뷰명칭을 지정하지 않을 경우, SELECT 문의 칼럼명이 들어감
- 단, SElECT 문에는 UNION이나 OREDER BY 절을 사용할 수 없음

### CREATE OR PERLACT VIEW
- 만약 동일한 이름의 뷰가 있을 경우, 그 뷰를 없애고 등록.

### DROP VIEW
- 뷰를 삭제하는 것을 의미한다.

### INDEX 관련 DDL
- CREATE [UNIQUE] INDEX 인덱스명 ON 테이블명(칼럼명1,칼럼명2, 칼럼명3, ....);
- 인덱스를 생성하는 명령어로, UNIQUE는 생략 가능하고, 인덱스 걸림 칼럼에 대해 중복값은 허용안됨. 프라이머리 키랑 다른 점은 복수 칼럼이 가능하다는 것
- ALTER INDEX [UNIQUE] INDEX 인덱스명 ON 테이블명(칼럼명1,칼럼명2, 칼럼명3, ....);
- 인덱스를 수정하는 명령어로, 일부 DBMS에선 지원하지 않음. VIEW 처럼 그냥 없애버리고, 새로 지정하는 게 안전하기 때문이다
- DROP INDEX 인덱스명;
- 해당 인덱스 명을 가진 녀석을 제거하는 걸 말함




