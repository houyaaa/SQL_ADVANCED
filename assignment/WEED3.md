# SQL_ADVANCED 3주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=1YmWy-7-OhQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=10
https://www.youtube.com/watch?v=tuQFkzjqEGw&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=11
https://www.youtube.com/watch?v=IOCsreDYqFE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=12
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_3rd_TIL

### 4장 SQL 고급 문법
#### 01. MySQL의 데이터 형식
#### 02. 두 테이블을 묶는 조인
#### 03. SQL 프로그래밍 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. MySQL의 데이터 형식

### 데이터 형식

#### 1. 정수형
- 소수점이 없는 숫자
- 크기와 범위

| 데이터 형식 | 바이트 수 | 숫자 범위 |
|------------|----------|-----------|
| TINYINT    | 1        | -128 ~ 127 |
| SMALLINT   | 2        | -32,768 ~ 32,767 |
| INT        | 4        | 약 -21억 ~ +21억 |
| BIGINT     | 8        | 약 -900경 ~ +900경 |


- **UNDESIGNED**: 값의 범위가 0부터 시작

<img width="626" height="246" alt="image" src="https://github.com/user-attachments/assets/c0172a9d-90ee-4dbf-be4a-67457ba83161" />

- 0부터 시작하는 만큼 줄어든 범위가 그 뒤에 덧붙여짐

✨추가학습: 효율(성능+저장공간+구조)의 이유로 적절한 데이터 형식을 고르는 것이 필수적




<br>
<br>





#### 2. 문자형

- 글자 저장
- 입력할 최대 글자의 개수 지정

| 데이터 형식 | 바이트 수 | 
|------------|----------|
| CHAR(개수)    | 1 ~ 255        | 
| VARCHAR(개수)   | 1 ~ 16383       |  


- CHAR(N): N자리보다 적은 수의 글자를 적더라도 N자리를 모두 확보
- VARCHAR(N): N자리보다 적은 수의 글자를 적으면 글자 수 만큼만 사용

<br>

- 공간 효율: CHAR < VARCHAR
- 성능(빠른 속도): CHAR > VARCHAR



✔ 글자길이가 다양한 컬럼 -> VARCHAR 

✔ 숫자로서의 의미
  ▸ 사칙연산
  ▸ 순서 의미

  ex) 전화번호 -> 글자로 취급

<br>


#### 3. 대량의 데이터 형식

- 더 큰 데이터를 저장하기 위해서 

<img width="709" height="179" alt="image" src="https://github.com/user-attachments/assets/0ddd2064-a0e3-4d43-88c9-6835ed22ae88" />


- TEXT: 65,535자
- LONGTEXT: 42억자

- BLOB: Binary Long Object
  - 글자x, 이미지 동영상 데이터

✨ 추가학습: BLOB는 링크로 저장되어있는 것인가?
-> NOPE, 이미지 파일, 동영상 파일이 그대로 들어가 있음
-> 따라서 실무에서는 자주 쓰이지 않음 (DB가 무거워짐, 성능이 떨어짐)

<br>

#### 4. 실수형

| 데이터 형식 | 바이트 수 | 설명 |
|------------|----------|------|
| FLOAT      | 4        | 소수점 아래 7자리까지 표현 |
| DOUBLE     | 8        | 소수점 아래 15자리까지 표현 |



#### 5. 날짜형

| 데이터 형식 | 바이트 수 | 설명 |
|------------|----------|------|
| DATE       | 3        | 날짜만 저장, YYYY-MM-DD 형식 |
| TIME       | 3        | 시간만 저장, HH:MM:SS 형식 |
| DATETIME   | 8        | 날짜 및 시간 저장, YYYY-MM-DD HH:MM:SS 형식 |


- DATE는 날짜만
- TIME은 시간만
- DATETIME은 둘 다 

<br>
<br>

### 변수의 사용

```
SET @변수이름 = 변수의 값;
SELECT @변수이름;
```

- 변수의 선언 및 값 대입
- 변수의 값 출력


#### PREPARE, EXECUTE
```
SET @CNT = 3;
PREPARE mySQL FROM 'SELECT mem_name, height FROM member ORDER BY height LIMIT?';
EXECUTE mySQL USING @CNT;
```

- @CNT = N 에 무엇을 적는지에 따라 상위 N개가 출력됨

<br>

### 데이터 형 변환
- 형 변환: 정수형 <-> 문자형
    - 명시적인 변환: 직접 함수 사용
    - 암시적인 변환: 자연스럽게 
 
