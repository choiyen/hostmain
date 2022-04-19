### 절차형 SQL 개념
= 일반적인 개발 언어처럼 SQL 언어에서도 절차 지향적 프로그램이 가능하도록 하는 트랜잭션 언어
- 절차형 SQL의 종류는 다음과 같다.
1. 프로시저(Procedure) : 일련의 퀴리 들을 마치 하나의 함수처럼 실행하기 위한 퀴리의 집합
2. 사용자 정의 함수(User Defined Function) : 일련의 SQL처리를 수행하고 수행 결과를 단일값으로 반환하는 절차형 SQL
3  트리거(Trigger) : 데이터베이스 시스템에서 삽입, 갱신, 삭제 등의 이벤트가 발생할 때마다 관련 작업이 자동으로 수행되는 SQL
- 출력부
1. DBMS_OUTPUT 패키지 개념
- 메시지를 버퍼에 저장하고 버퍼로부터 메시지를 읽어오기 위한 인터페이스 패키지
- 절차형 SQL이 정상적으로 동작하는 지를 테스트하는 목적으로 활용되는 것이며, 대표적으로 다음과 같다.
- DBMS_OUTPUT.PUT(문자열) : 개행 없이 문자열을 출력하는 프로시저, 
- DBMS_OUTPUT.PUT_LINE(문자열) : 문자열을 출력 후 개행하는 프로시져

### 조건문 IF문
- 프로그래밍에 사용하는 참인지, 거짓인지 사용하는 그 IF와 동일함
<pre>
<code>
IF 조건 THEN 문장;
ELSIF 조건 THEN  문장;
ELSE 문장;
END IF;
</code>
</pre>

### 간단한 케이스 문(SIMPLE CASE Expression)
간단한 케이스 문은 명확한 값을 가지는 조건에 따라 여러 개의 선택 중 하나를 취하고자 할 때 사용하는 조건문
범위 같은 더 복잡한 매칭을 수행하려면 겁색된 CASE 문을 사용해야 한다.

<pre>
<code>
CASE 변수 
WHEN 값1 THEN SET 명령어;
WHEN 값1 THEN SET 명령어;
WHEN 값1 THEN SET 명령어;
WHEN 값1 THEN SET 명령어;
ELSE SET  명령어;
END CASE;
</code>
</pre>

### 검색된 케이스문(Searched Case Expression)
- 검색된 케이스 문은 명확한 값 및 범위를 가지는 조건에 따라 여러 개의 선택 경로 중 하나를 취하고자 할 때 사용하는 조건문

<pre>
<code>
CASE 
WHEN 값1 THEN SET 명령어;
WHEN 값1 THEN SET 명령어;
WHEN 값1 THEN SET 명령어;
WHEN 값1 THEN SET 명령어;
ELSE SET  명령어;
END CASE;
</code>
</pre>

### 반복문
- LOOP 문은 특정 조건이 만족될 때까지 반복해서 문자를 실행하는 것.
<pre>
<code>
LOOP 문장;
EXT WHEN 탈출 조건;
END LOOP;
</code>
</pre>

- WHILE 문
시작과 종료 조건을 지정하여, 참인 동안에는 해당 문장을 반복해서 실행하는 명령어
조건이 참인 경우 반복하고, 조건이 거짓이거나 EXIT WHEN 조건이 만족하는 경우, 반복문을 빠져나온다.

<pre>
<code>
WHILE 반복조건 LOOP 문장;
EXT WHEN 탈출 조건;
END LOOP;
</code>
</pre>

- FOR LOOP 문
시작 값과 끝값을 지정하여 해당 값이 그 구간 내에 있을 때 반복하는 반복문.

<pre>
<code>
FOR 인덱스 IN 시작값 .. 종료값
LOOP 문장;
END LOOP;
</code>
</pre>

### 예외부
예외부는 실행 중 발생가능한 예외 사항을 수행하는 부분이다.
<pre>
<code>
EXCEPTION WHEN 조건 THEN SET 명령어;
</code>
</pre>

### 프로시저의 개념
일련의 퀴리들을 마치 하나의 함수처럼 실행하기 위한 쿼리의 집합

#### 프로시저의 구성
선언부(DECLARE) : 프로시저의 명칭, 변수와 인수 그리고 그에 대한 데이터 타입을 정의하는 부분
시작/종료부(BEGIN/END) : 프로시저의 시작과 종료를 표현하며 둘다 있어야 함. 다수 실행을 제어하는 기본적 단위가 되며, 논리적 프로세스를 구성함
제어부(CONTROL) : 기본적으로 순차적으로 처리되며, 조건문과 반복문을 이용하며 문장처리
SQL : DML을 주로 사용하며 자주 사용되지 않지만  DLL 중 TRUNCATE 사용
예외부 : 시작 종료부에서 실행되는 SQL문이 실행 될때 예외 발생 시 처리 방법을 정의하는 부
실행부 : 프로시저에서 수행된  DML 수행 내역의 DBMS 적용 또는 취소 여부를 결정하는 처리부







