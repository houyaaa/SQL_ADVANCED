# SQL_ADVANCED 2주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=_JURyg_KzHE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=7
https://www.youtube.com/watch?v=6qkPy7RfLqQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=8
https://www.youtube.com/watch?v=WWAFAm9op2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=9
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_2nd_TIL

### 3장 SQL 기본 문법
#### 01. 기본 중에 기본 SELECT ~ FROM ~ WHERE
#### 02. 좀 더 깊게 알아보는 SELECT문
#### 03. 데이터 변경을 위한 SQL문


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 기본 중에 기본 SELECT ~ FROM ~ WHERE

## 데이터베이스 만들기
```sql
DROP DATABASE IF EXISTS market_db;
CREATE DATABASE market_db;
```
1. **`DROP DATABASE`**: 데이터베이스를 삭제하는 문장
2. **`CREATE DATABASE`**: 데이터베이스를 새로 생성하는 문장

---

## 테이블 만들기
1. **`USE`**: 데이터 베이스를 선택하는 문장. `[SCHEMAS]` 패널에서 데이터베이스를 더블클릭하는 것과 동일한 효과
2. **`VARCHAR`**: `CHAR`와 동일하게 문자를 입력하는 것 (가변 길이)
3. **`AUTO_INCREMENT`**: 자동으로 숫자를 1씩 증가시켜 입력
4. **`FK` (FOREIGN KEY)**: 외래 키. 테이블 간의 관계를 연결

---

## 데이터 입력하기
1. **`INSERT`**: 테이블에 데이터를 삽입하는 문장
2. **입력 규칙**: `CHAR`, `VARCHAR`, `DATE`형 -> 양옆에 작은따옴표(`' '`) 사용 / `INT`형 -> 작은따옴표 생략
3. **`AUTO_INCREMENT`**: 자동입력이므로 해당 자리에는 `NULL` 입력

---

## 데이터 조회하기
- **`SELECT`**

### 1. USE
```sql
USE 데이터베이스_이름;
```
다른 DB를 사용하겠다고 명시하지 않으면 계속 해당 데이터베이스에서 쿼리 수행

### 2. SELECT 문의 기본 형식
```sql
SELECT 열_이름
    FROM 테이블_이름
    WHERE 조건식
    GROUP BY 열_이름
    HAVING 조건식
    ORDER BY 열_이름
    LIMIT 숫자;
```

### 3. SELECT / FROM
```sql
USE market_db;
SELECT * FROM market_db.member;
```
- 데이터베이스 이름 생략 -> `USE`문으로 지정해 놓은 DB 자동 선택
- 원칙적으로 `데이터베이스_이름.테이블_이름` 형식을 사용

### 4. 별칭 (ALIAS)
조회되는 열 이름에 별칭 지정을 해줄 수 있음 (예: `AS 별칭`)

### 5. 서브쿼리 (Subquery)
`SELECT` 안에 또 다른 `SELECT`가 들어가는 형태
```sql
SELECT mem_name, height FROM member
    WHERE height > (SELECT height FROM member WHERE mem_name = '에이핑크');
```
- 주로 `WHERE` 절 안에 서브쿼리가 들어가 조건의 기준으로 사용됨
- 🚨 **(중요) `GROUP BY` 절에는 서브쿼리가 들어갈 수 없음**


  

<!-- 이번 챕터에서 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 3~4장 제출해 주세요. -->

<img width="1833" height="927" alt="image" src="https://github.com/user-attachments/assets/9b92a248-4d07-4211-9ef6-b36b708231ab" />

<img width="946" height="652" alt="image" src="https://github.com/user-attachments/assets/729148ab-325b-4793-a0f1-c93e5a83c130" />

<img width="1294" height="763" alt="image" src="https://github.com/user-attachments/assets/866bd3df-3270-4217-b191-20cf198de610" />


> **확인문제: 다음 SQL문의 빈칸에 들어갈 WHERE절의 문법으로 틀린 것을 고르세요.**

