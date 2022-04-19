### 데이터 정의어(Data Definition Language)
- 데이터를 정의하는 언어로 데이터를 담는 그릇을 정의함
- 테이블과 같은 데이터 구조를 결정하는 명령어로 생성, 삭제, 이름 바꾸는 데이터 구조와 관련된 명령어를 말함
- 대표적인 것들론 생성을 담당하는 CREATE, 수정을 담당하는 ALTER, 삭제를 담당하는 DROP, TRUNCATE가 있다.

### CREATE TABLE
1. 테이블을 생성하는 명령어
2. 하나의 칼럼에 대해 칼럼명 데이터 타입 제약 조건의 순서로 구성됨

#### 사용방법

<pre>
<code>
CREATE TABLE 사원
{
  사번 VARCHAR(10) PRIMARY KEY,
  업무 VARCHAR(20) FOREIGN KEY REFEFENCES 부서(부서코드),
  이름 VARCHAR(10) UNIQUE,
  생년월일 CHAR(8) NOT NULL,
  성별 CHAR(1) CHECK(성별 = 'M' OR 성별 = 'F'),
  입사일 DATA DEFAULT SYSDATE -- SYSDATE는 현재시간/날짜

};
</code>
</pre>

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

### 데이터 조작어(Data Manipulation Language)
- 데이터베이스에 저장된 자료를 입력, 수정, 삭제, 조회하는 명령어
1. SELECT 명령어 개념
- 데이터를 조회할 때 사용하는 명령어
- SELECT절,  FROM절, WHERE 절, GROUP BY 절 HAVING 절, ORDER BY 절 등으로 그성 됨.

<pre>
<code>
SELECT [ALL | DISTINCT] 속성명 1, 속성 명2,,,,, 속성명 N 
FROM 테이블명,,.......
[WHERE 조건]
[GROUP BY 속성명,   ]
[HAVING 그룹조건]
[ORDER BY 속성 [ASC || DESC] ];
</code>
</pre>

### SELECT 명령어
- SELECT 절
1. 검색하고자 하는 속성명, 계산식을 기술
2. 속성명 별칭은 AS를 사용하여 생략 가능함
3. 2개 이상의 테이블을 대상으로 검색할 때는 '테이블명, 속성명'으로 표현함
4. 술어 부분은 ALL이 기본값
(참고사항 : ALL은 모든 튜플을 검색할때, DISTINCT는 중복된 속성 조회시 하나만 검색)

- FROM 절
1. 질의에 의해 검색될 데이터들을 포함하는 테이블 명을 기술

- WHERE 절
1.  검색 조건을 기술
2.  비교(=,<>,!=, <.....), 범위(BETWEEN AND), 집합(IN,NOT IN(포함되지 않은경우), 
    패턴(LIKE : % 0개이상문자 일치, [] 1개의 문자 일치, [^] 1개의 문자 불일치, _ 특정위치 문자 불일치), 복합조건(AND,OR, NOT, !)


- GROUP BY 절
1  어떤 속성을 그룹으로 분류하고자 할 때 사용

 - HAVING 절
1. GROUP BY  절에 의해 분류한 것들을 그룹에 대한 조건 지정

- ORDER BY 절
1. 속성값을 정렬하고자 할 때(ASC : 오름차순, DESC :내림차순, 기본값은 오름차순)


## 조인
두개 이상의 테이블을 연결하여 데이터를 검색하는 방법
내부 조인(inner Join) : 공통 존재 칼럼의 값이 같은 경우 추출하는 법
외부 조인<Outer Join) 
1. 왼쪽 외부 조인 : 왼쪽 테이블의 모든 데이터와 오른쪽 테이블의 동일 데이터를 추출함
2. 오른쪽 외부 조인 : 오른쪽 테이블의 모든 데이터와 왼쪽 테이블의 동일 데이터를 추출함
교차 조인(Cross Join) : 조인 조건이 없는 모든 데이터 조합을 추출하는 것
샐프 조인(Self Join) : 자신에게 별칭을 지정한 후 다시 좋인하는 방법

## 서브쿼리 
- 쿼리문 안에 또다른 쿼리를 넣어 정보를 찾는 것
- FORM 절 서브 쿼리 : FORM절 안에 서브 쿼리가 들어있는 형태로, 인라인 뷰라는 명칭으로 불림. 뷰처럼 결과가 동적으로 생성된 테이블 형태로 사용가능
- WHERE 절 서브 쿼리 : 중첩 서브 쿼리라고도 한다.


## 집합 연산자
집합 연산자는 테이블을 집합 개념으로 보고, 두 테이블 연산에 필요한 집합 연산자를 사용하는 방식
두개 절의 결과를 결합한느 방식을 위해 사용함
1. UNION : 중복 행이 제거된 쿼리를 반환하는 연산자
2. UNION ALL : 중복행을 제거하지 않은 체 반환
3. INTERSECT : 교집합
4. MINUS : 차집합


## INSERT 명령어
- 데이터의 내용을 삽입할 때 사용하는 명령어

<pre>
<code>
INSERT INTO 테이블명(속성명,....) VALUES (데이터1,    );
</code>
</pre>

1. 속성과 데이터 개수, 데이터 타입이 일치해야 함
2. 속성의 타입이 숫자인 경우, 데이터는 따옴표를 붙이지 않아도 되며, 아닌 경우는 따옴표를 붙여야 함


### UPDATE 명령어
- 데이터의 내용을 변경할 때 사용하는 명령어
- WHERE 절을 이용해 특정 조건이 만족할 때만 정보를 수정할 수 있는 형태로 주로 사용

<pre>
<code>
UPDATE 테이블명 SET 속성명 = 데이터, .... WHERE 조건;
</code>
</pre>

### DELETE 명령어 
- 데이터 내용을 삭제할 때 사용하는 명령어

<pre>
<code>
DELETE FROM 테이블명 WHERE 조건;
</code>
</pre>

###  데이터 제어어(DCL : Data Control Language)
- 데이터베이스 관리자가 보안, 무결성 유지, 병행 제어 회복을 위해 고나리자가 사용하는 제어용 언어
- 데이터 제어어의 유형에는 두가지가 있음

1. GRANT 권한부여
데이터베이스에 대한 여러 권한 들을 부여하는 명령어

<pre>
<code>
GRANT 권한 ON 테이블 TO 사용자;
GRANT UPDATE ON 학생 TO 유영태 : 유영태라는 사람한테, 데이터 업데이트 권한을 부여한다.
</code>
</pre>

2. REVOKE 권한 회수
데이터베이스에 대한 여러 권한을 다시 돌려받는 명령어

<pre>
<code>
REVOKE 권한 ON 테이블 FROM 사용자;
REVOKE UPDATE ON 학생 FROM 유영태 : 유영태라는 사람한테, 데이터 업데이트 권한을 부여한다.
</code>
</pre>



