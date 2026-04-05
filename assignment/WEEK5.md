# SQL_ADVANCED 5주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_5th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=KZmW6VaY5BU&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=16
https://www.youtube.com/watch?v=vWTDuoSG-YQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=17
https://www.youtube.com/watch?v=aiMSluMNzI8&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=18
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_5th_TIL

### 6장 인덱스
#### 01. 인덱스 개념을 파악하자
#### 02. 인덱스의 내부 작동
#### 03. 인덱스의 실제 사용  


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | ✅         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 인덱스 개념을 파악하자 

### 인덱스
- 데이터를 빠르게 찾을 수 있도록 도와주는 도구

**1. 클러스터형 인덱스**
    - 기본 키로 지정하면 자동 생성
    - 테이블에 1개 생성 가능
    - 기본 키로 지정한 열을 기준으로 자동 정렬
 
 **2. 보조 인덱스**
    - 고유 키로 지정하면 자동 생성
    - 여러 개를 만들 수 있음
    - but 자동 정렬 x
 
- like 책 뒤에 있는 index

### 인덱스의 문제점
- 필요없는 인덱스를 만들게 되면 데이터베이스가 차지하는 공간만 늘어남
- 속도도 느려짐

<br>

### 인덱스의 장점과 단점
<br>

#### 장점
1. SELECT 문으로 검색하는 속도가 매우 빨라짐
2. 그 결과 컴퓨터의 부담이 줄어 전체 시스템 성능 향상

<Br>

#### 단점
- 인덱스도 공간을 차지해서 데이터베이스 안에 추가적인 공간이 필요
- 처음에 인덱스를 만드는데 시간이 오래 걸릴 수 있음
- SELECT가 아닌 데이터의 변경 (INSERT, UPDATE, DELETE)이 자주 일어나면 오히려 성능이 나빠짐

<BR>

<BR>

### 인덱스의 종류
- 클러스터형: LIKE 영어사전
- 보조 인덱스: 책의 뒤에 찾아보기


#### 자동으로 생성되는 인덱스
- 인덱스는 테이블의 컬럼 단위에 생성
- 하나의 열에는 하나의 인덱스 생성 가능


```sql
CREATE TABLE member
( mem_id CHAR(8) NOT NULL PRIMARY KEY,
mem_name VARCHAR(8) NOT NULL,
mem_number INT NOT NULL
...

```

- mem_id를 기본 키로 정의
- 자동으로 mem_id열에 클러스터형 인덱스 생성
- 기본 키는 테이블에 하나 = 클러스터형 인덱스 테이블에 한 개 
- `SHOW INDEX`문을 사용하여 인덱스 정보 확인
- `PRIMARY` = 클러스터형 인덱스
- `col1` = col1열에 인덱스 생성
- `Non_Unique = 1` = 고유하지 않다 = 중복 허용
  

<br>

```sql
CREATE TABLE table2 (
  col1 INT PRIMARY KEY,
  col2 INT UNIQUE, -- 고유키로 지정
  col3 INT UNIQUE -- 고유 키로 지정
);
```
- 보조 인덱스는 고유 키로 지정하면 자동으로 생성
- 테이블당 여러 개 만들 수 있음

<img width="755" height="437" alt="image" src="https://github.com/user-attachments/assets/6cd01afd-100b-432e-a93c-2eb613aa74d3" />

#### 자동으로 정렬되는 클러스터형 인덱스
- 어떤 열을 기본 키로 지정하면(클러스터형 인덱스가 생성되면) 그 열을 기준으로 자동 정렬



<img width="715" height="494" alt="image" src="https://github.com/user-attachments/assets/e9026633-a330-4be8-ac12-72b266b96a82" />

<img width="553" height="481" alt="image" src="https://github.com/user-attachments/assets/45cc171c-2872-4c67-b979-0469848f8694" />

- `order by mem_id`을 추가했을 때와 같은 결과

<br>

**고유 키 변경하기**
<br>

<img width="768" height="490" alt="image" src="https://github.com/user-attachments/assets/d7ed570e-7ec1-4066-b1b2-cad524316f36" />