```sql
SELECT *
FROM table_name
WHERE ________;
```

보기는 아래와 같습니다.
```
1. mem_number == 4
2. mem_number >= 4
3. mem_number <= 4
4. mem_number = 4
```

```
1
```


## 2. 좀 더 깊게 알아보는 SELECT문

### ORDER BY
- 결과가 출력되는 순서를 조절
- ASC: 오름차순
- DESC: 내림차순

- LIMIT: 출력하는 개수 제한
  - LIMIT 3,2 -> 3번째부터 2건만 조회
 
- DISTINCT: 중복된 데이터 1개만
  ```
  SELECT
  DISTINCT addr
  FROM member
  ```

### GROUP BY
- 그룹으로 묶어주는 역할
- 집계함수가 주로 함께 쓰임
    - SUM(): 합계
    - AVG(): 평균
    - MIN()/MAX(): 최솟값, 최댓값
    - COUNT(): 행의 개수 -> COUNT(*): NULL인 값은 제외 
    - COUNT(DISTINCT): 중복 한 개만 인정한 행의 개수
 
  - HAVING
    - 집계함수에 대해서 조건을 제한
    - GROUP BY절 다음에

### ORDER BY
- 결과가 출력되는 순서를 조절하는 절
- **ASC**: 오름차순 (기본값)
- **DESC**: 내림차순

#### LIMIT
- 출력하는 데이터의 개수를 제한
- `LIMIT 3, 2`: 3번째 위치부터 2건만 조회 (시작 위치는 0부터 계산)

#### DISTINCT
- 조회된 결과에서 중복된 데이터를 1개만 남기고 보여줌
```sql
SELECT DISTINCT addr
    FROM member;
```

---

### GROUP BY
- 데이터를 특정 기준으로 묶어주는 역할
- 집계함수와 주로 함께 쓰임
    - **SUM()**: 합계
    - **AVG()**: 평균
    - **MIN() / MAX()**: 최솟값 / 최댓값
    - **COUNT()**: 행의 개수
        - `COUNT(*)`: NULL 값을 포함한 모든 행의 개수
        - `COUNT(열_이름)`: NULL 값을 제외한 행의 개수
    - **COUNT(DISTINCT 열_이름)**: 중복을 제거한 고유한 행의 개수

#### HAVING
- 집계함수의 결과에 대해서 조건을 제한할 때 사용
- 일반 조건절과 달리 반드시 `GROUP BY` 절 다음에 위치해야 함

> **확인문제: 다음 표는 주요 집계함수를 정리한 것입니다. 각 설명에 해당하는 올바른 함수명을 기호에 맞게 작성하세요.**

| 함수명 | 설명 |
|--------|------|
| SUM() | 합계를 구합니다. |
| (ㄱ) | 평균을 구합니다. |
| (ㄴ) | 최소값을 구합니다. |
| MAX() | 최대값을 구합니다. |
| (ㄷ) | 행의 개수를 셉니다. |
| (ㄹ) | 행의 개수를 셉니다 (중복은 1개만 인정). |

```
여기에 답을 적어주세요!
(ㄱ) AVG()
(ㄴ) MIN()
(ㄷ) COUNT()
(ㄹ) COUNT(DISDINT ID)
```


## 3. 데이터 변경을 위한 SQL문

### INSERT

```
INSERT INTO 테이블 [{열1,열2,...}] VALUES (값1, 값2, ...)
```

- 열 이름은 생략가능 -> 값의 개수가 열의 갯수와 동일해야함
    - 특정 열의 값을 비워두고 싶다면 NULL로 입력