#### 1. 함수를 이용한 명시적 변환
- CAST()
- CONVERT()

```
CAST( 값 AS 데이터_형식 [(길이)])
CONVERT( 값, 데이터_형식 [(길이)])
```

EX)
```
SELECT CAST(AVG(price) AS SIGNED) '평균 가격' FROM buy;
```

- SIGNED: 부호가 있는 정수
- UNSIGNED: 부호가 없는 정수

```
SELECT
  num,
  CONCAT(CAST(price AS CHAR), 'X', CAST(amount AS CHAR),'=') '가격X수량',
  price*amount '구매액'
FROM buy
```

- CONCAT(): 문자를 이어주는 역할


#### 2. 암시적인 변환 

```
SELECT '100'+'200';
```
>>> 300
>>> 자동으로 숫자 100, 200으로 변환됨

```
SELECT CONCAT('100','200');
```
>>> 100200


```
SELECT CONCAT(100,'200');
SELECT 100+'200';
```
>>> 100200
>>> CONCAT -> 숫자 100이 문자 '100'으로 변환되어 연결
>>> 300
>>> CONCAT X -> 200이 숫자로 변환 
  


<br>
<br>
<br>
<br>
<br>
<br>


<!-- MySQL의 데이터 형식에 관해 배우게 된 점을 적어주세요. -->

> **확인문제: 다음 보기에서 데이터 형식의 변환에 사용되는 함수를 2개 고르세요.**

보기는 아래와 같습니다.
```
CONVERT() / DATA() / CAST() / MOVE() / TYPE() / SUM() / AVG() / CURRENT_DATE()
```

```
CONVERT()
CAST()
```


## 2. 두 테이블을 묶는 조인

<!-- 두 테이블을 묶는 조인에 관해 배우게 된 점을 적어주세요. -->


### 내부 조인

#### 1. 일대다 관계의 이해 
- 두 테이블의 조인을 위해서는 테이블이 일대다 관계로 연결되어야 함
- 회원 테이블의 아이디, 구매 테이블의 아이디 -> 일대다 관계
- 일대다 관계: 한쪽 테이블에는 하나의 값만 존재해야하지만, 연결된 다른 테이블에는 여러 개의 값이 존재할 수 있는 관계

EX) 
회원 테이블 -> 블랙핑크의 아이디 'BLK' -> 1명 => 기본 키 

구매 테이블 -> 3개의 BLK 존재 

회원은 한 명, 이 회원은 구매를 여러 번 할 수 있다 -> 일대다 관계
<br>

구매 테이블의 아이디 => FK


<br>
<br>

#### 2. 내부 조인의 기본
```
SELECT <열 목록>
FROM <첫 번째 테이블>
  INNER JOIN <두 번째 테이블>
  ON <조인될 조건>
[WHERE 검색 조건]
```
교집합


#### 3. 내부 조인의 간결한 표현 
- 테이블_이름.열_이름 형식으로 작성
- 테이블의 이름 뒤에 별칭 부여


#### 4. 내부 조인의 활용
- 회원 아이디와 구매 아이디를 키로 조인을 할 경우
- 자동적으로 구매한 이력이 있는 아이디만 결과로 출력


<br>
<br>

### 중복된 결과 1개만 출력하기 
```
SELECT DISTINCT M.mem_id, M.mem_name, M.addr
FROM buy B
INNER JOIN member M
ON B.mem_id = M.mem_id
ORDER BY M.mem_id
```
 
구매한 이력이 있는 회원을 중복없이 출력

### 외부 조인
한쪽에만 데이터가 있어도 결과가 나옴


#### 1. 외부 조인의 기본

```
SELECT <열 목록>
FROM <첫 번째 테이블(LEFT 테이블)>
  <LEFT|RIGHT|FULL> OUTER JOIN <두 번째 테이블(RIGHT)>
  ON <조인될 조건>
[WHERE 검색 조건]
```

#### 2. 외부 조인의 활용
- FULL OUTER JOIN = LEFT + RIGHT JOIN


### 기타 조인 

#### 1. 상호조인 
- CROSS JOIN
- 한쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인
- 전체 행 개수 = 두 테이블의 각 행의 개수를 곱한 개수

**<상호 조인의 특징>**
1. ON 구문 사용X
2. 결과 내용 의미X (랜덤으로 조인)
3. 주 용도는 테스트를 위한 대용량 데이터 생성

<br>