<br>

<br>

<br>

**행 추가하기**
<br>
<img width="741" height="578" alt="image" src="https://github.com/user-attachments/assets/4b123fc0-6e69-44a0-be3d-5680eaddd860" />
<br>




#### 정렬되지 않는 보조 인덱스

- 고유 키로 지정 -> 보조 인덱스 생성
- 보조 인덱스는 테이블에 여러 개 설정 가능

<br>
<img width="586" height="514" alt="image" src="https://github.com/user-attachments/assets/909d84bd-688b-407f-93e7-78f6fa9a2b45" />
<br>
<img width="586" height="514" alt="image" src="https://github.com/user-attachments/assets/03c86566-9e80-4758-8071-9cb9aec5af82" />

- 고유 키로 지정된 보조 인덱스는 자동 정렬 x

**비교**
| 구분 | 클러스터형 인덱스 (Clustered Index) | 보조 인덱스 (Secondary Index) |
| :--- | :--- | :--- |
| **핵심 정의** | 데이터 자체가 물리적으로 정렬됨 | 별도의 공간에 색인 페이지만 정렬됨 |
| **생성 기준** | `PRIMARY KEY` (기본키) | `UNIQUE` (고유키) 또는 일반 `INDEX` |
| **테이블당 개수** | 오직 1개 | 여러 개 생성 가능 |
| **비유** | **영어 사전** (내용 자체가 정렬) | **책 뒤쪽 찾아보기** (본문은 그대로) |


<br>

<br>

<br>

> **확인문제: 다음은 인덱스 종류와 관련된 설명입니다. 가장 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 클러스터형 인덱스는 영어사전과 비슷한 개념입니다.
2️⃣ 보조 인덱스는 일반 책의 찾아보기와 비슷한 개념입니다.
3️⃣ 클러스터형 인덱스는 기본 키를 설정하면 자동 생성됩니다.
4️⃣ 보조 인덱스는 NOT NULL을 설정하면 자동 생성됩니다.
```

```
4️⃣  `NOT NULL`이 아니라 `UNIQUE`
```


## 2. 인덱스의 내부 작동 

<br>

### 인덱스의 내부 작동 원리
#### 균형 트리의 개념
- **노드**: 데이터가 저장되는 공간
  - **루트 노드**: 가장 상위 노드
  - **리프 노드**: 가장 마지막에 존재하는 노드
  - **중간 노드**: 위 두 노드에 끼인 노드들
- 노드 = MySQL) 페이지
  - 최소한의 저장 단위
  - 16Kbyte

- 데이터 검색 시 아주 뛰어난 성능
- 균형 트리에서 검색하면 루트 페이지부터 검색


<br>

#### 균형 트리의 페이지 분할
- 인덱스를 구성하면 데이터 변경작업(INSERT, UPDATEM DELETE) 시 성능이 나빠짐
  - 이유: 페이지분할
  - **페이지분할**: 새로운 페이지를 준비해서 데이터를 나누는 작업



<br>


### 인덱스의 구조
#### 클러스터형 인덱스 구성하기

<br>
<img width="809" height="743" alt="image" src="https://github.com/user-attachments/assets/71fc1c4e-64a0-4a14-9424-8553bffc6aac" />

#### 보조 인덱스 구성하기 

<br>
<img width="730" height="693" alt="image" src="https://github.com/user-attachments/assets/af063d7f-04ea-43eb-805b-250765041f9e" />


<br>

- 보조 인덱스가 생성되었음에도 입력한 것과 순서 동일
- 보조 인덱스는 데이터 페이지를 건들이지 X
- 별도의 장소에 인덱스 페이지 생성
- 데이터의 위치 -> **페이지 번호 + #위치**로 기록 

<br>

#### 인덱스에서 데이터 검색하기
**인덱스 검색**을 통해 클러스터형 인덱스는 2페이지, 보조 인덱스는 3페이지를 읽어 결과 

<br>





<br>
> **확인문제: 다음 설명에서 빈칸에 공통으로 들어갈 용어를 쓰시오.**

```
인덱스를 구성하게 되면 데이터의 변경 작업(INSERT, UPDATE, DELETE)시에 성능이 나빠지는 단점이 있습니다.  
특히 INSERT 작업이 일어날 때 더 느리게 입력될 수 있는데요, 이유는 (           ) 이라는 작업이 발생하기 때문입니다.  
(            ) 작업이 일어나면 MySQL이 느려지고 너무 자주 일어나면 성능에 큰 영향을 줍니다.
```

```
페이지분할
```


## 3. 인덱스의 실제 사용 

<!-- 이번 챕터에서 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->
### 1. 기존 인덱스 확인 
<img width="781" height="599" alt="image" src="https://github.com/user-attachments/assets/15974b26-361a-43f6-a7e0-4338f99dae65" />

<br>

### 2. 보조 인덱스
<img width="787" height="582" alt="image" src="https://github.com/user-attachments/assets/dc16f418-bd01-4019-9e9a-704b3f84bd2d" />
<br>

### 3. 고유 보조 인덱스
<img width="793" height="736" alt="image" src="https://github.com/user-attachments/assets/d5cfd9e7-8004-4f21-825d-233e877b39ed" />


<br>

### 4. 인덱스 활용

<img width="784" height="624" alt="image" src="https://github.com/user-attachments/assets/44b6f984-3742-4930-920a-648f76084c2e" />

<br>

### 5. 인덱스 제거
<img width="787" height="627" alt="image" src="https://github.com/user-attachments/assets/98a6c4bb-d20c-4453-907a-f3f6c3567f70" />

<br>
<br>

---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week5_db;
USE week5_db;

DROP TABLE IF EXISTS employees;

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(20),
    department VARCHAR(30),
    salary INT,
    hire_date DATE
);

INSERT INTO employees VALUES
(1, '진아', 'Sales', 3500, '2022-03-01'),
(2, '혜인', 'HR', 3200, '2021-06-15'),
(3, '규서', 'Sales', 4000, '2020-09-10'),
(4, '규영', 'IT', 5000, '2019-01-20'),
(5, '철원', 'Marketing', 3800, '2023-04-01'),
(6, '예운', 'IT', 4500, '2022-12-01'),
(7, '민서', 'Sales', 3700, '2021-08-18');
```