- 열 이름 적는다면 순서 상관 X
- **AUTO_INCREMENT**: 1부터 증가하는 값 입력
    - 이 경우 INSERT로 값을 입력할 때 해당 열이 없다고 생각하고 입력
    - PRIMARY KEY로 지정해야함
    - 100부터 시작하도록 변경
    - ```
      ALTER TABLE TABLE_A AUTO=100;
      ```
    - 1000, 1003, 1006 ... 으로 설정 -> **@@AUTO_INCREMENT_INCREMENT**
    - ```
      ALTER TABLE TABLE_A AUTO=100; -> 시작값은 1000으로 지정
      SET @@AUTO_INCREMENT_INCREMENT=3; -> 증가값은 3으로 지정
      ```


- DESC TABLE: 테이블의 구조를 출력

- ```
  INSERT INTO city_pop
      SELECT name, population FROM world.city;
  ```
  -> world.city에 있던 name과 population 열을 city_pop에 입력하는 쿼리
  
### UPDATE
- 데이터 수정
```
UPDATE TABLE
SET 열1=값1, 열2=값2,...
WHERE 조건;
```

EX) 전체 인구 데이터를 10,000명 단위로 바꾸기
```
UPDATE CITY_POP
    SET population = population / 10000;
SELECT * FROM CITY_POP LIMIT 5;
```


### DELETE
- 행 데이터를 삭제
```
DELETE FROM TABLE WHERE 조건;
```


### 대용량 테이블의 삭제

- DELETE: 오래 걸림, 빈 테이블을 남김 
- DROP: 테이블 자체를 삭제
- TRUNCATE: DELETE와 동일한 효과, 속도 매우 빠름 , 빈테이블이 남음 






> **확인문제: 다음이 설명하는 SQL이 무엇인지 쓰세요.**

```
* 데이터를 삭제합니다.
* DELETE와 동일한 효과를 내지만 속도가 무척 빠릅니다.
* 삭제 후에 빈 테이블이 남아 있습니다.
```

```
TRUNCATE
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week2_db;

-- 2. 사용할 데이터베이스 선택
USE week2_db;

-- 4. 테이블 생성
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(20),
    major VARCHAR(30),
    grade INT,
    age INT,
    gpa DECIMAL(3,2),
    admission_year INT
);

-- 5. 데이터 삽입
INSERT INTO students VALUES
(1, '진아', 'Statistics', 1, 19, 3.85, 2024),
(2, '혜인', 'Computer Science', 2, 20, 3.20, 2023),
(3, '규서', 'Business', 3, 22, 2.95, 2022),
(4, '규영', 'Statistics', 4, 23, 3.60, 2021),
(5, '철원', 'Economics', 2, 21, 3.75, 2023),
(6, '예운', 'Computer Science', 1, 19, 3.10, 2024),
(7, '민서', 'Statistics', 3, 22, 3.45, 2022);
```
## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.

1. 모든 학생의 정보를 조회하시오.
2. 전공이 'Statistics'인 학생을 조회하시오.
3. 현재 students 테이블에 존재하는 서로 다른 전공의 개수를 구하시오.
4. 나이가 20 이상이고 GPA가 3.5 이상인 학생을 조회하시오.
5. students 테이블에 본인의 정보를 직접 INSERT 하시오. (INSERT 실행 후, 데이터가 정상적으로 추가되었는지 확인할 수 있도록 조회 결과까지 포함하여 캡처하시오.)



# 1. 
<img width="1045" height="760" alt="image" src="https://github.com/user-attachments/assets/af79c716-9b21-4f94-b767-87b5e44c6cdf" />

# 2.
<img width="1015" height="693" alt="image" src="https://github.com/user-attachments/assets/725e1c98-368f-40d5-a2eb-ab168673885b" />

# 3. 
<img width="1020" height="680" alt="image" src="https://github.com/user-attachments/assets/449c7e75-6f4b-4ba1-8bfc-17edf5ef9700" />

# 4.
<img width="953" height="626" alt="image" src="https://github.com/user-attachments/assets/57d242bb-abc1-428c-a859-73ba2b913bc9" />

# 5. 
<img width="1095" height="775" alt="image" src="https://github.com/user-attachments/assets/c371ef38-478f-42c1-8aa6-4cfc094594d5" />

### 🎉 수고하셨습니다.