#### 2. 자체 조인
- SELF JOIN
- 자신이 자신과 INNER 조인
- 서로 다른 별칭을 붙임 
```
SELECT <열 목록>
FROM <테이블> 별칭 A
  INNER JOIN <테이블> 별칭 B
  ON <조인될 조건>
[WHERE 검색 조건]
```
EX) 직원의 직속상관의 연락처를 표기하는 쿼리
```
SELECT A.emp "직원", B.emp "직속상관", B.phone "직속상관연락처"
FROM emp_table A
INNER JOIN emp_table B
ON A.manager = B.emp
```



<br>
<br>
<br>
<br>
<br>
<br>

> **확인문제: 다음 SQL은 회원으로 가입만 하고, 한 번도 구매한 적이 없는 회원의 목록을 조회하는 쿼리입니다. 빈칸에 들어갈 가장 적절한 구문을 고르세요..**

```sql
SELECT DISTINCT M.mem_id, B.prod_name, M.mem_name, M.addr
  FROM member M
    LEFT OUTER JOIN buy B
    ON M.mem_id = B.mem_id
  __________
  ORDER BY M.mem_id;
```
보기는 아래와 같습니다.
```
1. JOIN B.prod_name IS NULL
2. LIMIT B.prod_name IS NULL
3. HAVING B.prod_name IS NULL
4. WHERE B.prod_name IS NULL
```
```
4. WHERE B.prod_name IS NULL

조건절에 해당하므로 3,4 중 하나임
BUT HAVING은 GROUP BY 와 함께 쓰임
따라서 답은 4

```

## 3. SQL 프로그래밍 

<!-- IF문, CASE문, WHILE문, 동적 SQL에 관해 배우게 된 점을 적어주세요. -->

> **확인문제: 다음은 CASE 문의 형식입니다. 빈칸에 들어갈 가장 적절한 명령어를 보기에서 고르세요..**

```sql
CASE
    (1) 조건 THEN
        SQL문장들1
    ELSE
        SQL문장들4
END (2);
```

보기는 아래와 같습니다.
```
WHEN / THEN / CURRENT / DATE / TIME / IF / END IF / CASE
```

```
여기에 답을 적어주세요!
(1)
(2) 
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week3_db;

-- 2. 사용할 데이터베이스 선택
USE week3_db;

-- 3. 기존 테이블 삭제 (초기화용)
DROP TABLE IF EXISTS orders;
DROP TABLE IF EXISTS customers;

-- 4. 테이블 생성 (조인 실습용)
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(20),
    signup_date_str VARCHAR(8) 
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,           
    order_date_str VARCHAR(8), 
    amount_str VARCHAR(10)     
);

-- 5. 데이터 삽입
INSERT INTO customers VALUES
(1, '진아', '20240218'),
(2, '혜인', '20230302'),
(3, '규서', '20220315'),
(4, '규영', '20210401'),
(5, '철원', '20230909'),
(6, '예운', '20240201'),
(7, '민서', '20220320'),
(8, '광윤', '20240105'); -- 주문 없는 고객(외부 조인용)

INSERT INTO orders VALUES
(101, 1, '20240220', '12000'),
(102, 1, '20240303', '30000'),
(103, 2, '20240111', '15000'),
(104, 3, '20221201', '9000'),
(105, 5, '20231111', '20000'),
(106, 7, '20220707', '5000'),
(107, 99, '20240210', '7000'); -- 고객 테이블에 없는 customer_id (외부 조인용)
```

## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.

1. **데이터 형식 변환**
   - orders 테이블의 `order_date_str`을 DATE 형식으로 변환하여 조회하시오.
   (힌트: STR_TO_DATE 사용)

2. **데이터 형식 변환**
   - orders 테이블의 `amount_str`을 숫자형으로 변환하여 조회하시오.

3. **내부 조인 (INNER JOIN)**
   - customers와 orders를 customer_id 기준으로 내부 조인하여
     고객 이름(name)과 주문 번호(order_id)를 함께 조회하시오.

4. **외부 조인 (LEFT JOIN)**
   - customers를 기준으로 LEFT JOIN을 수행하여,
     주문이 없는 고객도 함께 조회하시오.

5. **스토어드 프로시저 (IF문 사용)**
   - 입력받은 금액이 10000 이상이면 '고액 주문',
     그렇지 않으면 '일반 주문'을 출력하는
     프로시저를 생성하시오.
   - 생성 후 CALL로 실행 결과를 확인하시오.


<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->


### 🎉 수고하셨습니다.