## 2. 실습 문제

다음 문제를 수행하고 실행 결과를 캡처하여 제출하세요.

1. department 컬럼에 보조 인덱스를 생성하시오.
    - 인덱스 생성 후, `SHOW INDEX FROM employees;` 실행 결과가 보이도록 캡처합니다.
    - (idx_department 인덱스가 존재하는지 확인되어야 합니다.)
  
<br>
<img width="785" height="637" alt="image" src="https://github.com/user-attachments/assets/32e17aae-eff7-496a-a725-68dc1271b1fe" />

<br>

2. employees 테이블의 인덱스를 확인하시오.
<br>
<img width="782" height="562" alt="image" src="https://github.com/user-attachments/assets/43573b5b-9ed4-47b9-bcb0-332e312eebf8" />

<br>

3. department가 'Sales'인 직원을 조회하시오.
   - 'Sales' 조회 시, 반드시 `EXPLAIN`을 함께 실행한 화면을 캡처합니다.
   - (key 컬럼에 idx_department가 표시되어야 합니다.)
  <br>
<img width="768" height="500" alt="image" src="https://github.com/user-attachments/assets/24e2309c-ba7e-4e28-a24f-5540f953056c" />
<br>

4. 생성한 인덱스를 삭제하시오.
   - 인덱스 삭제 후, 다시 `SHOW INDEX FROM employees;`를 실행하여 idx_department가 사라진 것을 확인한 화면을 캡처합니다.
<br>
<img width="789" height="607" alt="image" src="https://github.com/user-attachments/assets/e124998b-3950-4f3a-879d-478081eb3b49" />
<br>
## 3. 제출방법

인덱스 생성 결과, EXPLAIN 실행 결과, 인덱스 삭제 결과가 모두 보이도록 캡처하여 제출하세요.

<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->

### 🎉 수고하셨습니다.






