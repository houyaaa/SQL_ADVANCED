# SQL_ADVANCED 4주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=DMNpkj_bZIs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=13
https://www.youtube.com/watch?v=BUHj-behLyc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=14
https://www.youtube.com/watch?v=JrXWxku7ZIM&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=15
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_4th_TIL

### 5장 테이블과 뷰
#### 01. 테이블 만들기
#### 02. 제약조건으로 테이블을 견고하게
#### 03. SQL 가상의 테이블: 뷰 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 테이블 만들기 
<br>
<br>

<img width="1221" height="550" alt="image" src="https://github.com/user-attachments/assets/13b0dff9-b91e-4bfe-97cf-ebcbac22c861" />

<img width="954" height="631" alt="image" src="https://github.com/user-attachments/assets/b8bf1d07-8e6d-4250-a565-fc53a13a7415" />

<img width="706" height="315" alt="image" src="https://github.com/user-attachments/assets/14b23409-a25b-4c34-bc7e-6defce84525b" />


## 2. 제약조건으로 테이블을 견고하게 

제약조건: 데이터에 결함이 없도록 무결성을 지키기 위해 제한을 두는 기능

오류가 적고 튼튼한 데이터 베이스 생성 가능

- **기본키**: 행 데이터를 구분하는 고유한 식별자, 중복될 수 없고 NULL을 허용X
- **외래키**: 두 테이블 사이의 관계를 연결하여 무결성 보장, 참조하는 기준 테이블의 열은 반드시 기본키 OR 고유 키
    - CASCADE옵션: `ON UPDATE CASECADE`및 `ON DELETE CASCADE` 설정 -> 기준 테이블의 데이터 변경 OR 삭제 시 참조 테이블의 데이터도 자동으로 변경 및 삭제
- **고유키**: 중복되지 않는 유일한 값을 이력해야하지만, 기본 키와 달리 NULL허용
- 체크: 입력되는 데이터를 점검하여 지정된 조건에 맞는 데이터만 허용
- 기본값: 값을 입력하지 않았을 때 자동으로 들어갈 값을 미리 지정



> **확인문제: 다음 보기 중에서 각 문항이 설명하는 것을 고르세요.**

보기는 아래와 같습니다.
```
CHECK / DEFAULT / PRIMAY KEY / UNIQUE / NOT NULL / FOREIGN KEY
```

```
여기에 답과 그 이유를 적어주세요!
1. 입력되는 데이터가 조건에 맞는지 검사하는 기능: CHECK
2. 값을 입력하지 않으면 자동으로 들어갈 값: DEFAULT
3. 빈 값을 입력하는 것을 허용하지 않음: PRIMARY KEY
```


## 3. 가상의 테이블: 뷰 

뷰는 테이블과 동일하게 보이고 작동함
BUT 실제로 데이터를 저장하고 있지는 않은 가상의 테이블
뷰의 실체는 `SELECT문`, 뷰에 접근하면 내장된 쿼리가 실행되어 결과를 보여줌

- 뷰를 사용하는 주요 이유
    1. 보안: 사용자에게 연락처나 개인정보 같은 중요 열을 숨기고 필요한 열만 포함된 뷰를 제공하여 데이터 접근 권한을 제한할 수 있음
    2. 복잡한 SQL 단순화: `JOIN`등이 포함된 길고 복잡한 쿼리를 뷰로 만들어 두면, 매번 복잡한 쿼리를 짤 필요없이 단순하게 조회 가능

> **확인문제: 다음은 뷰의 특징입니다. 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
2️⃣ 뷰는 복잡한 SQL을 단순하게 만드는 효과가 있습니다.
3️⃣ 뷰는 보안에 도움이 됩니다.
4️⃣ 일부 사용자가 테이블에는 접근하지 못하게 하고, 뷰에만 접근하도록 설정할 수 있습니다.
```

```
1. 개인정보와 같은 중요 열을 숨기고 필요한 열만 추출해서 뷰에 포함시킬 수 있음 
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week4_db;
USE week4_db;
```

## 2. 실습문제

1. 다음 조건을 만족하는 `users` 테이블을 생성하시오.
```
- user_id는 INT이며 **기본키(Primary Key)**로 설정합니다.
- name은 VARCHAR(20)이며 NULL을 허용하지 않습니다.
- email은 VARCHAR(50)이며 중복을 허용하지 않습니다.
- signup_date는 DATE 타입으로 설정합니다.
- grade는 INT이며 기본값(Default)을 1로 설정합니다.
```

2. 다음 조건을 만족하는 orders 테이블을 생성하시오.
```
- order_id는 INT이며 기본키(Primary Key)로 설정합니다.
- user_id는 INT이며 NULL을 허용하지 않습니다.
- amount는 INT이며 0보다 커야 합니다.
- order_date는 DATE 타입으로 설정합니다.
```

3. 다음 조건을 만족하여 데이터를 삽입하시오.
```
- users 테이블에 3명 이상의 데이터를 직접 INSERT 하시오.
- orders 테이블에 3건 이상의 데이터를 직접 INSERT 하시오.
```

4. users와 orders 테이블을 활용하여 다음 컬럼을 보여주는 뷰 user_order_view를 생성하시오.
```
- user_id
- name
- amount
```

5. 생성한 user_order_view를 조회하시오.

## 3. 제출 방법

1. 각 문제의 실행 결과가 보이도록 화면을 캡처합니다.
2. 테이블 생성 결과, 데이터 삽입 결과, 뷰 생성 및 조회 결과가 모두 보이도록 제출합니다.

<img width="593" height="545" alt="image" src="https://github.com/user-attachments/assets/8c47e04e-c804-4ec8-af75-6f982d569c28" />

<img width="681" height="619" alt="image" src="https://github.com/user-attachments/assets/a19ed288-7e66-4f84-9e8c-96d4e39f3d2b" />

<img width="627" height="414" alt="image" src="https://github.com/user-attachments/assets/56de4a72-2b63-45b2-9793-1d3f0b189294" />

<img width="448" height="280" alt="image" src="https://github.com/user-attachments/assets/745ced98-072e-4885-a25d-1e70e3804414" />


### 🎉 수고하셨습니다.






