# SQL_ADVANCED 1주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_1st_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=0cRhit1EJM0&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=1
https://www.youtube.com/watch?v=6JFEJWLcKUc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=2
https://www.youtube.com/watch?v=8r1W_7nuo2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=3
https://www.youtube.com/watch?v=j2DAiY-OXGs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=4
https://www.youtube.com/watch?v=EftIRlr6rPI&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=5
https://www.youtube.com/watch?v=lBk5YhLZevs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=6
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_1st_TIL

### 1장 데이터베이스와 SQL
#### 01. 데이터베이스 알아보기
#### 02. MySQL 설치하기
### 2장 실전용 SQL 미리 맛보기
#### 01. 건물을 짓기 위한 설계도: 데이터베이스 모델링
#### 02. 데이터베이스 시작부터 끝까지
#### 03. 데이터베이스 개체 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | 🍽️         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 데이터베이스 알아보기

- 데이터베이스: 데이터의 집합
- DBMS: DB를 관리하고 운영하는 소프트웨어 

> **확인문제: 다음 소프트웨어 중에서 DBMS가 아닌 것을 모두 고르세요.**

> MySQL / Excel / Oracle / SQL Server / MariaDB

```
EXCEL
-> 대용량 데이터를 관리하거나 여러 사용자와 공유한다고 보기 어려움
```


### DBMS의 분류
### 1. 계층형
- 트리형태
- 지금은 사용X

### 2. 망형
- 프로그래머가 모든 구조를 이해해야만 작성이 가능하다는 단점
- 지금은 거의 사용X

### 3. 관계형
- RDBMS
- 테이블 = 열 + 행
- 2차원 구조 




### SQL 
- 국제표준화기구 -> 표준 SQL
- 여러 회사에서 만들어서 조금씩 다름

## 2. MySQL 설치하기
<img width="1691" height="967" alt="image" src="https://github.com/user-attachments/assets/0dccfd78-c50f-4529-bc1b-29c784804a4a" />




## 3. 건물을 짓기 위한 설계도: 데이터베이스 모델링
### 데이터베이스 모델링
- 테이블의 구조를 미리 설계
- 폭포수 모델
- 테이블 구조 결정



### 프로젝트 진행 단계
- 프로젝트 : 현실 세계에서 일어나는 업무를 컴퓨터 시스템으로 옮겨놓는 과정
            대규노 소프트웨를 작성하기 위한 전체 과정
- 1. 프로젝트 계획: 계획 단계
  2. 업무 분석: 업무 정리 단계
  3. 시스템 설계: 업무 분석을 컴퓨터에 적용시키기 위한 가공 과정
  4. 프로그램 구현: 실제 프로그래밍 언어로 코딩
  5. 테스트
  6. 유지보수: 문제점 보완, 기능 추가
 


### 데이터 베이스 모델링
DBMS의 데이터베이스 걔체로 옯기기 위한 과정 (테이블로 변경하기 위한 작업)



### 전체 데이터베이스 구성도 
<img width="647" height="417" alt="image" src="https://github.com/user-attachments/assets/bdab5cc0-8522-4850-9b4b-241f26a1dbcc" />


- 데이터: 단편적 정보
- 테이블: 데이터를 입력하기 위한 표
- 데이터 베이스: 테이블이 저장되는 저장소
- DBMS: 데이터베이스 관리 시스템 OR 소프트웨어
- 기본키: PK, 각 행을 구분하는 유일한 열
- SQL: 구조화된 질의 언어, DBMS가 소통하기 위한 언어


> **확인문제: 다음은 폭포수 모델의 절차입니다. 차례대로 나열해보세요.**

> 시스템 설계 / 테스트 / 프로그램 구현 / 프로젝트 계획 / 업무 분석 / 유지보수

```
프로젝트 계획 > 업무 분석 > 시스템 설계 > 프로그램 구현 > 테스트 > 유지보수 
```


## 4. 데이터베이스 시작부터 끝까지 

<!-- 이번 챕터는 개념정리 없이 실습 인증사진으로 대체합니다. 강의를 수강하고, 실습 과정이 보이도록 인증사진 3-4장을 아래에 제출해주세요. -->

<img width="1158" height="739" alt="image" src="https://github.com/user-attachments/assets/6669264f-0ee1-48d5-8854-2d177ccca53c" />


<img width="851" height="810" alt="image" src="https://github.com/user-attachments/assets/3e1d6a8b-9981-4a5e-b2cc-2fdc6080fc3c" />


<img width="1041" height="557" alt="image" src="https://github.com/user-attachments/assets/bafc05d5-b176-44d6-bf95-7d73f66965fd" />



## 5. 데이터베이스 개체

- **인덱스** : 특정 단어를 찾기 위한 부분

<!-- 인덱스, 뷰, 스토어드 프로시저 실습을 각각 진행한 후, 각 실습에 대한 인증 사진을 1장씩 제출해 주세요. -->
<img width="1079" height="710" alt="image" src="https://github.com/user-attachments/assets/2a99e3e1-01b4-479a-8c7b-fb9fd27e585c" />

<img width="679" height="427" alt="image" src="https://github.com/user-attachments/assets/95e34417-ba7b-45d0-b21c-d0ebd5a134ba" />

<img width="730" height="736" alt="image" src="https://github.com/user-attachments/assets/a5b87e04-841c-4482-8978-daba82befa41" />

---

# 2️⃣ 실습과제

> SQL ADVANCED 과정은 별도의 확인문제가 없습니다. 다음 주부터는 확인문제 대신 제공되는 실습용 테이블을 활용하여, 배운 내용을 직접 적용하는 실습형 과제로 진행됩니다.

> 이번주는 개강과 함께 새로운 학기가 시작된 만큼, 학기 초 일정에 천천히 적응하시며 부담 없는 한 주 보내시길 바랍니다. 😊

### 🎉 수고하셨습니다.






